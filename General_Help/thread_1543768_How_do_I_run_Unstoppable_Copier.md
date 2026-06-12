---
title: "How do I run Unstoppable Copier?"
date: 2010-08-01
forum: General Help
---

### Post by xile102 on 2010-08-01
Hi im new to linux. I just want to transfer all my files that i backed up onto my Ipod and i wanted to use a great program called Unstoppable copier that is availalble on both windows and linux.  

Ok here is my problem. i downloaded the linux x86 version of unstoppable copier, can be found here: 
[http://www.roadkil.net/program.php/P29/Unstoppable%20Copier](http://www.roadkil.net/program.php/P29/Unstoppable%20Copier)

it gives me a file called unstopcp.gz.  So okay im pretty sure this is a compressed file so i extracted it.  now i am left with a file called unstopcp and in the properties it says 'executable (application/x-executable)'.

my question is how do i run it? already tried double clicking on it, alt+f2 (run), and in terminal done './unstopcp'.  These methods i found when i tried searching on the internet but they dont work.  I get the error "Could not display "/home/xxx/Downloads/unstopcp".
"There is no application installed for executable files"


ty very much for ur help.

---

### Post by xile102 on 2010-08-05
Hey guys im back and with a solution to my own question!  I tried many different things but none of them worked as there was no help on the internet for this program! but then i used the terminal again and it told me i needed a library. So here we go, this is a guide to running unstoppable copier on linux.

[edit] oops i forgot to mention, add those commands in Terminal.   :P

To run Unstoppable Copier in linux:

1. download and install library:
**sudo apt-get install libqt3-mt**

2. copy unstopcp to /usr/bin/
**sudo cp unstopcp /usr/bin/**

3. run it independently from terminal
**unstopcp&**

or making a shortcut from Edit Menus is prolly better to use to run the program.

right click on Applications on the top bar and click Edit Menus.
make sure u type **/usr/bin/unstopcp** in the command bit when u make a new shortcut.

---

### Post by MeanderingCode on 2010-12-16
I thought I'd bump this thread for containment purposes, rather than create another place for users to find.

I'm on Kubuntu 10.10 64bit with libqt3-mt (and everything that matches libqt3-mt*) installed, /usr/lib/libqt-mt.so.3 is a symbolic link to /usr/lib/lib-qt.so.3.3.8 (which exists), /usr/share/qt3/lib/libqt-mt.so.3 is a symbolic link pointing to the same, and I even linked to it from /lib/libqt-mt.so.3 .

I still get the following
```
user@host:$ unstopcp 
unstopcp: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
```

I even tried the 32bit version (as I originally used the 64bit for my system).

I'm not sure where it's looking. I'm also posting on an older thread with what appears to be the author (or at least linux author):
[http://www.roadkil.net/forums/forums.php?ID=481]("http://www.roadkil.net/forums/forums.php?ID=481")

Thank you to anyone with info or pointers.

---

### Post by astroboy123 on 2011-06-07
> **MeanderingCode said:**
> I thought I'd bump this thread for containment purposes, rather than create another place for users to find.

I'm on Kubuntu 10.10 64bit with libqt3-mt (and everything that matches libqt3-mt*) installed, /usr/lib/libqt-mt.so.3 is a symbolic link to /usr/lib/lib-qt.so.3.3.8 (which exists), /usr/share/qt3/lib/libqt-mt.so.3 is a symbolic link pointing to the same, and I even linked to it from /lib/libqt-mt.so.3 .

I still get the following
```
user@host:$ unstopcp 
unstopcp: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
```

I even tried the 32bit version (as I originally used the 64bit for my system).

I'm not sure where it's looking. I'm also posting on an older thread with what appears to be the author (or at least linux author):
[http://www.roadkil.net/forums/forums.php?ID=481]("http://www.roadkil.net/forums/forums.php?ID=481")

Thank you to anyone with info or pointers.

I having the same issue.

---

### Post by blueridgedog on 2011-06-07
Are you running 64 or 32 bit Linux?

---

### Post by miasmablk on 2011-06-07
This might sound stupid but did you try right clicking on the file and going to 

  properties ----> permissions ----> allow executing file as a program ?

---

