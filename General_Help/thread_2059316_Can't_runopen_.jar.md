---
title: "Can't run/open .jar"
date: 2012-09-17
forum: General Help
---

### Post by ChaosChris2009 on 2012-09-17
I got this when attempting to open a .jar I need run/open

```
The file '/home/ubuntu/Updater_Rev1815_Shaeef1b09554227b85ab6fdfb9354a87bda2d5ef8086a2ecc3f365040d87fa4e35/Updater.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
```Help?

12.04

---

### Post by AndyOpie150 on 2012-09-17
Try right clicking on the .jar file and selecting properties, then select the permissions tab. Then check the Execute box.

Do you have Wine installed already?

---

### Post by Kirk Schnable on 2012-09-17
Ubuntu requires that files be marked as "executable" before they can be run.  This is a sensible security precaution and very easy to do.

You have two quick ways to do this off the top of my head...

1) In a terminal, run:
```
chmod +x /path/to/your/file.jar
```

2) As AndyOpie150 already mentioned, in the GUI, right click the file, hit Properties, and go to the Permissions tab.  There should be a checkbox there like "Make executable" or something, I don't remember the exact wording off the top of my head.

Then, it should work as you expect, assuming you have Java installed to run your jar.

Kirk

---

### Post by AndyOpie150 on 2012-09-18
The open java6 jdk and the open java7 jdk can both be downloaded from the software center, at least it is from mine.

---

### Post by gleedadswell on 2013-05-29
Hi everyone.  I generally have no trouble running .jar files on my system.  I either use

> java -jar program.jar

from the command line or I set the executable bit and run it by double click.  I always set openjdk as the default application for nautilus to use for .jar files so that I can just double click them.

But there is something about this that has always puzzled me.  You can run a .jar using java -jar from the command line whether you've set the executable bit on the .jar file or not.  Why is there a difference between running it from nautilus vs. from the command line?  I would have **thought** (apparently incorrectly) that if you've set openjdk as the default application then double clicking would start an instance of java -jar ...  But the different behaviour of command line vs. nautilus suggests that this is not what nautilus is doing.  So what is doing nautilus doing?

---

