import java.util.Scanner;
import java.util.HashMap;
import java.util.Map;

public class CurrencyConverter {

    private static Map<String, Double> getExchangeRates() {

        Map<String, Double> rates = new HashMap<>();
        rates.put("USD", 1.0);
        rates.put("EUR", 0.85);
        rates.put("INR", 74.5);
        return rates;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Map<String, Double> rates = getExchangeRates();

        System.out.print("Enter the currency u want to convert (USD, EUR, INR): ");
        String base = scanner.nextLine().toUpperCase();
        System.out.print("Enter the currency which u want it to be converted to (USD, EUR, INR): ");
        String target = scanner.nextLine().toUpperCase();

        if (!rates.containsKey(base) || !rates.containsKey(target)) {
            System.out.println("Invalid currency. Enter valid currencies.");
            return;
        }

        System.out.print("Enter the money amount to convert: ");
        double amount = scanner.nextDouble();

        double convertedAmount = amount / rates.get(base) * rates.get(target);
        System.out.printf("Converted Amount: %.2f %s%n", convertedAmount, target);

        scanner.close();
    }
}
