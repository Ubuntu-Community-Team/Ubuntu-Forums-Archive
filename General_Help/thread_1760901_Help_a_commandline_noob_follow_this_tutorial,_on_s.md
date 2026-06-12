---
title: "Help a commandline noob follow this tutorial, on setting up Natty?"
date: 2011-05-17
forum: General Help
---

### Post by TheoJava on 2011-05-17
I don't have a complete aversion to using the commandline, but I do have an almost complete lack of experience with it. So very much of how this stuff works is Greek to me. This is the tutorial:

[http://ubuntuforums.org/showthread.php?t=1615564&highlight=asus+u43jc](http://ubuntuforums.org/showthread.php?t=1615564&highlight=asus+u43jc)

I've installed Natty on this model of laptop, alongside Windows 7. I was able to do the first portion of code, but I can't figure out how to proceed with the second (this part: "Apply the following patch to DSDT.dsl"...) Also, I've shut down the laptop, and restarted since doing the first portion of commands, so I'm not even sure if I should start over from the very beginning again, or continue from the next part.

---

### Post by TheoJava on 2011-05-18
Bump

---

### Post by wojox on 2011-05-18
The second portion calls for you to create a file in that directory and call it DSDT.dsl

Copy and paste that code in and save.

Then open a terminal cd to that directory and compile the patch.

---

### Post by Frogs Hair on 2011-05-18
The best thing may be to send a message to the author of the tutorial , otherwise you may have to wait for someone who has successfully used it before .

---

### Post by TheoJava on 2011-05-20
Well, I did leave a post in that topic, but no one has replied yet. So rather than bugging them further, I figured it'd be better to just make this topic, for anyone interested in helping out. It'll be fun! =^]

I seem to already have a collection of files in the src/acpidump directory, one of which is the DSDT.dsl file. I'm guessing that's a result of the first block of commands? Actually, I'd kinda like to back and learn exactly what's going on in the first block of commands anyway. I'll leave comments by each line of code:

```
$ cd 
$ mkdir -p src/acpidump 
$ cd src/acpidump 
$ sudo apt-get install acpidump iasl 
$ sudo acpidump > acpidump.txt && sudo acpixtract acpidump.txt && iasl -d DSDT.dat
```The first line and third line are obvious to me.

As I understand it, the second line is meant to create the src/acpidump directory, right? What is the '-p' for?

The fourth line is clear enough, though I don't know what 'acpidump iasl' is.

The last line is where I start to get a little confused. I'm assuming it's what's largely responsible for the group of files which are now sitting in the src/acpidump directory, but beyond that it doesn't make much sense to me. Also, what is the '-d' for?

At any rate, I'm guessing it doesn't matter much, since I've already entered those commands. So umm, how do I go about patching the DSDT.dsl file?

---

### Post by Vaphell on 2011-05-20
**mkdir --help** to see what -p does

**sudo apt-get install acpidump iasl** installs two packages: acpidump and iasl

X && Y means - do Y if X completed successfully, so the last line is a chain of commands that allows for no error. If error occurs, it ends right there.

1. acpidump > acpidump.txt - output of acpidump command ends in acpidump.txt file
2. acpixtract acpidump.txt - obvious, acpiextract (whatever it is) uses acpidump.txt as a parameter
3. iasl -d DSDT.dat - again, **iasl --help** to see what -d does: Disassemble or decode binary ACPI table to file (*.dsl)

---

