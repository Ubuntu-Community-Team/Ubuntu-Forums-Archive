---
title: "problem setting .exe permissions"
date: 2010-05-21
forum: General Help
---

### Post by LibmasterLib on 2010-05-21
10.04 (Lucid Lynx)
I've been trying to run a .exe file under WINE and I've been having trouble changing the permissions under properties.  Whenever I try to check the "allow executing file as program" box under properties I get a message stating "The Permissions Could Not Be Changed," with "Sorry, could not change the permissions of "AutoRun.exe": Error setting permissions: Read-only file system" under it.

---

### Post by LowSky on 2010-05-21
you need root (sudo) access to change a file's permissions.

```
sudo nautilus
```

---

### Post by Chesamo on 2010-05-21
AutoRun.exe? Is it on a CD or something?

Besides, you don't want to execute the file. You want to run ```
wine start AutoRun.exe
```

You're opening the file in WINE, not executing it.

---

### Post by LibmasterLib on 2010-05-21
Thanks for the fast replies and all the help

@ LowSky
I put in that code and then went under the file my .exe is in and had no luck changing the permissions

@ Chesamo
It is on a CD
I tried putting in that code and got a message saying it couldn't find it.  I'm not used to using the terminal how do I direct it to the autorun on the CD I'm using

---

### Post by sydbat on 2010-05-21
Do you have wine configured to read from a CD? If not, go into Applications > Wine > Configure Wine and make sure you CD drive is listed under the Drives tab.

---

### Post by sydbat on 2010-05-21
> **LowSky said:**
> you need root (sudo) access to change a file's permissions.

```
**gksudo** nautilus
```Fix it for you.

---

### Post by Serpher on 2010-05-21
> **LibmasterLib said:**
> Thanks for the fast replies and all the help

@ LowSky
I put in that code and then went under the file my .exe is in and had no luck changing the permissions

UNIX file permissions are a part of the file system. The file system optical discs use aren't able to use these permissions. You can only read from a file on a disc technically anyway.

> **LibmasterLib said:**
> @ Chesamo
It is on a CD
I tried putting in that code and got a message saying it couldn't find it.  I'm not used to using the terminal how do I direct it to the autorun on the CD I'm using

You can do this one of two ways:

1) Right click on the .exe and select "Run in WINE"
2) Learn to use the 'cd' and 'ls' commands to navigate to your CD. It'll be located in something like '/media/cdrom/'. Just try typing cd before that directory and it'll probably work.

---

### Post by hoenybear on 2011-03-04
Hy guys. I am new to this forum.

I have a similar problem with "setting permissions". I am trying to install a 2 cd game in wine. I was succesful to do it in Mandriva but in Ubuntu, it says it cant open... like above posts. I also cannot mark file as executable...

I tried installing by terminal wine and drag setup but then when asks for second CD im totally blind... I had to quit install and delete the folder... why isnt Ubuntu easy??

---

### Post by mcduck on 2011-03-04
> **hoenybear said:**
> Hy guys. I am new to this forum.

I have a similar problem with "setting permissions". I am trying to install a 2 cd game in wine. I was succesful to do it in Mandriva but in Ubuntu, it says it cant open... like above posts. I also cannot mark file as executable...

I tried installing by terminal wine and drag setup but then when asks for second CD im totally blind... I had to quit install and delete the folder... why isnt Ubuntu easy??

Didi you try the suggestions from the above posts? what happened?

> **hoenybear said:**
> why isnt Ubuntu easy??
It is. It's just that A) your new to it, and learning new things is always harder than doing things you already know, and B) you are trying to install a program that *isn't made to work on Ubuntu*. Try installing a Linux program on Windows or OSX and you'll have lot more troubles than you have with Wine... ;)

---

### Post by hoenybear on 2011-03-04
> **mcduck said:**
> Didi you try the suggestions from the above posts? what happened?


It is. It's just that A) your new to it, and learning new things is always harder than doing things you already know, and B) you are trying to install a program that *isn't made to work on Ubuntu*. Try installing a Linux program on Windows or OSX and you'll have lot more troubles than you have with Wine... ;)

Would somebody please read my post and understand it? It's about installing a game that is intended for Windows platform in Ubuntu. I have Wine configured etc. The game is on 2 CD-s....
 
Citing myself: "I was succesful in Mandriva..." , which means I know what im doing, geeze...

One thing I will never understand: Why things that should be common sense in general use: intuitive, esay  installing from a Setup, or video drivers etc are often omited from most linux distros... and ppl have to waste lots of time to find solutions for very basic common sense stuff... puzzles me...

Oh well, who am i to touch any sensitive spots...

---

### Post by mastablasta on 2011-03-04
you installing issue has much to do with wine and much less with Ubuntu.
 
Also Ubuntu is based on Debian and Mandriva is not. so there will likely be some differences.
 
here is some info from a multiCD diablo 2 install:

Launch winecfg to perform the following tasks:
[LIST]
[*][SIZE=1]
[*]Make sure the Windows version for Diablo 2 is NT 4.0, 2000, XP, or 2003 for correct copy protection support. Diablo 2 supports Win NT 4.0 or later.
[*]Create a drive letter for your cdrom if you have not already. For each cdrom drive letter, click advanced, and set the drive type from automatic to cdrom.[/SIZE]
[/LIST]It helps to add a device node symlink, so do the following. If your cd-rom drive letter in winecfg is d: and the corresponding device node to your mount point is /dev/hdc then run the following command: 
*$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\:* 
Note, you *must* have two colons! You can tell what your device node is in /etc/fstab or viewing your boot-log.
 
For running the multi-disk install, it helps to run the install using the drive letter and to not switch your shell to the cdrom's path. For example: 
*~/.wine/drive_c$ wine "D:\setup.exe" (where D: is the assigned letter of your CD drive).* 
If you run while having a current working directory of /mnt/cdrom, for example, then you will lock the drive and you won't be able to eject the disk.
 
If during the game's install the progress bar stops, the game is probably prompting you for the next disc, but the dialog is under the installer's window. For full install, the order is Install Disc, Play Disc, then Cinematics Disc. Just swap discs and hit enter when the progress stops.

---

### Post by howefield on 2011-03-10
> **hoenybear said:**
> Would somebody please read my post and understand it? It's about installing a game that is intended for Windows platform in Ubuntu. I have Wine configured etc. The game is on 2 CD-s....
 
Citing myself: "I was succesful in Mandriva..." , which means I know what im doing, geeze...

One thing I will never understand: Why things that should be common sense in general use: intuitive, esay  installing from a Setup, or video drivers etc are often omited from most linux distros... and ppl have to waste lots of time to find solutions for very basic common sense stuff... puzzles me...

Oh well, who am i to touch any sensitive spots...

Please don't get irritated with other members who are trying to help you. You have been given a solution, but if you want some more, try this thread :

[http://ubuntuforums.org/showthread.php?t=1500627](http://ubuntuforums.org/showthread.php?t=1500627)

---

### Post by K-Spaz on 2011-05-19
I for one tend to agree with the OP.  Here's my situation

Load any older version of Ubuntu up through 10.04.  Go to package manager and tell it to install wine.

Put in a windows program install CD, autorun works, and the program installer starts AND Runs.

Ok, let's "Upgrade" (almost an oxymoron) to 11.04.  Fresh load on a new system.  

Install wine from package manager.

Insert the SAME Cd, permission problems up the wazoo.  

Now...

What level of 'inexperience' is causing this?  More like I'd say, someone should be burned at the stake.  So now Wine won't run anything on a CD without inordinate configuration changes?  Oh, that's brilliant.  Thanks for saving me from an EXE.  Again I ask, are the powers-to-be at Ubuntu serious?  For me this 11.04 installation has become more of a battle of wills than anything.  I know there's no way I'll continue with this as a permanent desktop OS anymore.  I've got days of googling and re-configuration bs, all for things that 1 year ago needed NOTHING.  It's almost becoming fun to see what a pos they've turned this OS into.  There's not a doubt in my mind, this release has peeps at MS dancing in the streets.  Any marketshare numbers they were worried about will dwindle soon with the largest distro releasing this...

/rant

---

### Post by Morbius1 on 2011-05-19
> So now Wine won't run anything on a CD without inordinate configuration changes?I don't know if the following qualifies as "inordinate":

Right click an *.exe file and select Properties  -> Open With -> Add -> Use a custom command > type in:  wine

In the "Open With" tab mark the "wine"[COLOR=Black] [COLOR=Blue]**you just added**[/COLOR] [/COLOR]as   the default - from the Wine that's already selected. It has to do with something called cautious-launcer. The default in "open with" has it, yours will not.

---

### Post by K-Spaz on 2011-05-19
Thank you Morbius1.

Actually, I did find that before returning here, after some more googling.  Why wine doesn't have something in it's config that would alter this, this long after the 11.04 release, is beyond me.  You can read a long time on google without finding anything relevant.

---

### Post by Morbius1 on 2011-05-20
> **K-Spaz said:**
> Thank you Morbius1.

Actually, I did find that before returning here, after some more googling.  Why wine doesn't have something in it's config that would alter this, this long after the 11.04 release, is beyond me.  You can read a long time on google without finding anything relevant.

Actually, it's not wine that's doing it. How can an application designed to emulate a Windows environment determine the Linux permissions of a given file? It can't. This "cautious-launcher" thing is something Ubuntu adds to the mix.

---

### Post by linuxinstalledfromhdd on 2011-05-20
just for the heck of it.. can you run a chmod on the file you are trying to execute?

chmod 755 nameofthefileyouwanttochange

---

### Post by 3rdalbum on 2011-05-20
People, please: The file is on a CD-ROM. It doesn't have a filesystem that accepts Linux permissions. Even if it did, you can't chmod it because it's a read-only filesystem.

The solution is to use the terminal; open the terminal and type wine then a space, and then **drag the program you want to run to the terminal**. It will fill in its file path and then you can run the file just by pressing Enter.

Being able to double-click a file and run it without it having the execute permission is a perversion of the Unix/Linux security system, and it opens up a can of worms suspiciously shaped like viruses. Ubuntu's cautious-launcher is doing the right thing.

---

### Post by linuxinstalledfromhdd on 2011-05-20
You can tranfer that entire image into a virtual drive and make chmod changes

---

### Post by Morbius1 on 2011-05-20
> **3rdalbum said:**
> Being able to double-click a file and run it without it having the execute permission is a perversion of the Unix/Linux security system, and it opens up a can of worms suspiciously shaped like viruses. Ubuntu's cautious-launcher is doing the right thing.
The perversion of the Linux security system is the installation of Wine itself that has gotten so good at emulating a Windows environment that it will actually run some viruses.
> The solution is to use the terminal; open the terminal and type wine then a space, and then **drag the program you want to run to the terminal**. It will fill in its file path and then you can run the file just by pressing Enter.
That's a "perversion of the Unix/Linux security system, and it opens up a can of worms suspiciously shaped like viruses." ;)

Running it from the terminal with a "wine "path/to/exe/file", copying the contents of the entire cd just to do a chomd +x, or changing the files association to remove "cautious launcher" so that you don't have to run it from the terminal or copy the entire cd are all doing the same thing.

---

