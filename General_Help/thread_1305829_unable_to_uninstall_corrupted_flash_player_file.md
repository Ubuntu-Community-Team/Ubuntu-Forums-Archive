---
title: "unable to uninstall corrupted flash player file"
date: 2009-10-30
forum: General Help
---

### Post by Chrono Reaper on 2009-10-30
I have tried fixing the broken package through recovery mode, tried going in synaptic package manager and even tried reinstalling firefox. I have exhausted every option and it wont uninstall flash. 

Then I get a window that pops up:

> E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


also trying to uninstall Firefox 3.0 since I now have 3.5 but i get this message as well: 

> Package Operation Failed

The installation or removal of a software package failed.

E:I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.: 

---

### Post by Primefalcon on 2009-10-30
> **Chrono Reaper said:**
> I have tried fixing the broken package through recovery mode, tried going in synaptic package manager and even tried reinstalling firefox. I have exhausted every option and it wont uninstall flash. 

Then I get a window that pops up:



also trying to uninstall Firefox 3.0 since I now have 3.5 but i get this message as well:
try it throguh apt with

```
sudo apt-get remove adobe-flashplugin
```

also try

sudo apt-get install -f


then try reinstalling flash and you shouldn't have any issues, it worked for me when I had the same issue

---

### Post by Chrono Reaper on 2009-10-30
> **Primefalcon said:**
> try it throguh apt with

```
sudo apt-get remove adobe-flashplugin
```

```
chronoreaper@chronoreaper-laptop:~$ sudo apt-get remove adobe-flashplugin
[sudo] password for chronoreaper: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
chronoreaper@chronoreaper-laptop:~$ 

```

---

### Post by Primefalcon on 2009-10-30
> **Chrono Reaper said:**
> ```
chronoreaper@chronoreaper-laptop:~$ sudo apt-get remove adobe-flashplugin
[sudo] password for chronoreaper: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
chronoreaper@chronoreaper-laptop:~$ 

```
try sudo apt-get install -f

---

### Post by Chrono Reaper on 2009-10-30
ill give it a try...

---

### Post by nothingspecial on 2009-10-30
nevermind

---

### Post by phillw on 2009-10-30
Hi,

```
dpkg --list | grep flash
```

Will list what is there.

make a note of it & head over to here .....

