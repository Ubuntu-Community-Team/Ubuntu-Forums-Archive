---
title: "sed for a loop"
date: 2011-08-29
forum: General Help
---

### Post by maclenin on 2011-08-29
I am trying to coax sed into setting up a (very) large array for me....

Essentially:

A. I have created a database of hundreds of images.
```
0001.jpg
0002.jpg
0003.jpg
0004.jpg
0005.jpg
...
0400.jpg
```

B. I have used sed to scrub the data to (among other things) remove file extensions...
```
0001
0002
0003
0004
0005
...
0400
```

C. ...and set up the images in an array format that I intend to incorporate into a web-based image viewer:
```
image[i]="0001";
image[i]="0002";
image[i]="0003";
image[i]="0004";
image[i]="0005";
...
image[i]="0400";
```

**The crux of the issue:**

I am now trying to use a for loop to have sed replace the "i" with a sequence from 0 to 399, to produce:
```
image[0]="0001";
image[1]="0002";
image[2]="0003";
image[3]="0004";
image[4]="0005";
...
image[399]="0400";
```

My attempts (within a bash script)...
```
for ((i=0; i<400; i++))
do
sed -r 's/image\[i\]/image\['$i'\]/' -i array.txt
done
```
...are not yielding the results I crave (it looks as though I am (perhaps properly) looping through the array of 400 images 400 times!)!

Thanks for any suggestions!

---

### Post by sisco311 on 2011-08-29
Try:

```

index=0
while read -r line
do
    echo "${line/\[i\]/[$index]}"
    ((index++))
done < array.txt > newarray.txt

```

EDIT: renamed the variable i to index.

---

### Post by maclenin on 2011-08-29
Perfect!

I usually endeavor to come up with solutions on my own - but wow - can you break down (the syntax of) what you've gifted?

You have created a while loop which reads the number of lines in array.txt and replaces the "i" on each of those lines - in sequence, starting with "line" 0 and up to the number of lines (-1), via echo - to newarray.txt.... 

Thank you, **sisco311!**

---

### Post by sisco311 on 2011-08-29
See:
[http://mywiki.wooledge.org/BashFAQ/001](http://mywiki.wooledge.org/BashFAQ/001)
and
[http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion](http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion)

**index=0** sets the value of index to 0

[B]while read -r line
do
    :
done < array.txt[/B]

reads array.txt line-by-line.

**${line/\[i\]/[$index]}** replaces [i] with the value of index (in square brackets).

**echo** prints the line

**((i++))** increments the value of i, it's the equivalent of ((i=i+1))

**> newarray.txt** redirects the output to newarray.txt

---

### Post by maclenin on 2011-08-30
Thanks, **sisco311**.

Note: I used the variable "i" - worked fine for me (vs. index).... Was the renaming to prevent confusion with the original \[i\]?

---

### Post by sisco311 on 2011-08-30
> **maclenin said:**
> Thanks, **sisco311**.


You're welcome!

> **maclenin said:**
> 
Note: I used the variable "i" - worked fine for me (vs. index).... Was the renaming to prevent confusion with the original \[i\]?

yep

---

