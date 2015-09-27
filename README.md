# StringSorting
program to remove all the duplicate strings from the list and print the resulting list of strings in a sorted order

import java.util.Scanner;
import java.util.Set;
import java.util.TreeSet;

public class Sorting {

	public static void main(String[] args) {
		final Set<String> names = new TreeSet<String>();
		readInputStrings(names);
		outputResult(names);
	}

	public static void readInputStrings(final Set<String> names) {
		final Scanner scanner = new Scanner(System.in);
		System.out.print("Please enter a limit (limit should be less than or equal to 5000):");
		int limit = scanner.nextInt();
		while (limit > 0) {
			if (isLimitValid(limit)) {
				System.out.print("Please enter " + limit + " names:");
				scanner.nextLine();
				while (limit > 0) {
					final String name = scanner.nextLine();
					if (name.length() <= 100) {
						names.add(name);
					} else {
						System.out.print("Please enter a valid name (name length should be less than or equal to 100):");
						continue;
					}
					limit--;
				}
			} else {
				System.out.print("Please enter a valid limit (limit should be less than or equal to 5000):");
				limit = scanner.nextInt();
				continue;
			}
		}
		scanner.close();
	}

	public static void outputResult(final Set<String> names) {
		System.out.println("Below are the names which is under sorted order and without duplicate names");
		for (String name : names) {
			System.out.println(name);
		}
	}

	public static boolean isLimitValid(final int limit) {
		return limit <= 5000 ? true : false;
	}
}
