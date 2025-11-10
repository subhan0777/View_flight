# View_flightvoid viewFlights() {
    struct Flight flight;     // use existing struct definition
    FILE *fp = fopen("Flights.txt", "r");

    if (fp == NULL) {
        printf("\nNo flights found!\n");
        return;
    }

    printf("\n---------------------------------------------");
    printf("\n             🛫 All Available Flights");
    printf("\n---------------------------------------------\n");
    printf("%-10s %-15s %-15s %-12s %-8s %-10s %-10s %-8s\n",
           "ID", "Source", "Destination", "Date", "Time",
           "Seats", "Avail.", "Price");
    printf("--------------------------------------------------------------------------------\n");

    int count = 0;
    while (fscanf(fp, "%d,%[^,],%[^,],%[^,],%[^,],%d,%d,%f\n",
                  &flight.flight_id,
                  flight.source,
                  flight.destination,
                  flight.date,
                  flight.time,
                  &flight.total_seats,
                  &flight.available_seats,
                  &flight.price) == 8)
    {
        printf("%-10d %-15s %-15s %-12s %-8s %-10d %-10d %-8.2f\n",
               flight.flight_id,
               flight.source,
               flight.destination,
               flight.date,
               flight.time,
               flight.total_seats,
               flight.available_seats,
               flight.price);
        count++;
    }

    if (count == 0) {
        printf("\nNo flight records found.\n");
    }

    fclose(fp);
}
