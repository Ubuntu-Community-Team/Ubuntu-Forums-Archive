---
title: "dual boot help (win 7 -vista -ubuntu)"
date: 2010-02-02
forum: General Help
---

### Post by Danny_Fancher on 2010-02-02
// not sure if this topic is in the right place or not if not                         please let a moderator know so it can be moved. 

// I can navigate and do basic things inside Linux I am currently learning the ways of the road.

I have a 500 gig hard drive inside my desktop. ( HP slimline ) 
Created partitions for each of my OS's
I have windows 7 ultimate installed 
I have windows vista black installed
I have a partition ntfs just for backup media and files
I have the newest version of ubuntu installed as well as the swap

I believe my problem came when installing ubuntu I decided to venture off into the advanced settings somewhere when it came to the grub loader and I chose something about windows because I wanted the win 7 to be the main os. 

//I know I messed up...... moving on........

//I ultimately would like to start the computer and have a selection list to choose from my 3 os's

I do have the grub loader pop up and windows 7 is listed however the vista black is not and each linux entry appears to be doubled but that could be irrelevant, however when I choose the windows 7 selection it just restarts the grub loader and nothing has happens.

I have tried everything I feel comfortable with inside the terminal to fix this, I have also used many different boot options such as repairing with windows and other boot tools and to no avail nothing has changed. 

Please any help at all would be great. 

// If I have left out details that you need to help me please let me know by emailing me - [email]dannyfancher@gmail.com[/email]  or contacting me through here. 

Thanks

// Update : Easybcd is a tool I have been appointed to only I can not get into my windows distro so if there is a way to just force boot to that somehow so I can use that application let me know.

---

