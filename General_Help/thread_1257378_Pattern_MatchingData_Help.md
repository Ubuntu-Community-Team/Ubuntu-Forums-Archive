---
title: "Pattern Matching/Data Help"
date: 2009-09-03
forum: General Help
---

### Post by Prospero2006 on 2009-09-03
Hello all, I could use some advice on writing a script:

I have two files. 
One looks like this:
[B][U]
Grades.txt[/U][/B]

Mary 100
John 90
Doug 85

The other looks like this:
[B][U]
ID Numbers[/U][/B]

Mary 000111
John 000222
Doug 000333

Now, I'm trying to figure out how to write a script using awk, sed, cut, or anything really that will produce output like this:

000111 100
000222 90
000333 85

I need to grab the name and score, read them into a variable, then compare the name variable against the id list and print **id number**, **score**.

Any shell wizardry out there tonight?
Thanks,
Pros

---

### Post by denarced on 2009-09-06
Nice little brainteaser for sundaymorning
Here's a tryout with a very un-efficient algorithm

```
#!/bin/bash

O=$IFS
IFS=`echo -en "\n\b"`
for fil in $(cat $1 | sort)
do
	name=$(echo $fil | sed 's:\(.*\) .*:\1:')
	for filu in $(cat $2)
	do
		nam=$(echo $filu | sed 's:\(.*\) .*:\1:')
		if [ "$nam" == "$name" ]
		then
			id=$(echo $filu | sed 's:.* \(.*\):\1:')
			points=$(echo $fil | sed 's:.* \(.*\):\1:')
			echo $id $points
		fi
	done
done
IFS=$O

```

---

### Post by DaithiF on 2009-09-06
this is kind of a 'toy' solution, in that it works for the supplied data, but won't scale well for real-world data, but just for fun:
```
sort grades.txt numbers.txt | sed 'N;s/^\([^ ]*\) \([0-9]*\)\n\1/\2/'
``````
xxxx@yyyyyy:~/tmp$ cat grades.txt
Mary 100
John 90
Doug 85
xxxx@yyyyyy:~/tmp$ cat numbers.txt
Mary 000111
John 000222
Doug 000333
xxxx@yyyyyy:~/tmp$ sort grades.txt numbers.txt | sed 'N;s/^\([^ ]*\) \([0-9]*\)\n\1/\2/'
000333 85
000222 90
000111 100
```

---

### Post by kaibob on 2009-09-06
The following works with the sample data provided:

```
join file1 file2 | cut -d " " -f 2,3
```

To illustrate:

> $ cat file1
Mary 000111
John 000222
Doug 000333

$ cat file2
Mary 100
John 90
Doug 85

$ join file1 file2 | cut -d " " -f 2,3
000111 100
000222 90
000333 85

An alternative, that sorts the data but is less like to break:

```
join <(sort file1) <(sort file2) | cut -d " " -f 2,3
```

SOURCE REFERENCE
[http://superuser.com/questions/25302/how-to-join-files-on-the-command-line-without-creating-temp-files](http://superuser.com/questions/25302/how-to-join-files-on-the-command-line-without-creating-temp-files)

---

### Post by Prospero2006 on 2009-09-07
Thanks for the solutions everyone. Wasn't familiar with some of that.
TY
Josh

---

