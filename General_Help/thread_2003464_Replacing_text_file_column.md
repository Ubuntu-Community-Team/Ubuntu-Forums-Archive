---
title: "Replacing text file column"
date: 2012-06-14
forum: General Help
---

### Post by JCM_Pico on 2012-06-14
Hi there,

I'm trying to replace a whole column of a text file (many text files) from line 2 to 121... replacing a blank space with a zero... is there any way of doing this with sed or vim without the boring work to replace it by hand?

waiting for your suggestions =)

---

### Post by greenpeace on 2012-06-14
Hi, 

It's a little difficult to say without some more information..

Could you give us an examples of what you have now, and how you want it to be after processing?

cheers!

---

### Post by JCM_Pico on 2012-06-14
From this 
```

 107.0   6295  -67.1 
 103.0   6523  -66.5 
 100.0   6700  -66.1 
  97.0  16886  -65.8 
  94.0  17078  -65.5 
  92.0  17210  -65.3 
  84.0  17766  -64.4 
  82.0  17913  -64.2  
   8.0  18219  -63.7  
   5.0  18458  -63.4    
   2.0  18708  -63.0   
```

To this
```

 107.0  06295  -67.1 
 103.0  06523  -66.5 
 100.0  06700  -66.1 
 097.0  16886  -65.8 
 094.0  17078  -65.5 
 092.0  17210  -65.3 
 084.0  17766  -64.4 
 082.0  17913  -64.2  
 008.0  18219  -63.7  
 005.0  18458  -63.4    
 002.0  18708  -63.0   
```

:)

---

### Post by greenpeace on 2012-06-14
I would use Python... as I am most familiar with it.  there are definitely a load of ways to do this with sed / awk etc.

save this as "formatasizer.py":

```
#!/usr/bin/python
import csv, sys, os

try:
	infile=open(sys.argv[1], 'r')
	if not os.path.exists(sys.argv[2]):
		outfile=open(sys.argv[2], 'w')
	else:
		print "stopping before I overwrite an existing file!!"
		sys.exit(1)
except IndexError:
	print "check commandline options: \nformatasizer.py <input-file> <output-file>"
	sys.exit(1)
except IOError:
	print "check input exists"
	sys.exit(1)

first_column_length=5
second_column_length=5

for line in csv.reader(infile, delimiter=' ', skipinitialspace=True):
	outfile.write("%s\t%s\t%s\n" % (line[0].zfill(first_column_length), line[1].zfill(second_column_length), line[2]))

outfile.close()
```

then run it from the commandline:

```
python formatasizer.py <input-file> <output-file>
```

It's pretty simple... with the following assumptions:

[LIST=1]
[*]first column should be 5 characters wide (with the 0's)
[*]second column should be 5 characters wide (with the 0's)
[*]third column doesn't need padding with spaces
[*]columns are separated by the space (' ') character
[*]that you want the output in a new file (ie. it won't overwrite anything)
[*]the output is separated by a tab ('\t') character
[/LIST]

hope that helps you!  

If you know any python you can make small changes to this to help you achieve what you need! :)

---

### Post by JCM_Pico on 2012-06-14
> **greenpeace said:**
> I would use Python... 

Thank you very much....
It worked perfectly for the example.... However the file is a bit different...

I don't know Python, but I'm not afraid of using it :p so I gave a try adapting the script... But it didn't work... I guess I'm missing something... 

I did this

```
#!/usr/bin/python
import csv, sys, os

try:
	infile=open(sys.argv[1], 'r')
	if not os.path.exists(sys.argv[2]):
		outfile=open(sys.argv[2], 'w')
	else:
		print "stopping before I overwrite an existing file!!"
		sys.exit(1)
except IndexError:
	print "check commandline options: \nformatasizer.py <input-file> <output-file>"
	sys.exit(1)
except IOError:
	print "check input exists"
	sys.exit(1)

first_column_length=6
second_column_length=5
third_column_length=5
fourth_column_length=5
fifth_column_length=2
sixth_column_length=4
seventh_column_length=3
eighth_column_length=2
nineth_column_length=5
tenth_column_length=5
eleventh_column_length=5

for line in csv.reader(infile, delimiter=' ', skipinitialspace=True):
	outfile.write("%s\t%s\t%s\n" % (line[0].zfill(first_column_length), line[1].zfill(second_column_length), line[2].zfill(third_column_length), line[3].zfill(fourth_column_length), line[4].zfill(fifth_column_length), line[5].zfill(sixth_column_length), line[6].zfill(seventh_column_length), line[7].zfill(eighth_column_length), line[9].zfill(nineth_column_length), line[9].zfill(tenth_column_length), line[10].zfill(eleventh_column_length), line[11]))

outfile.close()
```

and my file is attached

---

### Post by greenpeace on 2012-06-14
aaah, okok ... bonus points for giving it a try!! :)

You've specified the new column width, but the program doesn't know to output the new columns (I thought there were only 3 columns in the output!)

as there are a variable numbers of spaces separating the contents of the file it's very difficult to determine where the columns should be... 

is there anyway you get the input files into more of a CSV (comma-separated values) or TSV (tab-separated values) format?  

Alternatively, having a '0' or maybe a dash ('-') character where there is no data would be useful... 

is that possible?

---

### Post by Vaphell on 2012-06-14
```
awk 'NR==1 {print}; NR!=1 { printf("%05.1f %05d %s\n", $1, $2, $3) }'
```

example:
```
$ echo $'a b c\n107.0   6295  -67.1\n  2.0  18708  -63.0'
a b c
107.0   6295  -67.1
  2.0  18708  -63.0

$ echo $'a b c\n107.0   6295  -67.1\n  2.0  18708  -63.0'| awk 'NR==1{print};NR!=1{ printf("%05.1f %05d %s\n", $1, $2, $3) }'
a b c
107.0 06295 -67.1
002.0 18708 -63.0
```

awk '....' file > file2 to read from file1 and output results to file2

---

### Post by JCM_Pico on 2012-06-14
> **greenpeace said:**
> aaah, okok ... bonus points for giving it a try!! :)

