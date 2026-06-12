---
title: "Using secure-delete"
date: 2011-02-05
forum: General Help
---

### Post by Total Noob on 2011-02-05
I downloaded "secure-delete" from the Ubuntu Software Center, but it doesn't have any instructions, there is no website, and it does not appear in the Apps tab. I can't even begin to begin using it.

How do I get this going? I haven't the faintest idea how to use the terminal programs. Zilch.

Thanks.

---

### Post by Frogs Hair on 2011-02-05
I guessing this is a terminal based application and as you may know there is no website or information . Try typing the application name in the terminal . Running this application may require  a sudo command . The fact that there is no information  about how to use it   would keep me away if were a new user or had no terminal experience .

If you want a cleaning app check out BleachBit and If want data recovery look at backup options that include some documentation and a website .

---

### Post by Total Noob on 2011-02-05
> **Frogs Hair said:**
> I guessing this is a terminal based application and as you may know there is no website or information . Try typing the application name in the terminal . Running this application may require  a sudo command . The fact that there is no information  about how to use it   would keep me away if were a new user or had no terminal experience .

If you want a cleaning app check out BleachBit and If want data recovery look at backup options that include some documentation and a website .

Fair enough, and that's what I did.

But it would be nice if the repository had all the info that a noob needs to get an app going and if apps all plugged into the apps list, even those that have to be run from a terminal (something I'm loathe to do).

---

### Post by Habitual on 2011-02-05
```
man shred
```

Stick this in your ~/.bashrc
```
alias shred='shred -u -n 5'
```

Then reload bashrc with
```
reload='source ~/.bashrc'
```

Usage:
```
shred filename
```

**Wiped with Zeros Five times then deleted.**

HTH

---

### Post by Andrew.Z on 2011-02-05
Recent versions of [BleachBit include a file shredder](http://bleachbit.sourceforge.net/) which has an easy-to-use GUI (great for noobs) for shredding arbitrary files (just like shred in secure-delete).  

IIRC, BleachBit 0.8.0 in Ubuntu 10.10 is too old for this feature (at least for shredding whole folders), so do this

[LIST=1]
[*]Download the latest BleachBit (currently 0.8.7) from its web site
[*]Install it by following the prompts
[*]Start it from the menu
[*]Click **File - Shred Files** or **File - Shred Folders**
[/LIST]

---

### Post by oldos2er on 2011-02-05
> **Total Noob said:**
> But it would be nice if the repository had all the info that a noob needs to get an app going and if apps all plugged into the apps list, even those that have to be run from a terminal (something I'm loathe to do).

Synaptic Package Manager and aptitude and apt-get all can show you descriptions of packages, including all the files a given package contains and where they are installed. Synaptic is probably the easiest of the three to use for someone new to Ubuntu.

If every CLI app were to have a menu entry, your menus would be so big they would be unuseable.

---

### Post by Total Noob on 2011-02-09
> **Andrew.Z said:**
> Recent versions of [BleachBit include a file shredder](http://bleachbit.sourceforge.net/) which has an easy-to-use GUI (great for noobs) for shredding arbitrary files (just like shred in secure-delete).  

IIRC, BleachBit 0.8.0 in Ubuntu 10.10 is too old for this feature (at least for shredding whole folders), so do this

[LIST=1]
[*]Download the latest BleachBit (currently 0.8.7) from its web site
[*]Install it by following the prompts
[*]Start it from the menu
[*]Click **File - Shred Files** or **File - Shred Folders**
[/LIST]

Thanks. I did use BleachBit after finding it in my Ubuntu repository, but "about" was for some reason disabled, so I don't know what version it is.

In all candor and by way of constructive criticism, I found the BleachBit version I have OK to use, but the GUI and the functionality of Ccleaner is terrific and should be aimed for.

---

### Post by scarey9 on 2011-02-09
I use the secure delete package.
```
sudo apt-get install secure-delete
```You can delete a file by  it's self by using the srm command or you can remove an entire directory  and sub-directories by using recursive mode. 

for single file (i like to use verbose mode to see what it is doing with the -v option
```
srm -v (path)filename
```for an entire directory and  subdirectory use recursive mode (also with verbose option so i can see  that it is happening but that is prefrence)
```
srm -rv (path to directory)
```use man to find out more on  other options ***warning it can take a while to do lots of files**** it  writes over each file 38 times bit by bit.

link to some more info about this topic [http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html](http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html)

---

### Post by dennisonIT on 2011-06-04
It would be great if someone could write down in newbie language for (ubuntu/linux fans like me who are still learning their way) on how to add secure-delete and or shred into the latest version of nautilus actions configuration (3.05) as my old shred command didn't upgrade from 10.10 to 11.04 (lots of people have had this problem-no answers yet-  other than to purge the latest version and go back to v2.30). The latest version seems to have lots of options that could be left to an advanced option leaving the simple version for basic users. I wonder if this was a case of development for developments sake or that the latest version shouldn't have been included with Natty but as an option for those users that needed it

---

