---
title: "Adept: Another process using packaging system... But which?"
date: 2006-05-01
forum: General Help
---

### Post by Gijith on 2006-05-01
Hello,

Whenever I try to open Adept, I get:

You will not be able to change your system settings in any way because another process is using the packaging system. Please close the other application before using this one.

The apps it suggests might be causing the program (another Adept, apt-get, aptitude) are all off, according to Ksysguard. I'm not sure what caused the start of this error, but I can't figure out which program is causing it. Any clues would be very appreciated. Thanks.

---

### Post by Al3xanR0 on 2006-05-02
[QUOTE=Gijith]Hello,

Whenever I try to open Adept, I get:

You will not be able to change your system settings in any way because another process is using the packaging system. Please close the other application before using this one.

The apps it suggests might be causing the program (another Adept, apt-get, aptitude) are all off, according to Ksysguard. I'm not sure what caused the start of this error, but I can't figure out which program is causing it. Any clues would be very appreciated. Thanks.[/QUOTE]

The only thing I can think of is either you were in the middle of an ```
apt-get update
``` when you tried to use Adept or Synaptic is running.

---

### Post by fmo on 2006-05-02
Maybe you could try to use lsof to list open files

```
lsof |grep -i apt
```

```
lsof |grep -i adept
```

or maybe have a look at

```
/var/lib/apt/lists/lock
```

to check if maybe your package manager crashed and left the lock on the package database

---

### Post by freakout2 on 2007-06-29
my adept gave the same error after it crashed during a full upgrade. i restarted the computer but kept getting the same error as you guys. So what i did to fix it was boot into terminal. Typed
#sudo apt-get#
the computer promted me to run 
#dpkg --cnfigure a#
 so i did . and that was that it was back on line. if this works for you please confirm it  . and if not say it doesn't we don't want any one else wasteing there time

---

### Post by kansei on 2007-06-30
That didn't seem to work for me, but I didn't 'boot into terminal' to issue the commands, just issued them at a virtual terminal.

What worked for me was to run apt-get install [name of some package you want], then it seems to have processed the entire list of packages I was originally attempting to install with adept. I did 'apt-get install pidgin' and it also installed firefox, j2re, etc.

After that finished, I ran adept and it was happy again.

---

### Post by andi763 on 2007-08-01
I did
$ sudo apt-get check
the computer promted me to run
$sudo dpkg --configure -a

The interrupted update was finishing and all was back to normal.

---

### Post by JeevesBond on 2007-09-17
This may be an old thread, but it's still a good one. I had Adept Manager crash in the middle of an update, then it displayed the message shown in the OP every time I tried to open it. I expected it to use a pid file or something similar in /var/run so was quite suprised to find the lock file hidden away at /var/lib/apt/lists/lock !

Thanks for posting those solutions everyone, particularly fmo. :)

---

### Post by Greetings from mirth on 2007-10-12
I had to delete this file
/var/lib/apt/lists/lock
then sudo apt-get check
the computer then said to run dpkg --configure -a
so I sudo'd that.
It did a few "setting up..." one was java, and a few others

then add/remove programs worked again
[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)
:guitar:

---

