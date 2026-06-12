---
title: "&quot;ls&quot; command question"
date: 2010-01-25
forum: General Help
---

### Post by tripler on 2010-01-25
I'd like to modify the ls command so I can specify a file and only list files with a later date-stamp. Is that possible? What would the command be?

Thanks

---

### Post by audiomick on 2010-01-25
Hi.
I can't try that to check at the moment, I am on a windows machine.
If you do
```
man ls
```
and read through that, you should find what you need

---

### Post by llamabr on 2010-01-25
I'm not sure I understand what you want.  You want to list them by date, rather than alphabetically?  it's

```
ls -c
```

If I have it wrong, maybe spell out a bit more explicitly what you want.

---

### Post by Leppie on 2010-01-25
i think you're actually looking for something like the "find" command rather than ls...

---

### Post by SoFl W on 2010-01-25
I use an alias command in my ".bashrc" file because it is easier to remember the command rather than the command line options.  This lists the latest files at the bottom with all the file info:
```
alias udir='ls -latrh' 
```
(stands for ubuntu directory)


Try "ls --help" for a list of all the options.

---

### Post by danastasio on 2010-01-25
I know what he's asking (I think) he wants to invoke ls, which prompts him for a file, lets say file abc, ls then finds anyfile with a datestamp later than abc and returns it to the user.

No, I do not believe that this is possible, nor is it possible to modify the executable files that the commands are run from.

---

### Post by llamabr on 2010-01-25
> **danastasio said:**
> 
No, I do not believe that this is possible, nor is it possible to modify the executable files that the commands are run from.

I like reading this, because I always take it as a personal challenge.  Of course it's possible to manipulate text and data in a million different ways.  

But I agree, I don't think that ls is the right tool for this.  What you want is some combination of find, inside of a shell script with awk and sed.

Maybe a specific example of what you want would help.

---

### Post by tripler on 2010-01-25
Sorry if I wasn't very clear. I've been running this command
```
ls -1tr > files.txt
``` to get a txt file listing the files in that directory. Now I want to made a txt file listing only files created after a certain date. So I want to specify a file, eg. 
```
201001261059.jpg
``` and list only the files in the directory which were created after the file above.

Hope that makes sense.

---

### Post by danastasio on 2010-01-25
> **llamabr said:**
> I like reading this, because I always take it as a personal challenge.  Of course it's possible to manipulate text and data in a million different ways.  

But I agree, I don't think that ls is the right tool for this.  What you want is some combination of find, inside of a shell script with awk and sed.

Maybe a specific example of what you want would help.

:P But no, I mean I actually think its NOT possible at all. I remember once I tried to nano the file for cd just for the hell of it. And nano couldn't understand the file at all.

> nano /bin/cp

gives

> ^?ELF^B^A^A^@^@^@^@^@^@^@^@^@^B^@>^@^A^@^@^@&#65533;,@^@^@^@^@^@@^@^@^@^@^@^@^@^P&#65533;^A^@$
&#65533;Y_&#65533;&#65533;&#65533;&#1913;1&#65533;@ù&#65533;&#65533;\&#65533;&#65533;nbja^@^@^@&#65533;^@^@^@|^@^@^@^@^@^@^@X^@^@^@^Y^@^@^@^@^@^@^@^M^@^@^@$
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^^^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^$
^@^@^@^@^@^@^@^@^@^@^@P&#65533;a^@^@^@^@^@^G^@^@^@^K^@^@^@^@^@^@^@^@^@^@^@X&#65533;a^@^@^@^@^$
^@^@^@&#65533;@&#65533;&#65533;&#65533;&#65533;%Bj!^@h^K^@^@^@&#65533;0&#65533;&#65533;&#65533;&#65533;%:j!^@h^L^@^@^@&#65533; &#65533;&#65533;&#65533;&#65533;%2j!^@h^M^@^@^@&#65533;^P&#65533;&#65533;&#65533;&#65533;%*j$
j!^@h^R^@^@^@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%^Bj!^@h^S^@^@^@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;i!^@h^T^@^@^@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;i!^@h^U^@^@^@&#65533;&#65533;$
i!^@h2^@^@^@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%^Bi!^@h3^@^@^@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;h!^@h4^@^@^@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;h!^@h5^@^@^@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;$
h!^@hR^@^@^@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%^Bh!^@hS^@^@^@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;g!^@hT^@^@^@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;g!^@hU^@^@^@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;$
g!^@hr^@^@^@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%^Bg!^@hs^@^@^@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;f!^@ht^@^@^@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;f!^@hu^@^@^@&#65533;&#65533;&#65533;&#65533;&#65533;1$
H&#65533;&#65533;^AH&#65533;G(H&#65533;^\$H&#65533;l$^HL&#65533;d$^PH&#65533;&#65533;^X&#65533;H&#65533;^\$H&#65533;l$^H&#65533;
^@^@^@L&#65533;d$^PH&#65533;&#313;^X&#65533;^K&#1913;&#65533;&#65533;ff.^O^_&#65533;^@^@^@^@^@UH&#65533;&#65533;AWI&#65533;&#65533;AVAUATI&#65533;&#65533;SL&#65533;&#761;H&#65533;&#65533;8^D^@^@H&#65533;E^X&#65533;$
^@^@D&#65533;&#65533;&#65533;&#65533;?&#65533;&#65533;^L&#65533;&#65533;&#65533;&#65533;{!^@^O&#65533;&#65533;^L^@^@A&#65533;&#65533;^@@^@^@


pages and pages of that. I don't -think- theres any editor that can read it. Please correct me if im wrong though :guitar:

---

### Post by danastasio on 2010-01-25
I just read that...

> ^?ELF^B^

Elves.... our computers use elves to operate... thats it I give up, computers are magic. I wonder if I can find "santa" in the file for sudo... xD