### Post by ImperialXT on 2010-02-02
Can you please post a copy of your menu.lst file. More info can be found here: [https://help.ubuntu.com/community/GrubHowto]("http://ubuntu-tutorials.com/2006/12/29/tweaking-grub-ubuntu-510-6061-610/")

---

### Post by oldfred on 2010-02-02
windows has to combine its boots as that is the only way it knows how to boot. If you want to boot each directly from grub there is a work around when you install the second windows.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

I do not know easyBCD, some say it works but it adds confusion to me. If you want help there it would be better to go to there forums.

Download this script to document your system:
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by red eye dragon on 2010-02-02
THE GRUB FIX,  for 9.10 and 9.04—8.04-8.10 go to bottom of this book and read the last chapter----problem seems to be with grub legacy and grub2----500 mile to go and an hour to get their. Looks like a problematic situational time issue. It appears that grub legacy and grub2 are having issues with error 13,17, I believe 22. after reading for about two days I believe I figured it out.  THE GRUB FIX. OK here it is a lot more simple then everyone is making it out to be. If you have data that you would like to save I suggest you boot from the disk Ubuntu live CD and mount too the hdd Ubuntu is installed on and grab any important data that might be valuable or if you know how to run a back up thats another option. But with the live cd you can copy and past it to another hard drive and check the data to make sure its saved to the new location. And its also easyer on people who have never thought about backing up their data until today.
  However, accomplish the task mentioned, shut the pc down unplug power and switch hdd1 or sata1 that I am assuming windows is installed On with hdd2 were ubuntu probable is installed unless you have 3 or 4 hdds. But no matter make sure Ubuntu is physicaly set on sata1 or hd1 by hand on the mobo([SIZE=2]some motherboards(mobos) may have it listed on the board as the hd  or sata with the # [/SIZE][SIZE=3]0 [/SIZE]) OR the cable  swaped  physical from the back of the hdd. I simple unplugged the sata cable and swapped from the back of my hdd instead of disconnecting it from the mobo it seemed easier and less wear on the mobo. After doing so Ubuntu is now set up were windows once was and ubuntu now should be the 1[SIZE=5]st[/SIZE][SIZE=5] [/SIZE]hdd connected to the mobo. Windows now should be were ubuntu once was. OK restart your system and you should get an error message, don't sweet, we are making sure Bios has a chance to pick up the new hdd change cordanating bois config for install and new grub setup. Shut the PC down and reboot from the live cd or Ubuntu install disk as you would do during a fresh install if it were me I would go with 9.10. -64 bit system if you have 64 bit other wise 32 bit, this way your up to date with whats new and also go for the upgrade since your going threw this trouble, no matter thats a personal prefrence. But 9.10 has cool stuff and why hold back right? but this will work on 9.04-9.10--- OK Run the disk as you would doing a fresh install and follow threw the regular procedure until you reach the partition manager,section or step what ever you want to call it.  do the fresh install and do not mess with any of the default settings other than choosing the correct hdd for the ubuntu install. Grub will assume for some strange reason that dev/sda the first partition is Ubuntu. Yes ,  grub boot loader plays a guessing game when it installs grub, trust me on this one. But we are not going to leave a guess to a program that was designed by people. Thats why We know now grub and our hardware are 100% corrosponding with one another. After the install reboot your system and your good to go. You now have grub lagecy .97 I think, after you have reboot your yall have some updates that will be waiting on you grub2 will be in it, when it goes to install chose keep local version and stay away from it until it is more stable this applies to the 64 bit system people 32 cant really say now that I know longer own 32 bit systems.  
 

 8.04 8.10 you can do the exact same thing if you do not have a live disk down load 9.04 or 9.10 and boot to live disk to snatch your data from the broke booter system then reinstall your version. And If  thats a problem and you cannot get access to a disk for some strang reason, act like your doing fresh install but do not partition the disk, when it comes time to partition hit esc botton on key board and package manager should pop up click grub bootloader reinstall and you can rap it up from their follow the instructions  
 
> **oldfred said:**
> windows has to combine its boots as that is the only way it knows how to boot. If you want to boot each directly from grub there is a work around when you install the second windows.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

I do not know easyBCD, some say it works but it adds confusion to me. If you want help there it would be better to go to there forums.

Download this script to document your system:
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by 2hot6ft2 on 2010-02-02
For Vista not showing up in the grub have you tried updating grub?
```
sudo update-grub
```
or reinstalling it?
> Using Ubuntu 9.10 livecd
Here assuming the Ubuntu partition is sda7,and /boot partition is sda6 (if you have a separate /boot partition).
Boot up ubuntu from the livecd,open terminal and run:

To get the info needed use:
```
sudo fdisk -l
```

Then to actually do it use:
```
sudo -i
mount /dev/sda7 /mnt
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
grub-install --root-directory=/mnt/ /dev/sda


```
Replace sda7 and sda6 with those for your setup.
From [Grub 2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275")

As for
Windows 7 ultimate
and
Windows vista black

are highly bootlegged copies of windows. That being said. There are problems with the Windows 7 boot loaders being used on the bootlegs resulting in the system rebooting. See the long thread here:
[http://forums.mydigitallife.info/threads/8632-Program-based-Windows-7-loader](http://forums.mydigitallife.info/threads/8632-Program-based-Windows-7-loader)
Might take a look at pages 572 and up.

Anyway if once the grub shows up and you choose Ubuntu it boots fine.
Then when you try booting win 7 it reboots and you've already tried the win 7 recovery and it still reboots, then it's time to contact M$ if it's not a bootleg.

---

### Post by Danny_Fancher on 2010-02-02
Thanks very much for all the quick replies. I will be trying them after I write this message and get back to you all. 

again very quick replies and all hopefully helpful thanks guys.

---

### Post by cat2005 on 2010-02-03
What if I want Windows XP on 1 internal SATA hdd and Linux Ubuntu 9.04 on the other internal SATA hdd?
 
Would it be the same as described in this thread, or not?

---

### Post by cat2005 on 2010-02-05
Bump...anyone?

---

### Post by oldfred on 2010-02-05
cat2005
Unless your problem is exactly the same it is better to start a new thread as then we can directly comment on your exact issue.
With 2 drives you should have no issues if you set the BIOS to boot the Ubuntu drive first before you install. It will find your windows install and set windows up to boot from the second drive and make windows think it is still first. That is always the best case as the windows drive will still have the win boot loader in its MBR and worst case you can in BIOS set that drive first and boot windows. Your windows drive is then not modified at all.

---

### Post by cat2005 on 2010-02-05
> **oldfred said:**
> cat2005
Unless your problem is exactly the same it is better to start a new thread as then we can directly comment on your exact issue.
With 2 drives you should have no issues if you set the BIOS to boot the Ubuntu drive first before you install. It will find your windows install and set windows up to boot from the second drive and make windows think it is still first. That is always the best case as the windows drive will still have the win boot loader in its MBR and worst case you can in BIOS set that drive first and boot windows. Your windows drive is then not modified at all.
 
 
Thanks.  Since I don't know if my problem is exactly the same, I will start a new thread.

---

