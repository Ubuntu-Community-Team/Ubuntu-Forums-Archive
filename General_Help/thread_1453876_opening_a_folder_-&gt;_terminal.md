---
title: "opening a folder -&gt; terminal"
date: 2010-04-13
forum: General Help
---

### Post by Konbuntu on 2010-04-13
[SIZE=4][SIZE=2]I'm tryin to open a folder using the terminal. i always get an error. here is what i am trying to do:

kon@kon-laptop:~$ cd ~/Desktop
kon@kon-laptop:~/Desktop$ ls
A History of Opera.pdf
Dvorak 
Handel - Manze - Concerti Grossi, Op.6 
John Adams - Harmonielehre
nietzsche~
Nietzsche - The Antichrist.epub
opera_0756622042.pdf
Philosophy of the Marquis de Sade-gPG.pdf
kon@kon-laptop:~/Desktop$ [/SIZE]

[SIZE=2]i'm trying to open the folder called "Dvorak", so i can split my ape file... anyways i hope someone will be able to help me... thanks![/SIZE]
[/SIZE]

---

### Post by lisati on 2010-04-13
Try:
```
cd Dvorak
```
(cd = "change/current directory", i.e. go to a new folder)

---

### Post by v1ad on 2010-04-13
or cd ./Dvorak cd Dvorak will work fine also

---

### Post by Konbuntu on 2010-04-13
this is what i get:

kon@kon-laptop:~/Desktop$ cd Dvorak
bash: cd: Dvorak: No such file or directory

just one thing.. "Dvorak" is highlighted in blue... maybe that means something or maybe not

---

### Post by lyall on 2010-04-13
try entering on the terminal screen 
ls -l
and see what permissions are for Dvorak

good luck and have fun learning

---

### Post by Konbuntu on 2010-04-13
drwxr-xr-x 12 kon kon     4096 2010-04-12 18:20 Dvorak 

i like learning but today is quite not the day for me to learn!
but yes.. learning can be fun! hehe

---

### Post by v1ad on 2010-04-13
make sure you are in the same directory of dvorak. also remember that it is very case sensitive.

do pwd
and then do cd /theworkingdirectory/Dvorak
it will probably end up being
cd /home/username/Dvorak or something similar. make sure that there is no spaces saved with the Dvorak file name. 
the blue means that it is a folder.

---

### Post by Konbuntu on 2010-04-16
i don't get this...
i'm doing whatever you are telling me to do and it still doesn't work =/

kon@kon-laptop:~/Desktop$ cd /home/kon/Desktop/Dvorak
bash: cd: /home/kon/Desktop/Dvorak: No such file or directory
kon@kon-laptop:~/Desktop$

---

### Post by The Cog on 2010-04-16
There might be funny characters in it. Do **cd /home/kon/Desktop** to change to the containing directory, and then type "cd D" (without the quotes) and then press the tab key - this should fill in the rest of hte filename for you, and should handle any hidden characters in the name properly (provided the directory does actually start with "D"). It's called "filename completion" and it's really handy for typing long or difficult filenames.

---

### Post by Konbuntu on 2010-04-16
this is sooooooooo strange: how come i'm having such a hard time?
this folder contains music in Ape. formats
all i want to do is convert my Ape files to Flac and then split the fies. the only way i can do this is by using the terminal...

so i tried doing what you told me and NOTHING =/  
maybe the folder has some restrictions on it.. but if it does i wouldn't know how to recognize and fix the problem.

anyways, thanks for all the help im getting  so far...

---

### Post by Konbuntu on 2010-04-16
i did what you told me and by pressing tab nothing happens and by pressing ENTER this is what i get:

kon@kon-laptop:~$ cd /home/kon/Desktop
kon@kon-laptop:~/Desktop$ cd D
bash: cd: D: No such file or directory
kon@kon-laptop:~/Desktop$ 

and if i insert "ls" you can see that Dvorak ( i changed to sDvorak) does exist:

kon@kon-laptop:~/Desktop$ ls
A History of Opera.pdf
Handel - Manze - Concerti Grossi, Op.6 
John Adams - Harmonielehre
nietzsche~
Nietzsche - The Antichrist.epub
opera_0756622042.pdf
Philosophy of the Marquis de Sade-gPG.pdf
sDvorak 
kon@kon-laptop:~/Desktop$

---

### Post by KeyserSoze93 on 2010-04-16
This is strange.

Try:

```

cd *ora*

```

---

### Post by linden940 on 2010-04-16
Konbuntu when your posting things from terminal/code do it with the code command [ code ] what ever your code is here [ / code ] so it will look like this

```
what ever your code is here
```

---

### Post by Serpher on 2010-04-16
Try typing in

```
cd ~/Desktop/Dvorak/
```

If that still doesn't work copy paste the output here of:

```
file ~/Destkop/Dvorak
```

Check the spelling of Devorak with:

```
ls ~/Desktop/
```

---

### Post by The Cog on 2010-04-16
How about this: post the output from these two commands:
> cd ~/Desktop
ls | hexdump -C

---

### Post by Konbuntu on 2010-04-16
> **KeyserSoze93 said:**
> 
cd *ora*



yesssssssssssssssssssss! =)

thank you  thank you and thank you =)

---

