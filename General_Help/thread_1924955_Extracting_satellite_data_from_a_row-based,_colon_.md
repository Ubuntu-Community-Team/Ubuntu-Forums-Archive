---
title: "Extracting satellite data from a row-based, colon delimited file"
date: 2012-02-13
forum: General Help
---

### Post by BigBennyC on 2012-02-13
Hello everyone, first post here.  I have about 200 txt files, all in the same directory, which look like this:

Cube:           /home/bc186828/Desktop/Testing/testfile.cub
Band:           1
Average:        0.0895063
Std Deviation:  0.00779792
Variance:       6.08076e-05
Median:         0.0903048
Mode:           0.0929003
Skew:           -0.30719
Minimum:        0.0512764
Maximum:        0.134821

I need a way to extract the data under Cube and Average for all these files and place it into another text file or spreadsheet, preferably with the categories at the top of the rows like a good, normal csv.  I feel like the fact that it's colon delimited and arranged in rows makes it more difficult for me to change existing code I've found.  Thanks in advance!
Ben

---

### Post by Andrew_P on 2012-02-13
It looks like a task for a BASIC or Python program, or other programming language of your choice.  It could also probably be done with a clever shell script.  My background is DOS/Windows, and I'm not a Unix shell whiz.  Maybe someone who knows BASH or C shell programming could chime in and give you some pointers.  Unix shells have far more processing power than DOS/Windows shells.

The advantage you may have here is that all the data files appear to be plain text with one parameter per line.  If the files are all identical with the exception of the numeric values for the parameters, that would make programmed processing easier.

If processing a single file is easier, you might start by concatenating the multiple small files into a single, large text file, then processing that one file.  Concatenating could be done easily with a script.  Use "ls" to list the files and redirect the output to a text file.  If, for instance, all the files have a .dat extension, open a terminal in the directory where they reside and execute this command:

ls *.dat > names.txt

You can then open names.txt with a text editor like gedit and start manipulating the strings to build a script that takes every one of the file names and consecutively writes their contents into a destination file, where you'll end up with a collection of all the data from all of the files.  Then you can massage the data in the destination file with gedit, stripping out the parameter names, enclosing values with parentheses and replacing newlines with commas, eventually turning it into a comma-separated-value (CSV) file that can be sucked into a spreadsheet.

These are just a few things that can be done without having to resort to sophisticated programming.  If this is a one-shot problem, it may not be worth spending a lot of time on programming.  If you find yourself doing this two or more times, or on a regular basis, then it's worth writing some custom programs.

---

### Post by Vaphell on 2012-02-13
try this quick and dirty script
```
#!/bin/bash

# output file
csv=out.csv

# columns to appear in output file
cols=( "Cube" "Band" "Average" "Std Deviation" "Variance" "Median" "Mode" "Skew" "Minimum" "Maximum" )

# header row
for col in "${cols[@]}"
do
  echo -n "${col},"
done > "${csv}"
echo >> "${csv}"

# process files and fill rows
for f in *.txt
do
  for col in "${cols[@]}"
  do
    echo -n $( sed -r "/${col}:/ s/^${col}: (.*)$/\1/p;d" "${f}" ),
  done
  echo
done >> "${csv}"

# show file contents
echo "${csv}:"
cat "${csv}"
```

---

### Post by HiImTye on 2012-02-13
you could try something like
```
CUBE=`grep Cube /path/to/file | sed 's/.*: //'`; AVERAGE=`grep Average /path/to/file | sed 's/.*: //'`; echo Cube,Average >> outputfile; echo $CUBE,$AVERAGE >> outputfile
```and then make a loop to handle all your files

in your loop you could reference the file with $FILE so it looks like:
```
FILE=/path/to/file$i; CUBE=`grep Cube $FILE | sed 's/.*: //'`; AVERAGE=`grep  Average $FILE | sed 's/.*: //'`; echo Cube,Average >>  outputfile; echo $CUBE,$AVERAGE >> outputfile
```if your files are numerical (i.e. file1, file2, etc) that way when you use for i, you can pass i to the filename, or something, Im not sure how you would impliment it

---

