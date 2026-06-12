---
title: "Bash: Script fails to complete due to write speed?"
date: 2009-10-16
forum: General Help
---

### Post by allenwjones on 2009-10-16
[FONT=Century Gothic][COLOR=DarkRed]
[SIZE=3]Hello![/SIZE]
[SIZE=2]
Synopisis:
I have some captured data from an automated terminal session using << and I have output the results using > results.txt from a bash script. I then want to parse the file for specific data and output the new result to another file.

I have tested the syntax of both of these from the terminal command line, but when I input the commands to a bash script it fails and exits back to the command line without finishing.

Here is the order of commands:
[/SIZE]

```

#! /bin/bash

# Capture results
 {application to get the data} << ! > temp.txt
  {various steps in application}
 !

# Refine results to newfile
 grep "something to look for" temp.txt | tee result.txt

# Remove temporary results
 rm temp.txt

```[SIZE=2]
The grep command syntax works from the command line, but not from the script. My only guess is that the drive has not had time to write the temp.txt file before the grep command executes. I may be wrong about this..
[/SIZE]


[SIZE=3]Any suggestions?[/SIZE]


[SIZE=2]I have verified it's not the drive speed. I have left the data file intact and tried to grep from the script directly and it still fails for some reason.

More Additional Information:
I now believe the issue to be tied to the output from the first application including special characters '<' and '>'.. in fact the lines I am searching for start with the '<' which the grep finds and outputs to the second file *from the command line but not from the script.*

Is there any way to get around this?
[/SIZE] [/COLOR][/FONT]

---