[http://ubuntuforums.org/showthread.php?t=274844](http://ubuntuforums.org/showthread.php?t=274844)

As it says, you shouldn't need to do this - but, hey, every now and again summat is bound to goof up, somewhere for someone - It picked you  this time :p

That should clear your flash problem up.

Regards,

Phill.

---

### Post by Chrono Reaper on 2009-10-30
> **Primefalcon said:**
> try sudo apt-get install -f

```
chronoreaper@chronoreaper-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

```

> 
Code:

dpkg --list | grep flash

Will list what is there.

make a note of it & head over to here .....

[http://ubuntuforums.org/showthread.php?t=274844](http://ubuntuforums.org/showthread.php?t=274844)

As it says, you shouldn't need to do this - but, hey, every now and again summat is bound to goof up, somewhere for someone - It picked you this time

That should clear your flash problem up.

Regards,

Phill. 

```
chronoreaper@chronoreaper-laptop:~$ dpkg --list | grep flash
rFR adobe-flashplugin                          10.0.32.18-1                               Adobe Flash Player plugin version 10

```

This is getting irritating...

---

### Post by Primefalcon on 2009-10-30
> **Chrono Reaper said:**
> ```
chronoreaper@chronoreaper-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

```



```
chronoreaper@chronoreaper-laptop:~$ dpkg --list | grep flash
rFR adobe-flashplugin                          10.0.32.18-1                               Adobe Flash Player plugin version 10

```

This is getting irritating...
as phill mentioned try

```
sudo dpkg --force-all -r adobe-flashplugin
```

then do

```
sudo apt-get install adobe-flashplugin
```

edit, sorry corrected

---

### Post by Chrono Reaper on 2009-10-30
> **Primefalcon said:**
> as phill mentioned try

```
sudo dpkg --force-all -r /var/cache/apt/archives/adobe-flashplugin
```

then do

```
sudo apt-get install adobe-flashplugin
```

```
chronoreaper@chronoreaper-laptop:~$ sudo dpkg --force-all -r /var/cache/apt/archives/adobe-flashplugin
[sudo] password for chronoreaper: 
dpkg: warning: ignoring request to remove /var/cache/apt/archives/adobe-flashplugin which isn't installed.
chronoreaper@chronoreaper-laptop:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
```

also got this when i opened up the synaptic package manager:

> The package 'adobe-flashplugin' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.

---

### Post by phillw on 2009-10-30
> **Chrono Reaper said:**
> ```
chronoreaper@chronoreaper-laptop:~$ sudo dpkg --force-all -r /var/cache/apt/archives/adobe-flashplugin
[sudo] password for chronoreaper: 
dpkg: warning: ignoring request to remove /var/cache/apt/archives/adobe-flashplugin which isn't installed.
chronoreaper@chronoreaper-laptop:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
```also got this when i opened up the synaptic package manager:


okay... the hint is in the message ....   "ignoring request to remove..." which isn't installed...

let's try this on it ....

```
 ~$ sudo apt-get --purge autoremove adobe-flashplugin
```

Phill.

---

### Post by Primefalcon on 2009-10-30
lets see if it its in the archives

```
ls /var/cache/apt/archives/ | grep adobe-flash
```

try what phill said first

---

### Post by Chrono Reaper on 2009-10-30
> **phillw said:**
> okay... the hint is in the message ....   "ignoring request to remove..." which isn't installed...

let's try this on it ....

```
 ~$ sudo apt-get --purge autoremove adobe-flashplugin
```

Phill.

```
chronoreaper@chronoreaper-laptop:~$ sudo apt-get --purge autoremove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
chronoreaper@chronoreaper-laptop:~$ 

```

EDIT: I am locked out from getting any update or unable to access the synaptic Package manager

---

### Post by wojox on 2009-10-30
```
sudo apt-get --reinstall install adobe-flashplugin
```

---

### Post by Chrono Reaper on 2009-10-30
> **wojox said:**
> ```
sudo apt-get --reinstall install adobe-flashplugin
```

```
chronoreaper@chronoreaper-laptop:~$ sudo apt-get --reinstall install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
chronoreaper@chronoreaper-laptop:~$ 

```


also tried to attempt removing firefox 3.5 and 3.0 through add/remove but still locked out with the following message: 

> E:I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.: 

---

### Post by phillw on 2009-10-30
> **Chrono Reaper said:**
> ```
chronoreaper@chronoreaper-laptop:~$ sudo apt-get --reinstall install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
chronoreaper@chronoreaper-laptop:~$ 

```also tried to attempt removing firefox 3.5 and 3.0 through add/remove but still locked out with the following message:


::SIGH:: ....... do the purge in sudo again, then head over to here to clear your database of the package....

[http://ubuntuforums.org/archive/index.php/t-540286.html](http://ubuntuforums.org/archive/index.php/t-540286.html)

Looks like your dbase is corrupted ..

Regards,

Phill.

---

### Post by Chrono Reaper on 2009-10-30
i went there but I cant figure out the sudo commands to put in the terminal that would work,

---

### Post by phillw on 2009-10-30
> **Chrono Reaper said:**
> i went there but I cant figure out the sudo commands to put in the terminal that would work,


Give me a cple of minutes ...

---

### Post by Chrono Reaper on 2009-10-30
okay...I would like to do this without reinstalling Ubuntu. got 9.10 through updating with 9.04. I thought that firefox 3.0 would have been replaced with 3.5 like the last few upgrades.

---

### Post by phillw on 2009-10-30
> **Chrono Reaper said:**
> i went there but I cant figure out the sudo commands to put in the terminal that would work,


1) cd /var/lib/dpkg
2) sudo cp available available.bad
3) sudo cp status status.bad
4a) gksudo gedit available 
4b) remove all references to adobe-flashplugin Save/close.
5a) gksudo gedit status 
5b) remove all references to adobe-flasplugin. Save/close.
6) cd info
7) sudo rm all files relating to adobe-flashplugin.


That should clear the little B* out of your system.

---

### Post by Chrono Reaper on 2009-10-30
> **phillw said:**
> 1) cd /var/lib/dpkg
2) sudo cp available available.bad
3) sudo cp status status.bad
4a) gksudo gedit available 
4b) remove all references to adobe-flashplugin Save/close.
5a) gksudo gedit status 
5b) remove all references to adobe-flasplugin. Save/close.
6) cd info
7) sudo rm all files relating to adobe-flashplugin.


That should clear the little B* out of your system.

Do i copy and paste that word for word in the Terminal?

---

### Post by phillw on 2009-10-30
and wait before you do anything to firefox !!!!

---

### Post by phillw on 2009-10-30
> **Chrono Reaper said:**
> Do i copy and paste that word for word in the Terminal?

No ...

```

cd /var/lib/dpkg
sudo cp available available.bad
sudo cp status status.bad
gksudo gedit available 

```Copy and paste that, then ...

