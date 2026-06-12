---
title: "Installer software"
date: 2012-05-08
forum: General Help
---

### Post by op3studios on 2012-05-08
hello,

I downloaded an executable program (truecrypt), extracted and set permissions, but the program association is off and the file is opened in Gedit, which makes for a pretty screen, but does not install the software.

What is the proper installation utility software to associate the setup file with?

thanks

Jim

---

### Post by 3rdalbum on 2012-05-08
I believe Truecrypt is in the repositories, so there's no need to seek it out elsewhere.

To run an executable program, you first need to add execute permission (which you say you've done) and then run it. Double-clicking on it doesn't usually run it, but you can certainly run it by dragging it into the terminal window and pressing Enter.

You may need to run it as root; type "sudo" into the terminal and then leave a spacebar character, and then drag the file into the terminal and press Enter.

---

### Post by Cheesemill on 2012-05-08
If it's a .deb file you can install it using gdebi:
```
gdebi filename.deb
```

---

### Post by op3studios on 2012-05-08
thank you for your replies.

the suggestions are great to know, and inspire me to take another look at learning the terminal better.

My problem is that the default 'handler' program (sorry I don't know the right word), is set as gedit, so the executable file executes, but loads into gedit instead of running a self-installation.

I need to know how to designate the 'handler' program that will be used to execute the executable execution uh....what's the name of that program in Ubuntu please...

must be teatime.:popcorn:

Jim

---

### Post by Cheesemill on 2012-05-08
The file you extracted is the installer, you just need to run it from the terminal....

OK then, first open a terminal and navigate to the location of the extracted file.
Then run the file by doing:
```
./truecrypt-7.1a-setup-x64
```Obviously you need to change the command slightly if your extracted filename is different to mine.

---

### Post by op3studios on 2012-05-08
the installer, when clcked, or run in terminal, calls up the wrong program, in this case gedit.

so if I were using the 'open with' dialogue, what program would I choose to install the program?  I tried to associate it with synaptic with no luck.

the self-installer is calling up the wrong processing program and I need to change associations to call up whatever is the program that handles program installs.

I need to get back to defaults in file associations.

thanks for input

---

### Post by op3studios on 2012-05-09
I'm pretty sure I understand the problem now.

I keep all my data files on a separate NTFS platter hard drive, including my downloads etc...

Soon as I moved the install files to my Artist X partition (SSD) the programs whistled merrily along and installed themselves without issue.

I noticed this issue first when trying to record audio to a separate drive, and considered it was a speed issue between the ssd and plater hard drives.

Now I wonder if it isn't an NTFS / permissions thing. well, anyway, it works.

thanks for your input.

---