---

### Post by Leppie on 2010-01-25
check out the -newerXY option for find:
```
man find
```

---

### Post by falconindy on 2010-01-25
> **danastasio said:**
> I just read that...



Elves.... our computers use elves to operate... thats it I give up, computers are magic. I wonder if I can find "santa" in the file for sudo... xD
The basis of any binary file in Linux is [ELF]("http://en.wikipedia.org/wiki/Executable_and_Linkable_Format").

---

### Post by tripler on 2010-01-28
Here's how to do what I wanted. 

First create a date marker for the desired time stamp.
```

touch -d "28 january 2010 17:54:19" date_marker
```Next list all the files created after the date specified above and put them into a txt file:
```
find . -newer date_marker > files.txt
```

---

### Post by tripler on 2010-01-28
One more question...
```
find . -newer date_marker > files.txt
```The command above creates a txt file in this format:
> .
./hap_201001271412.jpg
./hap_201001281115.jpg
./hap_201001270757.jpg
./hap_201001261715.jpgbut I need it to be in this format: 
> hap_201001271412.jpg
hap_201001281115.jpg
hap_201001270757.jpg
hap_201001261715.jpgwhich is what I get with the command:
```
ls -1tr > files.txt
```How can I make the find command create a txt file in the same format as the ls command?

---

### Post by falconindy on 2010-01-28
If all you're looking to do is rip off the first 2 characters of the line, cut will solve this quickly:

```
find . /path/to/search -moreargs | cut -c3- > outfile.txt
```

You can use basename as well in find:
```
find . /path/to/search -moreargs -exec basename "{}" \;
```

Both will properly handle white space as well.

---

### Post by tripler on 2010-01-28
thanks, falconindy. I found that deleting the first line allows me to make an avi (my final objective) with
```
mencoder -nosound -ovc lavc -lavcopts vcodec=mpeg4 -o test.avi -mf type=jpeg:fps=30 mf://@files.txt
```
BUT I now realise "find" doesn't list the files in order ("ls" does) so the avi is a meaningless jumble.

So is there something I can add to the "cut" command to get them back in order?

---

### Post by t4thfavor on 2010-01-29
> **tripler said:**
> thanks, falconindy. I found that deleting the first line allows me to make an avi (my final objective) with
```
mencoder -nosound -ovc lavc -lavcopts vcodec=mpeg4 -o test.avi -mf type=jpeg:fps=30 mf://@files.txt
```
BUT I now realise "find" doesn't list the files in order ("ls" does) so the avi is a meaningless jumble.

So is there something I can add to the "cut" command to get them back in order?

Pipe the output to sort before you redirect into the text file, I believe it can sort by mdate.

Should do it
find . -newer Rusume.doc| sort -k 2,2n| cut -c3- > outfile.txt

---

### Post by tom.swartz07 on 2010-01-29
> **falconindy said:**
> The basis of any binary file in Linux is [ELF]("http://en.wikipedia.org/wiki/Executable_and_Linkable_Format").

:lolflag::lolflag:

---

### Post by t4thfavor on 2010-01-29
Couldn't you write a small shell script to find all files newer than this file, move them into a temp directort, then create the ls -ltr which would have the correct order? I think this would be easier.

I know my example above does not work, it was a coincidence that it did what I wanted it to.

```

#!/bin/bash
#Set an array of files newer than the first arg. 
#You could add -iname to weed out non images
files=$(find . -maxdepth 1 -type f -newer ${1});
#Make a tmp directory to hold all the newer files.
mkdir ./tmp;
#loop the file array
for file in $files;
do 
        #copy all the newer files into the tmp dir
        #preserving the create date. !!Very IMPORTANT!!
	cp -p $file ./tmp;
done
#Create a listing sorted by modified date but only containing the filename
#in form "file.jpg"
ls -ltr ./tmp|awk '{print $8}' > ./tmp/file.txt;
#add your movie command here 
mencoder -nosound -ovc lavc -lavcopts vcodec=mpeg4 -o test.avi -mf type=jpeg:fps=30 mf://@./tmp/file.txt

```

---

### Post by whiteychs on 2010-01-29
```
#/usr/bin/env python
import os
import sys
import re

dir = os.popen('ls -lrt') 
dir.readline()
sent = 0
wanted = ''
for x in dir:
	if sent == 1:
		wanted = wanted + x
	if x.find(sys.argv[1]) != -1:
		sent = 1
dir.close()
lines = wanted.split('\n')
lines.pop()
print lines
os.system('rm Final.txt && touch Final.txt')
f = open('Final.txt', 'r+')
for x in lines:
	x = x.split(' ')
	x = x[len(x) - 1]
	if x.find('.jpg') != -1:
		f.write(x + '\n')
f.close

```

I did it with a quick and bloated python script that writes the files to Final.txt in case the previous bash script doesn't work.

---

### Post by tripler on 2010-01-29
> **t4thfavor said:**
> 
I know my example above does not work, it was a coincidence that it did what I wanted it to.

What d'you mean it doesn't work, t4thfavor? Seems to work ok.

I do
```
touch -d "26 january 2010 05:00:00" date_marker
```then
```
find . -newer date_marker| sort -k 2,2n| cut -c3- > output.txt
```then
```
mencoder -nosound -ovc lavc -lavcopts vcodec=mpeg4 -o movie.avi -mf type=jpeg:fps=30 mf://@output.txt

```And I get my avi looking how it should. Thanks!

(scripts are a bit beyond me)

---

### Post by t4thfavor on 2010-01-29
Well I defer to the person with correct data to use it on, I was getting inconsistant results with my tests.

That's why I wrote the previous BASH script.

Scripts are easy, if your into Linux, you gotta learn a little.

---

