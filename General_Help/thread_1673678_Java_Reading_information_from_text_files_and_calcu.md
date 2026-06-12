---
title: "Java: Reading information from text files and calculating ..."
date: 2011-01-22
forum: General Help
---

### Post by Natalie108 on 2011-01-22
So I need to right a program that reads information from an existing file ("WeeklyPayroll.txt"). The file is exactly this: 
 
Jane
Smith
10.50
12
 
Helen
Clarke
11.50
10
 
Rain
Parker
10.50
10
 
I then need to take each employee earnings (the this number line in each pragraph) and calculate sepately their total earnings using their weekly hours (the fourth line in each paragraph). How do I take specific lines from a file? Here's a program i have that simply reads the file and re-prints it. Can someone help me? 
 
[FONT=Courier New][COLOR=#941edf][FONT=Courier New][COLOR=#941edf]import[/COLOR][/FONT][/COLOR][/FONT][FONT=Courier New] java.io.*;[/FONT]
 
[FONT=Courier New][COLOR=#941edf][FONT=Courier New][COLOR=#941edf]class[/COLOR][/FONT][/COLOR][/FONT][FONT=Courier New] txtFile[/FONT]
[FONT=Courier New]{[/FONT]
[FONT=Courier New][COLOR=#941edf][FONT=Courier New][COLOR=#941edf]public[/COLOR][/FONT][/COLOR][/FONT][FONT=Courier New][COLOR=#941edf][FONT=Courier New][COLOR=#941edf]static[/COLOR][/FONT][/COLOR][/FONT][FONT=Courier New][COLOR=#941edf][FONT=Courier New][COLOR=#941edf]void[/COLOR][/FONT][/COLOR][/FONT][FONT=Courier New] main(String[] args) [/FONT][FONT=Courier New][COLOR=#941edf][FONT=Courier New][COLOR=#941edf]throws[/COLOR][/FONT][/COLOR][/FONT][FONT=Courier New] IOException[/FONT]
[FONT=Courier New]{[/FONT]
[FONT=Courier New]FileInputStream file = [/FONT][FONT=Courier New][COLOR=#941edf][FONT=Courier New][COLOR=#941edf]new[/COLOR][/FONT][/COLOR][/FONT][FONT=Courier New] FileInputStream([/FONT][FONT=Courier New][COLOR=#00cb00][FONT=Courier New][COLOR=#00cb00]"WeeklyPayroll.txt"[/COLOR][/FONT][/COLOR][/FONT][FONT=Courier New]);[/FONT]
[FONT=Courier New]InputStreamReader isr = [/FONT][FONT=Courier New][COLOR=#941edf][FONT=Courier New][COLOR=#941edf]new[/COLOR][/FONT][/COLOR][/FONT][FONT=Courier New] InputStreamReader(file);[/FONT]
[FONT=Courier New]BufferedReader reader = [/FONT][FONT=Courier New][COLOR=#941edf][FONT=Courier New][COLOR=#941edf]new[/COLOR][/FONT][/COLOR][/FONT][FONT=Courier New] BufferedReader(isr);[/FONT]
 
[FONT=Courier New][COLOR=#941edf][FONT=Courier New][COLOR=#941edf]int[/COLOR][/FONT][/COLOR][/FONT][FONT=Courier New] ch;[/FONT]
 
[FONT=Courier New][COLOR=#941edf][FONT=Courier New][COLOR=#941edf]while[/COLOR][/FONT][/COLOR][/FONT][FONT=Courier New] ((ch = reader.read()) != -1)[/FONT]
[FONT=Courier New]{[/FONT]
[FONT=Courier New]System.out.print(([/FONT][FONT=Courier New][COLOR=#941edf][FONT=Courier New][COLOR=#941edf]char[/COLOR][/FONT][/COLOR][/FONT][FONT=Courier New])ch);[/FONT]
[FONT=Courier New]}[/FONT]
[FONT=Courier New]isr.close();[/FONT]
[FONT=Courier New]file.close();[/FONT]
[FONT=Courier New]}[/FONT]
[FONT=Courier New]}[/FONT]

---

### Post by endotherm on 2011-01-22
instead of reading char by char with bufferedreader.read(), try bufferedReader.ReadLine() 
and use println(string) rather than print(char).
will make your job much easier.

thats all the advise i can give on homework, otther than to use code tags when posting code, so your indents don;t get all messed up.

---

