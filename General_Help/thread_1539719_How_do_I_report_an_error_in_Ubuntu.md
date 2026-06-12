---
title: "How do I report an error in Ubuntu?"
date: 2010-07-26
forum: General Help
---

### Post by sleepee on 2010-07-26
Well, it's not a real bug/error in Ubuntu per se, but i found an error in the spanish language pack of Ubuntu.  There were some words that weren't translated right.
I was wondering how to report/change that.
I actually found it in the Ubuntu 9.10 spanish language pack, so i don't know if it's been fixed for lucid, but i thought it would be good to know either way just in case i find some other translation errors.

---

### Post by MaxIBoy on 2010-07-26
Find out the name of the package which included the program, then run this command:
```
sudo apt-get install reportbug
reportbug name_of_package
```

---

### Post by sleepee on 2010-07-26
> **MaxIBoy said:**
> Find out the name of the package which included the program, then run this command:
```
sudo apt-get install reportbug
reportbug name_of_package
```

to be honest, i'm not sure which package it is.
when i installed the spanish language pack, it installed a few packages together.  i assume it's the language-pack-es-base, but i don't really know.
it also installed language-pack-es, language-pack-es-base, language-pack-gnome-es, and a whole bunch of other packages.  how do i find out which one is the one with the actual translation error?

---

### Post by sleepee on 2010-07-26
by the way, i tried reportbug anyway and i got an error.

```
sleepee@sleepee-laptop:~$ reportbug language-pack-gnome-es
*** ERROR: "Ubuntu" BTS is currently unsupported. Please use "ubuntu-bug" (from the apport package) for reporting bugs in Ubuntu. You can report bugs to Debian by specifying 'bts debian' in your
~/.reportbugrc or by passing the -B debian option on the commandline (see reportbug(1)).
```

i'm going to try the "ubuntu-bug" command next.

---

### Post by wojox on 2010-07-26
Try Alt+F2 and type 

```
apport-bug
```

---

### Post by MaxIBoy on 2010-07-26
You can figure out the package with this procedure. (This is the longest and most complicated way to do it, but also the most fool-proof and accurate.) I'll walk you through it using the calculator program as an example. 

First, pull up a terminal and type "cat" followed by a space, but do not hit enter. Drag-and-drop the icon to launch the program in question into the terminal window, then type "| grep Exec" and *then* hit enter. When I did this for the calculator, I got this:
```
maxtothemax@maxtothemax-mint ~ $ cat '/usr/share/applications/gcalctool.desktop' | grep Exec
Exec=gcalctool
maxtothemax@maxtothemax-mint ~ $ 
```This is to find out what the actual command for the program is. 

From there, type in "whereis -b <command>" and hit enter. For example:
```
maxtothemax@maxtothemax-mint ~ $ whereis -b gcalctool
gcalctool: /usr/bin/gcalctool /usr/share/gcalctool
maxtothemax@maxtothemax-mint ~ $ 
```This is to figure out where the executable file is. (If multiple files are listed, use the file browser to check-- in this example, one of them is an actual executable file and the other is just a folder.)

Finally, to get the name of the package:
```
maxtothemax@maxtothemax-mint ~ $ dpkg -S /usr/bin/gcalctool
gcalctool: /usr/bin/gcalctool
maxtothemax@maxtothemax-mint ~ $ 
```So we can see that the package is named "gcalctool" in this case.

---

### Post by sleepee on 2010-07-27
thanks for the advice, but i found out how to report translation bugs through the wikis.  it's kind of a longer process than i thought it was going to be, but i have to give back to the community somehow.  you've all helped me out a lot.
anyway, here's the wikis, just in case anybody else comes to this thread looking to report translation bugs like me.

[https://wiki.ubuntu.com/Translations/KnowledgeBase/ReportingBugs](https://wiki.ubuntu.com/Translations/KnowledgeBase/ReportingBugs)
[https://wiki.ubuntu.com/Translations/KnowledgeBase/HandlingBugs](https://wiki.ubuntu.com/Translations/KnowledgeBase/HandlingBugs)
[https://wiki.ubuntu.com/Translations/TranslationLifecycle](https://wiki.ubuntu.com/Translations/TranslationLifecycle)

---

