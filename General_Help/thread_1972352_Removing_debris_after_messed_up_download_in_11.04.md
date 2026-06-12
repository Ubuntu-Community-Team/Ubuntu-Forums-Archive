---
title: "Removing debris after messed up download in 11.04"
date: 2012-05-03
forum: General Help
---

### Post by grey1beard on 2012-05-03
I have messed up a download of Phasex/Jack/Virtual Keyboard onto my 64 bit Desktop running 11.04.

As removing/re-installing it still doesn't work, I assume that there is something of the original download interfering.

How do I go about finding out if this is true, or not, and then cleaning up ?

Many thanks
John

---

### Post by raja.genupula on 2012-05-03
could you provide us the terminal code about the error , we will try our best to help you .:)

---

### Post by grey1beard on 2012-05-03
Thanks raja.genupula for posting.

> **grey1beard said:**
> .....How do I go about finding out if this is true, or not, and then cleaning up ?....
> ...could you provide us the terminal code about the error ...
Could you indicate what sort of instruction to enter into terminal to give you the necessary information ?

Additional info -

I thought I had installed Phasex successfully, but if I open Jack, then Phasex, no Phasex GUI appears, and the entry of Phasex in the Jack window is only momentarily visible.
From this I concluded that something was amiss, so I removed it all, and tried again, but with no success.

---

### Post by raja.genupula on 2012-05-03
As you said uninstalling/Removing apps the terminal code 
```
sudo apt-get remove <App_name>
```

so just try to do that in your terminal and post them here .
then after that , you said some application not launching properly so in your terminal do this 
 ```
gksu <app_name>
```
and post the errors here .

All the best :)

---

### Post by grey1beard on 2012-05-03
After trying to remove Phasex using "PHASEX", as per name in Applications, and getting "Unable to locate package", I tried again using "phasex", and this time it proceeded.

> john@dragon:~$ sudo apt-get remove phasex
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  phasex
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 983kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 329605 files and directories currently installed.)
Removing phasex ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for python-support ...
john@dragon:~$ 

As I am unfamiliar with gksu, I assume I need to install Phasex again before I run it ?
Should I use Software Centre, or Synaptic, or apt-get install ?
(I've never understood the difference or advantages in one route or another).

John

---

### Post by Darkness Des on 2012-05-03
The Software Center, Synaptic and apt-get install are all the same thing, it's just how easy it looks to the end-user. For example:
The software center is friendly and has icons and helpful descriptions, very little tech specs.
Synaptic has more tech specs but is still graphically displayed and easily searchable.
Apt-get is command line only, takes a bit more knowledge to use, and is not very easily searchable to someone that is unfamiliar with it (the command is "apt-cache search <package name>"), and takes a little more effort to use.

---

### Post by grey1beard on 2012-05-03
Thanks Des, "apt-cache search" - another bit on the learning curve ;)

John

---

### Post by grey1beard on 2012-05-03
Installed phasex via synaptic.
Started Jack, then ran gksu phasex in terminal.
No GUI appeared, and in terminal it said - 

> jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory

even though the Jack window is on the desktop !

Then I tried again, but this time started Jack, then switched on my midi keyboard, then launched phasex, and this time a phasex gui appears !!!

So I think your advice to use terminal to remove phasex must have cleaned it up properly, and now it seems I can make some progress.

I'll mark this thread as solved, and continue to pursue my midi problem separately.
Thank you Raja

---