You've specified the new column width, but the program doesn't know to output the new columns (I thought there were only 3 columns in the output!)

as there are a variable numbers of spaces separating the contents of the file it's very difficult to determine where the columns should be... 

is there anyway you get the input files into more of a CSV (comma-separated values) or TSV (tab-separated values) format?  

Alternatively, having a '0' or maybe a dash ('-') character where there is no data would be useful... 

is that possible?

The objective of change does columns is to be able to open the file in a csv format... in the present format I'm not able to import the file, because the separation between columns its not uniform :(

---

### Post by JCM_Pico on 2012-06-14
> **Vaphell said:**
> ```
awk 'NR==1 {print}; NR!=1 { printf("%05.1f %05d %s\n", $1, $2, $3) }'
```

example:
```
$ echo $'a b c\n107.0   6295  -67.1\n  2.0  18708  -63.0'
a b c
107.0   6295  -67.1
  2.0  18708  -63.0

$ echo $'a b c\n107.0   6295  -67.1\n  2.0  18708  -63.0'| awk 'NR==1{print};NR!=1{ printf("%05.1f %05d %s\n", $1, $2, $3) }'
a b c
107.0 06295 -67.1
002.0 18708 -63.0
```

awk '....' file > file2 to read from file1 and output results to file2

Tried to adapt you suggestion and got this :/

```
 awk 'NR==1 {print}; NR!=1 { printf("%05.1f %05d %03.1f %03.1f %02d %02.2f %03d %02d %04.1f %04.1f %04.1f", $1, $2, $3 $4 $5 $6 $7 $8 $9 $10 $11) }' d29.txt > dd.txt
awk: run time error: not enough arguments passed to printf("%05.1f %05d %03.1f %03.1f %02d %02.2f %03d %02d %04.1f %04.1f %04.1f")
	FILENAME="d29.txt" FNR=2 NR=2

```

---

### Post by greenpeace on 2012-06-14
right, OK... so it looks like you're going to have to split each line of a file at a given point in the line... if you have just one file, then the text-to-columns function of OpenOffice Calc will work well.

looks like the first column is 6 chars long, and then subsequent columns are 7 chars long... this means we can use this Python script to output a CSV file of the values:

```
#!/usr/bin/python
import csv, sys, os

try:
	infile=open(sys.argv[1], 'r')
	if not os.path.exists(sys.argv[2]):
		outfile=csv.writer(open(sys.argv[2], 'w'), delimiter=',')
	else:
		print "stopping before I overwrite an existing file!!"
		sys.exit(1)
except IndexError:
	print "check commandline options: \nformatasizer.py <input-file> <output-file>"
	sys.exit(1)
except IOError:
	print "check input exists"
	sys.exit(1)

first_column_width = 6
subs_column_width  = 7

for line in infile:
	i=first_column_width
	out=[line[0:i].replace(' ','')]
	for j in range(first_column_width+subs_column_width, len(line), subs_column_width):
		out.append(line[i:j].replace(' ', ''))
		i+=subs_column_width
	outfile.writerow(out)
```

It's very similar to the first, only now we're using the csv.writer() function to write the formatted CSV data to the file.

Also, we're using the replace(' ', '') function to remove the spaces from the data.

how's that?

---

### Post by JCM_Pico on 2012-06-14
> **greenpeace said:**
> 
how's that?

Pretty nice mate :) it worked like a charm

There is only one tiny thing when I stop to get data (eg. column 4, 5 and 6) but that ain't a problem... I can change the columns to the right place in openoffice... 

Thank you very much for the help given :)

---

### Post by greenpeace on 2012-06-14
Sem problemas! ;)

It should give you an empty "cell" when there's no data (it will look like two or more commas next to each other: ",," )... 

...so as long as you're opening in OpenOffice, and don't select "Merge Delimiters" so that should leave the columns ok!

---

### Post by JCM_Pico on 2012-06-14
nice... so the script is flawless :)
I need to learn Python... ;)

---

### Post by greenpeace on 2012-06-14
> **JCM_Pico said:**
> I need to learn Python... ;)

EVERYONE needs to learn Python :biggrin:

---

### Post by Vaphell on 2012-06-14
where are the commas? each %something requires a corresponding parameter. 11 %'s = 11 separate values listed.
```
printf("%05.1f %05d %03.1f %03.1f %02d %02.2f %03d %02d %04.1f %04.1f %04.1f",
$1, $2, $3[COLOR="Red"],[/COLOR] $4[COLOR="Red"],[/COLOR] $5[COLOR="Red"],[/COLOR] $6[COLOR="Red"],[/COLOR] $7[COLOR="Red"],[/COLOR] $8[COLOR="Red"],[/COLOR] $9[COLOR="Red"],[/COLOR] $10[COLOR="Red"],[/COLOR] $11) 
```

writing page worth of code for trivial reformatting purposes is a huge overkill

---

### Post by greenpeace on 2012-06-15
> **Vaphell said:**
> writing page worth of code for trivial reformatting purposes is a huge overkill

Not overkill if it works first time... whereas this awk script fails to separate the columns in the way the OP needed, because of the way his file is formatted.

---

### Post by Vaphell on 2012-06-15
file formatting is what awk does for a living.
example format looks straightforward and awk failed only because OP didn't bother to provide proper real life example and nail the syntax down (missing commas are a glaring omission), also it was not that obvious that what he really needed was a csv file.

---

