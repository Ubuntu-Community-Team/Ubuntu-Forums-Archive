---
title: "bash script will not respect &quot;exit 0&quot;"
date: 2009-06-29
forum: General Help
---

### Post by rjs2006 on 2009-06-29
All,

I am a complete ubuntu newb trying to learn.

the echo in this piece of code prints out to stdout:

cat /home/bob/my_work/projects/equity_db/holidays/schedule.csv | while read line; do
	echo $line   #line contains 20090629
	echo $DATE   #date here is 20090629
	COMPARE=$((line-DATE))
	echo $COMPARE   #this comes out to 0

	#if ever the current date matches a holiday date, exit the script
	if [ "$COMPARE" -eq "0" ]
	then
		echo "Day is a holiday and script will not continue with processing"
		exit 0
	fi

done

however the script never exits???  Can anyone tell me why?  $COMPARE is 0 triggering the echo.  

thanks,
bob

---

### Post by t4thfavor on 2009-06-30
make sure your DATE command is coming back in the correct format, I think that may have something to do with it.

---

### Post by kaibob on 2009-06-30
I think you have to define the date as in the following:

```
DATE=$(date  +%Y%m%d)
```

Also, the following line has to be modified:

```
COMPARE=$(($line-$DATE))
```

I made these changes and the shell script appears to run as you want.

BTW, as your shell script is presently written, the schedule file has to have each date on a separate line without anything else. I don't believe this is normally the case with a csv file. If the schedule file is comma-separated, perhaps you could pipe it through the tr utility.

---

### Post by rjs2006 on 2009-06-30
thanks for replies.

DATE is a variable being concatenated somewhere else and on echo returns 20090629 (yesterday), 20090630 (today).

When I "echo $COMPARE" this is printing 0 on screen so I remain confused here.

The csv file extension is misleading...sorry.  The file does have dates line by line, no commas are in the file.

COMPARE=$(($line-$DATE)) - > this I will try and let you know.

thanks much.

---

### Post by asmoore82 on 2009-06-30
> **rjs2006 said:**
> 
COMPARE=$(($line-$DATE)) - > this I will try and let you know.

thanks much.

This was right the first time ...
variables do not need $ inside of the $(( ... ))

I believe the reason it's not exiting is this ...

re-arrange the
```
cat *file* | while
do
done
```
to this contruct:
```
while
do
done < *file*
```
and see if that fixes it.

I believe that the use of a pipe creates a subprocess and only *that* subprocess is exiting ...
you can rewrite the pipe statement like this and
the scope of the exit statement becomes more clear:
```

echo hello | (
   cat
   exit 1
)
echo world

```

just for the sake of completeness, another possible solution
without rearranging the while loop would be like this:
```
echo hello | (
   cat
   exit 126
)
[ "$?" -eq "126" ] && exit 1
echo world

```
^^this is testing for a specific exit code of the subprocess immediately after it,
and terminating the main script on that condition.

---

### Post by kaibob on 2009-06-30
I copied and pasted your exact code into a shell script. The only difference is that I defined the variable DATE as shown below and used a different date file name and path. The script worked fine. So, I don't know why $COMPARE is always returning a 0 for you. My guess would be that there is a problem with the $DATE or $line variables but that should be evident when the script echoes these variables. So, I'm not sure what is going on. Sorry I couldn't help. 

BTW, as noted by asmoore82, what I wrote last night about the line that begins with COMPARE= and performs arithmetic expansion is incorrect. The line as written should work. 

```
#!/bin/bash

DATE=$(date  +%Y%m%d)

cat /home/kaibob/datefile.txt | while read line; do
echo $line
echo $DATE
COMPARE=$((line-DATE))
echo $COMPARE #this comes out to 0

#if ever the current date matches a holiday date, exit the script
if [ "$COMPARE" -eq "0" ]
then
echo "Day is a holiday and script will not continue with processing"
exit 0
fi

done
```

> kaibob@dell:~$ datescript
20090607
20090630
-23
20090606
20090630
-24
20090112
20090630
-518
20090630
20090630
0
Day is a holiday and script will not continue with processing

---

### Post by asmoore82 on 2009-06-30
> **kaibob said:**
> The line as written should work.

I believe the OP's understated problem is that he has lines that he didn't  show us
beyond that last `done` - that are always executing no matter what.

---

### Post by asmoore82 on 2009-06-30
Another good cleanup would be to eliminate the arithmetic altogether:

```

if [ "$line" = "$DATE" ]
...
```

the shell is a text processing powerhouse - which is why you must use `-eq`
 for comparing numbers - but a simple `=` in the [ ... ] construct
is understood to be a string comparison.

A nasty bug can lay dormant in your script when using dates and the $(( ... )) -
numbers with leading zeros in there are assumed to be in octal:
[http://www.commandlinefu.com/commands/view/2385/super-speedy-hexadecimal-or-octal-calculations-and-conversions-to-decimal.#comment](http://www.commandlinefu.com/commands/view/2385/super-speedy-hexadecimal-or-octal-calculations-and-conversions-to-decimal.#comment)

---

### Post by kaibob on 2009-06-30
> **asmoore82 said:**
> I believe the OP's understated problem is that he has lines that he didn't  show us
beyond that last `done` - that are always executing no matter what.

I'm sure that is the case--especially with the script-never-exits problem. Perhaps the OP will post his entire shell script.

BTW, I agree that the shell script could be better written, eliminating cat and using test rather than arithmetic expansion. Good suggestions.

---

### Post by t4thfavor on 2009-06-30
heryago
```

cat /home/chance/schedule.csv | while read line; 
do
	#echo $line #line contains 20090629
	holidayDate=$(date +%Y%m%d)
	COMPARE=$((line - holidayDate))
	echo "Line = " $line
	echo "Date = " $holidayDate
	echo " Compare = "$COMPARE #this comes out to 0

	#if ever the current date matches a holiday date, exit the script
	if [ "$COMPARE" -eq "0" ]
	then
		echo "Day is a holiday and script will not continue with processing"
		exit
	fi

done

```

---

### Post by asmoore82 on 2009-06-30
> **t4thfavor said:**
> heryago
```

cat /home/chance/schedule.csv | while read line; 
do
	#echo $line #line contains 20090629
	holidayDate=$(date +%Y%m%d)
	COMPARE=$((line - holidayDate))
	echo "Line = " $line
	echo "Date = " $holidayDate
	echo " Compare = "$COMPARE #this comes out to 0

	#if ever the current date matches a holiday date, exit the script
	if [ "$COMPARE" -eq "0" ]
	then
		echo "Day is a holiday and script will not continue with processing"
		exit
	fi

done

```
```
cat /home/chance/schedule.csv | while read line; 
do
	#echo $line #line contains 20090629
	holidayDate=$(date +%Y%m%d)
	COMPARE=$((line - holidayDate))
	echo "Line = " $line
	echo "Date = " $holidayDate
	echo " Compare = "$COMPARE #this comes out to 0

	#if ever the current date matches a holiday date, exit the script
	if [ "$COMPARE" -eq "0" ]
	then
		echo "Day is a holiday and script will not continue with processing"
		exit
	fi

done

[COLOR="Red"]echo "This should not be seen - but is it??"[/COLOR]
``` :evil: ... :razz:

---