4b) remove all references to adobe-flashplugin Save/close.

Use the Search Find for the word adobe until you get a block like this ....

> Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from the net.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can
 use the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.
 .
 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from [www.adobe.com]("http://www.adobe.com").  The distribution license of the Adobe flash
 plugin is available at [www.adobe.com]("http://www.adobe.com").  Installing this Ubuntu package implies
 that you have accepted the terms of that license.
Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Description: Adobe Flash SWF Player ([http://www.adobe.com](http://www.adobe.com))
Npp-File: libflashplayer.so
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Original-Maintainer: Bart Martens <bartm@knars.be>
Delete it.

Then ..

```
gksudo gedit status 
```
5b) remove all references to adobe-flasplugin. Save/close.

Do the same as above - looking for the same thing.

Then ..

```
cd info
```Then..

```
sudo rm -r adobe-flashplugin
```Now, I didn't find anything on my system in /var/lib/info  - so don't be worried if you don't !!


/edit Hmmm... I issued a sudo rm -r command - these are not good. PLEASE BE REALLY CAREFUL.


Phill.

---

### Post by Chrono Reaper on 2009-10-30
> **phillw said:**
> No ...

```

cd /var/lib/dpkg
sudo cp available available.bad
sudo cp status status.bad
gksudo gedit available 

```

Copy and paste that, then ...

4b) remove all references to adobe-flashplugin Save/close.

Use the Search Find for the word adobe until you get a block like this ....



Delete it.

Then ..

```
gksudo gedit status 
```


5b) remove all references to adobe-flasplugin. Save/close.

Do the same as above - looking for the same thing.

Then ..

```
cd info
```

Then..

```
sudo rm -r adobe-flashplugin
```

Now, I didn't find anything on my system in /var/lib/info  - so don't be worried if you don't !!

Phill.

fixed...

Thanks for all your help and patience in taking care of this error. I'll make sure to book mark this for now on if any other problems like this occur.

---

### Post by phillw on 2009-10-30
> **Chrono Reaper said:**
> fixed...

Thanks for all your help and patience in taking care of this error. I'll make sure to book mark this for now on if any other problems like this occur.


PHEW !!! Thank heaven for that - I was out of ideas if that didn't work !!!

For general FFox stuff, lovinglinux keeps an excellent area at ....

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

I plug it, coz it makes him blush :D

You're welcome to the help, glad to have it sorted !!!

Phill.

---

### Post by Chrono Reaper on 2009-10-30
now if I can only enjoy getting my other Toshiba computer to use its Atheros WiFi card on 9.10 I'll rest easy this holiday...:popcorn:

---

### Post by phillw on 2009-10-30
> **Chrono Reaper said:**
> now if I can only enjoy getting my other Toshiba computer to use its Atheros WiFi card on 9.10 I'll rest easy this holiday...:popcorn:


<<<< RUNS AWAY .... LOL

Please edit your 1st posting in this thread and mark it solved - it helps everyone else :D

Phill.

---

### Post by vijaybilgoji on 2009-10-31
Fixed the problem for me

sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg-reconfigure adobe-flashplugin --force
sudo dpkg --purge --force-all adobe-flashplugin

---

### Post by razaz03 on 2009-11-10
> **phillw said:**
> No ...

```

cd /var/lib/dpkg
sudo cp available available.bad
sudo cp status status.bad
gksudo gedit available 

```Copy and paste that, then ...

4b) remove all references to adobe-flashplugin Save/close.

Use the Search Find for the word adobe until you get a block like this ....

Delete it.

Then ..

```
gksudo gedit status 
```5b) remove all references to adobe-flasplugin. Save/close.

Do the same as above - looking for the same thing.

Then ..

```
cd info
```Then..

```
sudo rm -r adobe-flashplugin
```Now, I didn't find anything on my system in /var/lib/info  - so don't be worried if you don't !!


/edit Hmmm... I issued a sudo rm -r command - these are not good. PLEASE BE REALLY CAREFUL.


Phill.


Bravo! Been on this for an hour now since the upgrade (didn't even try to download flash it just auto-corrupted since the upgrade from jaunty) and you've solved it.

Much obliged,

razaz03

---

### Post by phillw on 2010-01-06
Hi, to > Worlds00ps

Can you post here what you have tried, there are a couple of solutions available & also what was reported back as you did things.

Regards,

Phill.

---

### Post by mac9416 on 2010-01-24
> E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report. 

That error is easily solved by enabling the partner repos. Go to System > Administration > Software Sources > Other Software and enable 'http://archive.canonical.com/ karmic partner'.

---

