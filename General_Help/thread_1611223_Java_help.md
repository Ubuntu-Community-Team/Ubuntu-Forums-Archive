---
title: "Java help"
date: 2010-11-01
forum: General Help
---

### Post by fejomu on 2010-11-01
HELLO peoplr, im doin this java programme to ask a user for a file name and read the CSV file into a data structure. this is what i have done but dosent seem to work
import java.io.BufferedReader;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStreamReader;

public class Pro{
	int n_elements = 100;
    StudentInfo[] Student_Files = new StudentInfo[n_elements];
    int Files_Pointer = 0;
	public void Menu() throws NumberFormatException, IOException{
		BufferedReader object = new BufferedReader(new InputStreamReader(System.in));
			System.out.println("\nPlease select a choice\n" +
                "(1) – Load CSV file\n" +
                "(2) – Display data\n" +
                "(3) – Add row\n" +
                "(4) – Delete row\n" +
                "(5) – Calculate statistics\n" +
                "(6) – Sort data by first column\n" +
                "(7) – Save CSV file\n" +
                "(8) – Quit\n" +
                "Choice:>");
				int choice = 0;
				choice = Integer.parseInt(object.readLine());
			switch(choice){
				case 1:
					LoadCSVFile();
					break;
				case 2:
					DisplayData();
					break;
				case 3:
					AddRow();
					break;
				case 4:
					DeleteRow();
					break;
				case 5:
					CalculateStatistics();
					break;
				case 6:
					SortData();
					break;
				case 7:
					SaveCSVFile();
					break;
				case 8:
					System.exit(0);
					break;
				default:
					System.out.println("Invalid input, please try again");
					Menu();
					break;
			}
			Menu();
    }
	private void LoadCSVFile() throws NumberFormatException, IOException {
		FileInputStream inStream;
		InputStreamReader inFile;
		BufferedReader br;
		String fileName = "F:/data.txt", line;
		int lineNum;
		try {
			inStream = new FileInputStream(fileName);
			inFile = new InputStreamReader(inStream);
			br = new BufferedReader(inFile);
			line = br.readLine(); // read first line
			lineNum = 0;
			while (line != null){
				line = br.readLine(); // read some more
				lineNum++;
			}
		}
		catch (IOException e){
			System.out.println("Error " + fileName);
		}
		Menu();
	}
	private void DisplayData() {
		// TODO Auto-generated method stub
		
	}
	private void AddRow() {
		// TODO Auto-generated method stub
		
	}
	private void DeleteRow() {
		// TODO Auto-generated method stub
		
	}
	private void CalculateStatistics() {
		// TODO Auto-generated method stub
		
	}
	private void SortData() {
		// TODO Auto-generated method stub
		
	}
	private void SaveCSVFile() {
		// TODO Auto-generated method stub
		
	}
	
	
	public static void main(String[] args) throws NumberFormatException, IOException
    {
        Pro pro = new Pro();
        try {
        	pro.Menu();
		} 
        catch (NumberFormatException e) {
			System.out.println(e.getMessage() + " is not a numeric value.\n");
			System.out.println("Press ctrl + f11 to continue\n");
			pro.Menu();
			//System.exit(0);
		}
        
    }
}
please help help urgent.
thanks

---

### Post by lykeion on 2010-11-02
1. Posting code as text makes it hard to read, wrap it with PHP tags for readablility.

2. This looks very much like a homework question, which is against forum policy, [http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

3. Your code won't compile without StudentInfo class (even though I can guess how that class looks like). 

4. You should read some tutorial on Java File I/O like this: [http://download.oracle.com/javase/tutorial/essential/io/file.html](http://download.oracle.com/javase/tutorial/essential/io/file.html)

---

