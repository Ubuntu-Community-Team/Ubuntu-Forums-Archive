---
title: "Need help with Play on Linux: is there a &quot;trust apps&quot; in Ubuntu?"
date: 2010-12-03
forum: General Help
---

### Post by 0949er on 2010-12-03
I have run into some problem trying to install starcraft II on my ubuntu system using "play on linux". I have contacted their technical support and they have suggested it is because "PlayOnLinux" is not in my "trusted apps" catagory. Does this mean anything to anybody? Does ubuntu have a trusted apps catagory? If so, how do I add POL to it? 

Furthermore, has anybody gotten any game to work with playonlinux and ubuntu?

```

swooshonln@power-house:~$ playonlinux
PlayOnLinux v3.8.6

touch: cannot touch `/home/swooshonln/.PlayOnLinux/configurations/last_string': Permission denied
Checking plugin: Advanced Wine Configuration...
Checking plugin: Offline PlayOnLinux...
Checking plugin: Capture...
Checking plugin: Transgaming Cedega...
Checking plugin: Wine Import...
Checking plugin: Wine Look...
Checking plugin: Detour...
Xlib:  extension "RANDR" missing on display ":0.0".
Running install menu
Xlib:  extension "RANDR" missing on display ":0.0".
/home/swooshonln/.PlayOnLinux/install: line 46: cd: /home/swooshonln/.PlayOnLinux/tmp/*.jpg: No such file or directory
--2010-12-03 15:18:58--  http://mulx.playonlinux.com/wine/linux-i386/LIST
Resolving mulx.playonlinux.com... 91.121.5.64
Connecting to mulx.playonlinux.com|91.121.5.64|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10010 (9.8K) [text/plain]
Saving to: `STDOUT'

100%[======================================>] 10,010      41.0K/s   in 0.2s    

2010-12-03 15:18:59 (41.0 KB/s) - written to stdout [10010/10010]

```

---

### Post by ean5533 on 2010-12-03
As far as I know there is no "trusted" setting of any kind in Ubuntu. "Trusted" is a Windows thing, and there is no equivalent in the Linux world (again, as far as I know).

I got SC2 to install fine just by running the normal installer through Wine. I never needed PlayOnLinux. Are you running the installer from the DVD? What is going wrong?

---

### Post by WorMzy on 2010-12-03
POL is basically just a front-end to wine, so see if the AppDB has any hints or tips regarding the problem you're having: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882)

As far as I'm concerned, a trusted app is one that you've installed.

---

### Post by 0949er on 2010-12-03
I guess I am trying to eventually run the installer off the DVD with PlayOnLinux, however I cannot get that far into the process. (Due to a error with Playonlinux)

How did you get wine to run the installer? What do I need to installed in the software center to just "run" it? What kind of configuring do I need to do? The only thing "wine" related I have installed as of right now is "play on linux"



The trusted apps thing came from the admin of the Play On linux forum. He might just be guessing, I will link you guys to that thread as well, It is only a few posts:

[http://www.playonlinux.com/en/topic-4038.html](http://www.playonlinux.com/en/topic-4038.html)


if anybody has any other ideas to make this work... I am all ears.

---

### Post by ean5533 on 2010-12-03
I just used plain ol' Wine.

It's been a while since I installed it, so I can't remember what version of Wine I was using. It was either the version of Wine that's in the maverick (Ubuntu 10.10) repositories, or it was the latest development version. You can try it both ways and see which one works. You can install the version from maverick's repositories by running:

> sudo apt-get install wine

If that doesn't work, you can install the latest development version by adding the Wine PPA and then installing:

> sudo apt-add-repository ppa:ubuntu-wine/ppa && sudo apt-get update && sudo apt-get install wine

Once that's done, just put the SC2 DVD in, browse the files on it, and then launch the Autorun.exe file. It should be opened by Wine automatically, and the installer should "just work". It did for me, anyway.

If you have any problems, I highly suggest clicking on the link WorMzy provided. The info there is all from guys just like you and me who give their solutions to problems they ran into.

---

### Post by 0949er on 2010-12-03
real quick, here is what is going on when I right click on Installer.exe on the SC dvd:

*side not*
while navigating the DVD, it doesnt seem like it really see's any files... I mean I see installer.exe and a folder that has a few files in it, but I dont see any core files or anything.

[IMG]http://img690.imageshack.us/img690/5747/screenshotl0.png[/IMG]

---

### Post by ean5533 on 2010-12-03
Ah! You know what, I do remember I had that same problem, where not all files are showing up on the DVD. I completely forgot about it.  I also remember I **definitely** found the answer to that problem on the Wine AppDB forums (the link from earlier). Unfortunately I have to get back to work, but let me know if you can't find a solution and I'll take a look tonight or tomorrow.

---

### Post by endotherm on 2010-12-03
sorry for jumpin in late. in your original playonlinux error, does this file already exist?
```
`/home/swooshonln/.PlayOnLinux/configurations/last_string' 
```? if so, destroy it and try again. if you get the same error again, check the permisions on ~/.PlayOnLinux/configurations/ to make sure you have RWX.

---

### Post by 0949er on 2010-12-03
> **ean5533 said:**
> Ah! You know what, I do remember I had that same problem, where not all files are showing up on the DVD. I completely forgot about it.  I also remember I **definitely** found the answer to that problem on the Wine AppDB forums (the link from earlier). Unfortunately I have to get back to work, but let me know if you can't find a solution and I'll take a look tonight or tomorrow.

ok I am going to check it out now. I will update here if I cant find a solution. thanks for the help everybody.

---

### Post by 0949er on 2010-12-03
> **endotherm said:**
> sorry for jumpin in late. in your original playonlinux error, does this file already exist?
```
`/home/swooshonln/.PlayOnLinux/configurations/last_string' 
```? if so, destroy it and try again. if you get the same error again, check the permisions on ~/.PlayOnLinux/configurations/ to make sure you have RWX.

errr can you brush me up on my chmod skills?

---

### Post by 0949er on 2010-12-03
I changed permissions to 777 on everything in .PlayOnLinux directory (-R to follow all directories) and it still doesnt help

---

### Post by endotherm on 2010-12-03
> **0949er said:**
> errr can you brush me up on my chmod skills?
```
sudo chmod -R 770 ~/.PlayOnLinux

``` should do it.

no idea if that will solve all or some of your problems, but it should resolve the 'touch' error.

---

### Post by endotherm on 2010-12-03
> **0949er said:**
> I changed permissions to 777 on everything in .PlayOnLinux directory (-R to follow all directories) and it still doesnt help
same error message at the top, 
(can't touch file) or is it a new one?

---

### Post by 3Miro on 2010-12-03
Have you checked with the winehq database. I got SCII working with the instructions here.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882)

---

### Post by 0949er on 2010-12-03
> **3Miro said:**
> Have you checked with the winehq database. I got SCII working with the instructions here.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882)

thats exactly my problem I Think (as to installing with regular wine)

How do I do this under ubuntu? since it does all the mounting and unmounting automatically?

```

To successfully mount the DVD you have to use the "unhide" option.
 example: # mount -o ro,unhide,uid=1000 /dev/cdrom /mnt/cdrom
 If you are unable to install directly from the DVD, copy the files to a hard-disk first!

```

---

### Post by mc4man on 2010-12-03
first check on  what device, /dev links your drive is (if you only have 1 drive likely /dev/sr0 ), look in *-cdrom section
```
sudo lshw -C disk
```

then place dvd in drive, let the icon show up. In a terminal (assuming /dev/sr0, adjust if sr1 or sr2
```
umount /dev/sr0
```
The above shouldn't need sudo, if it does then add to command, the icon should disappear

Then 
```
sudo mkdir /media/fix
```
```
sudo mount -o ro,unhide,uid=100  /dev/sr0 /media/fix
```
The icon should reappear

When done with disk go 
sudo umount /dev/sr0

If further issues then may be a permission deal w/ playonlinux and .exe's - should be fixable

---

