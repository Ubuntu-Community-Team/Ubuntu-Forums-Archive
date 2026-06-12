---
title: "How use &quot;ls&quot; command to get output for other app"
date: 2009-07-20
forum: General Help
---

### Post by marek23 on 2009-07-20
Hello,

I want write bash script, and have problem.

I need get all files in directory.
To do this i can use "ls" command.

Output  of " ls" command will be list of files in directory.

1.avi 
Scanned picture.png
1.png
Scanned picturew.png
Scanned picturrew.png

How can i use this output with other application like zip or send by email.

some thing like

zip **(ls - first position)** my.zip

or

mutt -s "test test" -a  **(ls - first position)**  adres@email <content.txt

I need this in loop, what goes in all files showed usually by ls.

normal ls

1.avi 
Scanned picture.png
1.png
Scanned picturew.png
Scanned picturrew.png

**add loop for zip and i need something like this**

zip 1.avi 
zip Scanned picture.png
zip 1.png
zip Scanned picturew.png
zip Scanned picturrew.png
Zip is only example !

I don't know, i said this correctly.

So i will say again in simplest word.

I want use output  (each line) of "ls" with my command.


Regards

---

### Post by wojox on 2009-07-20
Why don't you just zip the folder?

---

### Post by Niksko on 2009-07-20
You could do something like this:

```
#!/bin/bash

Lines=`ls | wc -l`
Count=0
ls > list
while [ $Count -lt $Lines ]
do
File=`head -$Count list | tail -1`
zip $File.zip $File
Count=`expr $Count + 1`
done
rm list list.zip


```

That will zip all the files in the directory it's in

-Nik

EDIT, just realised that zip was only an example

The key line is:
```
head -$Count list | tail -1
```
To use that on ls you would do:
```
ls | head -$Count | tail -1
```
Where $Count is the line number.

---

### Post by benj1 on 2009-07-20
are you wanting to zip them all separately or as one big file 

to do it individualy

```
for file in *; do gzip $file; done
```

you don't need 'ls', '*' just matches anything so *.png would match all png files

im not sure about emailing, mutt isn't something i use.

if you want to learn bash scripting have a look at this, (its not advanced as the name implys)

---

### Post by Niksko on 2009-07-20
Well, that just shows my scripting inexperience. Heh

-Nik

---

### Post by marek23 on 2009-07-20
I said,  zip is only example.
I know, i can put everything in one archive, but that's not point.


I will ask it in other way.
I have few archives, split by size of CD disk.

I need burn them in to my cd-disk, but i can't select everything by *.* because there are too big.

So first i need burn disk with contain first file, next second file, and again again again (...); until finish.

So i need do something like this:

use   "ls"
Look at files list
file1
file2
filezz
filexsd
(...)

And then do
burn xxx **file1** label='part1/20'
ok, then again
burn xxx **file2** label='part2/20'
next
burn xxx **filezz** label='part3/20'
(...)
until finish.


I really have no idea how to deal with that.
I want this automatic, in bash, not manual like in example above.

I cant figure out any command what allow me "cut" this output into lines..
I have try with greep

```

ls
DSCF0023.JPG  DSCF0024.JPG  DSCF0025.JPG  DSCF0026.JPG  DSCF0027.JPG  DSCF0028.JPG  Originals  Picasa.ini



ls >>temp.txt

grep -n "" temp.txt 
1:DSCF0023.JPG
2:DSCF0024.JPG
3:DSCF0025.JPG
4:DSCF0026.JPG
5:DSCF0027.JPG
6:DSCF0028.JPG
7:Originals
8:Picasa.ini

cat temp.txt | head -2 | tail -1
DSCF0024.JPG


```Now we can put this 
"cat temp.txt | head -2 | tail -1" in for loop 
-2 will be our x
but i don't know range for the loop.

Loop start from 1 to x
but how get last element line number

---

### Post by marek23 on 2009-07-20
Thank you **benj1**.
You solve my problem.

I don't know, is there for **file** loop :)
I'm try to work it around so hard.

I'm very glad to use you're solution.


Regards

---

### Post by benj1 on 2009-07-20
> **Niksko said:**
> Well, that just shows my scripting inexperience. Heh

-Nik

well yours looks more impressive :P

im not that good either, that just happens to be one bash thing i know, tend to use python more.

@marek23
the name file isn't important thats just a variable name, just as long as variable and $variable match

---

### Post by marek23 on 2009-07-20
I got that.


I have another problem, don't know why but IF statement wont work.

```

enabled=1;
if [$enabled = 1];
then
echo "Option has been enabled";
else
echo "Option has been disabled";
fi

```
Always i got "disabled" (else statement).

---

### Post by kaibob on 2009-07-20
Change the second line to:

```
if [ "$enabled" -eq 1 ];
```

There has to be spacing as shown. Also, although I believe it will work either way in this instance, = (equal sign) is for string comparison, and -eq is for integer comparison.

---

### Post by marek23 on 2009-07-20
> **kaibob said:**
> Change the following line:

```
if [ $enabled -eq 1 ];
```There has to be spacing as shown. Also, equal sign is for string comparison; -eq is for arithmetic comparison.

Hello,

I tray that but it don't work :(

Now i have
```

if [ $enabled -eq 1 ];

```

---

### Post by decoherence on 2009-07-20
For your complete code, try

```
enabled=1;
if [ $enabled -eq 1 ];
then
echo "Option has been enabled";
else
echo "Option has been disabled";
fi

```

this works for me. If it still doesn't work for you, try running it in shell debugging mode
```

sh -x nameofyourscript.sh
```

see if you can spot where it goes wrong, or paste the output here

---

### Post by marek23 on 2009-07-20
Thank you.

It start working, i forgot space after 

eq 1_HERE_I_FORGOT_SPACE] 


So, i will say it again Thank you.


BTW: It's look quiet complicated for someone who work with PHP where are no traps like this one. But it's very user-full and power-full.

---

### Post by decoherence on 2009-07-20
> **marek23 said:**
> BTW: It's look quiet complicated for someone who work with PHP where are no traps like this one. But it's very user-full and power-full.

BASH scripts are not known for being readable or easy to understand. The joke is that you can do anything in a single line of code, but it'll take hours to figure out how.

BASH (and shell scripts in general) is extremely well suited to dealing with files or configurations, or building a job out of many different programs. Once you figure out the 'traps' it's pretty hard to beat.

In cases where you need to structure data in specific ways, or if you aren't calling a bunch of programs from the operating system to do your bidding, you're almost always better off with Python or Perl.

---

### Post by benj1 on 2009-07-20
> **decoherence said:**
> 
BASH (and shell scripts in general) is extremely well suited to dealing with files or configurations, or building a job out of many different programs. Once you figure out the 'traps' it's pretty hard to beat.

the problem is after youve figured out the bash traps you then have the awk traps and the sed traps.

i personnally don't use bash for anything more than one liners, after that i go onto python

---

### Post by decoherence on 2009-07-20
> **benj1 said:**
> the problem is after youve figured out the bash traps you then have the awk traps and the sed traps.


They don't say "shell scripting is for masochists" for nothing!

That said, if you know the various traps bash throws at you (and more importantly, *why*), then you know the fundamentals of the command line.

---

