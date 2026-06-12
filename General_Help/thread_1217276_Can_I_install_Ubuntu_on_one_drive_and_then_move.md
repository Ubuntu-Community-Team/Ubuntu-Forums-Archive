---
title: "Can I install Ubuntu on one drive and then move?"
date: 2009-07-19
forum: General Help
---

### Post by Declanthedork on 2009-07-19
Hello!
I just got a (working) hard drive from the dump. I plugged it in to computer and installed Ubuntu on it with a live CD.

I'm wondering if I can movee that hard drive to my M$ computer so I can have M$ on one HDD and Ubuntu on the other. Will I be able to drop it right in? 

Thank you so much for your time.

-Declan

---

### Post by lindsay7 on 2009-07-19
Yes you should be able to do that.  If you set up each drive in that way then which ever drive you tell bios to see first will boot up. It is a good way to do things but can be a pain because you do not have a true dual boot system. You can set up your system to dual boot from the grub menu but you will need to install grub and then tell it how to start up by mapping the drive in the grub menu.   I have a whole lot of info on doing this that you could sort thru or you can find this same info on this forum.

---

### Post by lindsay7 on 2009-07-19
Here is the info,

```
Dual boot, Two separte systeims







Mark, I prefer not to modify the Windows boot loader in any way, but that option would work the same way for selecting the OS to boot.

Lindsay, nothing is done with the BIOS. The BIOS only knows enough to boot the primary drive. Windows must be the primary drive or it won't boot. So when we unhook the Windows drive and put the Ubuntu drive in it's place, it is the primary drive as far as the BIOS is concerned. As yet, there is no secondary.

When Grub installs on the primary drive during the LINUX install, it knows nothing about a secondary. When the LINUX install is done, plug the Windows drive in the secondary position. You then need to add a few lines of code to the Grub menu file to tell it about Windows. 

The sneaky part that Grub does for Windows is to electronically swap primary drives before calling the Windows boot loader. Windows then is on the primary drive as far as Windows knows.

So for a Windows boot, the BIOS runs Grub on your LINUX drive, Grub swaps the drives, then runs the original untouched Windows boot loader. That's why either drive can be removed and the remainder plugged into the primary position and you now have a single OS system with no changes needed.
    	   
 2 Days Ago 	  #6 
lindsay7 
Way Too Much Ubuntu

 
 
 
Join Date: Feb 2009
Location: Little Rock, AR
Posts: 259 
Ubuntu Jaunty Jackalope (testing) 	Re: Two Hard Drives 
Very cool! Could you post the lines of code that you add to the grub file or post a screen shot of the grub menu. Thanks for the help.
__________________
Six Saturdays a week for me. 
    	    
 1 Day Ago 	  #7 
daveg2 
5 Cups of Ubuntu

 
Join Date: May 2006
Posts: 26 	Re: Two Hard Drives 
Here you go, Lindsay: 

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

title Windows XP Home
map (hd1) (hd0)
map (hd0) (hd1)
root (hd1,0)
chainloader +1

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script

If you copy and paste, you'll be OK. If not, be sure to notice that there are 2 spaces in the map lines and one in the root and the chainloader lines. It's pretty obvious in the editing box, but didn't look so clear in the post.

Yeah, the syntax has to be right which is why I went back and talked about the spaces.  But I can't count.  There are only 2 spaces in the map lines.  You only need one space between the (hd...) and the next (hd...).  Sorry for the confusion.[/QUOTE] 

>  
Thanks one more time, this is a big help! 

You're welcome.  Glad I could help. 

Just got done doing it myself with a from empty disk install of 9.04 beta.  One new thing I learned is that those spaces are at least one or more spaces.  I'm guessing tabs might work, but don't know.  That lets us line things up in more readable columns.[/QUOTE] 

Originally Posted by lindsay7 
Your last post,

Here you go, Lindsay:

title Windows XP Home
map (hd1) (hd0)
map (hd0) (hd1)
root (hd1,0)
chainloader +1

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script

If you copy and paste, you'll be OK. If not, be sure to notice that there are 3 spaces in the map lines and one each in the root and the chainloader lines. 

Can you clear up what you mean when you talk about the 3 spaces in the map lines and 1 space in the root and chainloader lines. Are you saying 1 space between map and (hd1) and 2 spaces between (hd1) and (hd0). And 1 space between root and (hd1,0) and chainloader and +.

Or do you mean something else? I think it is important that this syntax is correct.

Yeah, the syntax has to be right which is why I went back and talked about the spaces. But I can't count. There are only 2 spaces in the map lines. You only need one space between the (hd...) and the next (hd...). Sorry for the confusion.

Dear lindsay7,

You have received a new private message at Ubuntu Forums from daveg2, entitled "Re: One more question, please".

To read the original version, respond to, or delete this message, you must log in here:
http://ubuntuforums.org/private.php

This is the message that was sent:
***************
[/quote]

Yeah, the syntax has to be right which is why I went back and talked about the spaces.  But I can't count.  There are only 2 spaces in the map lines.  You only need one space between the (hd...) and the next (hd...).  Sorry for the confusion.[/quote]


---Quote---
Thanks one more time, this is a big help!
---End Quote---
You're welcome.  Glad I could help.

Just got done doing it myself with a from empty disk install of 9.04 beta.  One new thing I learned is that those spaces are at least one or more spaces.  I'm guessing tabs might work, but don't know.  That lets us line things up in more readable columns.
***************

Again, please do not reply to this email. You must go to the following page to reply to this private message:
http://ubuntuforums.org/private.php

All the best,
   	

Open a terminal,
cd /boot/grub
sudo cp menu.lst menu.lst.org # So you have a backup
sudo vi menu.lst
arrow key down to just before "### BEGIN AUTOMAGIC KERNELS LIST"
i to put you in insert mode
copy one line and paste into vi, enter to put you on the next line
repeat until done
[escape]:wq to save it and exit.

There's probably an easier to learn GUI editor on the Ubuntu menu, but I've never used it.

This thread suggests instead of sudo vi, use gksudo gedit. That's a graphical editor that might be easier to use. He also gives a very clear description of exactly the technique we're talking about.
http://ubuntuforums.org/showthread.php?t=179902


Dualboot Two Hard Drives 
As a beginner, I wanted to set up a dual boot without installing Grub to windows and was able to find two excellent links for doing this:

http://www.ubuntuforums.org/showthre...umper+settings
http://ubuntuforums.org/showthread.p...880#post677880

The excellent instructions provided by "lha" worked flawlessly for installing on 2 IDE drives.

I also found links to dualboot with a SATA and an IDE drive:

http://www.ubuntuforums.org/showthre...dual+boot+sata
http://www.ubuntuforums.org/showthread.php?t=192954
http://www.ubuntuforums.org/showthre...=275728&page=3
The above IDE + SATA threads are probably outdated, but I'll leave them FYI.

Hope this helps someone looking for an alternate method of dualbooting with 2 hard drives...

I have my personal computer set up to dualboot using the method described in the first two links, lha has give me his "blessings" to write up a HowTo with his instructions. This is an alternate method of dualbooting Ubuntu and Windows, using 2 hd, without installing grub to Windows or altering your Windows installation.

First, disconnect your Windows drive, then connect the drive you want to install Ubuntu on as the primary IDE master drive. After installing Ubuntu, allow the updater to install all the necessary updates, this may take awhile. Shutdown your computer and reconnect your Windows drive as slave, then restart, your computer will boot into Ubuntu.

You will need to edit your menu.lst file:
(Open a terminal, copy & paste one line at a time, press "enter" each time)

Code:
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
The first line changes to the grub directory, the second line makes a backup of your menu.lst file, and the third line opens the menu.lst file using the gedit text editor.

Copy and paste the following lines above the line
###BEGIN AUTOMAGIC KERNEL LIST
Code:
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
If grub gives an error when rebooting, you can try rootnoverify (hd1,0) instead of root (hd1,0) in the second line.

Note: If you prefer Ubuntu to boot by default, you can copy & paste the above entry at the very end of your menu.lst, instead of above ###BEGIN AUTOMAGIC....

To automatically display the grub menu at bootup, find the line
Code:
hidden
and replace with 

Code:
#hidden
To adjust the time grub is displayed at bootup, change the timeout(in seconds)...I'd suggest 10 seconds(default is 3).

Quit and save settings.

Note: If for some reason you need to restore your original menu.lst:
Code:
cd /boot/grub
sudo cp menu.lst_backup menu.lst
Reboot your computer, it will automatically boot to Windows, unless you choose Ubuntu within the time grub is displayed.

If you want to uninstall Ubuntu, you can make the Windows drive primary master and reformat or unplug the Ubuntu drive.

If you want to remove Windows, then you can unplug the Windows drive or reformat it, then open menu.lst

Code:
gksudo gedit /boot/grub/menu.lst
and remove the Windows entry in grub.

Installing on a Dell Dimension 4550:
I tried the above method trying to set up a dualboot on my Dell Dimension 4550, but when I tried to boot into Windows, I got "Error 21:Selected disk does not exist".
I finally was able to get it to work by:
Boot into Ubuntu, open up a terminal:
Code:
sudo fdisk -l
The -l is a lowercase "L"
Code:
cat /etc/fstab
From these two commands, I was able to determine that hdb, which was the slave drive with windows actually had 2 partitions. The first partition was a 35 Mb Dell utility and the second partition was Windows, so I changed the Windows root from (hd1,0) to (hd1,1) in the /boot/grub/menu.lst. However, I continued to get the error21 message...I thought maybe the jumper settings on the slave drive were incorrect. Fortunately, I entered bios setup by pressing "F2" during bootup and found out that the Primary ide controller for hd1 was turned "off" by default...I changed it to "Auto" detect. Grub booted directly into Windows and I'm enjoying dualboot of Windows and Dapper on my Dell computer.

It is possible to set up a dualboot with Windows & Ubuntu on separate hard drives, with both hard drives connected during the install of Ubuntu:
http://www.ubuntuforums.org/showpost...8&postcount=47
if you want to be absolutely sure not to overwrite your Windows mbr, then disconnect your Windows drive during Ubuntu installation.

An excellent tool to download before installing Ubuntu is the Super Grub Disk:
http://users.bigpond.net.au/hermanzo...bDiskPage.html
the Super Grub Disk is capable of restoring Windows mbr or reinstall grub...and can boot either Windows or Ubuntu.
Last edited by confused57; July 8th, 2008 at 03:09 PM.. Reason: Instructions 
    	   
 May 21st, 2006 	  #2 
confused57 
Ubuntu addict and loving it

 
Join Date: Dec 2005
Location: Eden, N.C.
Posts: 4,502 
Ubuntu 8.04 Hardy Heron 	Re: Dualboot Two Hard Drives 
The definitive guide for dualbooting Windows and Ubuntu on a single hard drive, using the alternate cd, can be found at Herman's site:

http://users.bigpond.net.au/hermanzone/

For Dapper Desktop CD:
http://www.psychocats.net/ubuntu/installing

The guides can be used to install on 2 different hard drives, but Windows would need to be the master drive and Ubuntu the slave drive. You would select "IDE drive hdb" to install Ubuntu onto and install Grub to Windows(hda) when prompted. Windows doesn't like it when it's not the first OS in a dualboot system, therefore, it has to be on the master drive when using this method. (The menu.lst(Grub) Windows entry, provided in the links in my first post method, has a mapping command, which fools Windows into thinking it is the first OS.) 

If you decide to uninstall Ubuntu, heaven forbid, you'd need to boot up your computer with the Windows installation CD, go to recovery mode and enter fixmbr, which restores your Windows mbr(deletes Grub). Then you could reformat the slave drive from Windows.

Note: I would recommend anyone installing grub onto their Windows mbr when setting up a dual boot with Ubuntu to download the Windows 98SE OEM boot floppy from bootdisk.com as described here:
http://www.users.bigpond.net.au/hermanzone/p18.htm
If for some reason Ubuntu or grub becomes corrupted, you would need to repair your mbr in order to boot Windows, by booting up with the Win98SE boot floppy and enter fdisk /mbr. The boot floppy would be useful for anyone not having a Windows install cd, or as a backup for those that do have one.

I opted to post this method as a reply, rather than editing my first post, since it is a different way of setting up a dualboot with 2 hd. Any adivce from more experienced Ubuntu Linux users concerning dualbooting would be welcomed.

I feel that having one link with various options concerning dualbooting with 2 hd, most importantly with Herman's guide, would give a beginner alternative methods for setting up a dualboot Windows/Ubuntu system. My initial intent was to offer only the dualboot method by "lha", but other options would be helpful, in my opinion...so that beginners would have a choice depending on their system, their experience with computers & linux, and their preferences...
Here's a thread with one person's solution to dual boot dual hard drives:
http://www.ubuntuforums.org/showthread.php?t=259422

If your computer supports selecting which drive to boot in bios:
http://www.ubuntuforums.org/showthread.php?t=275728

Tip: Before installing Ubuntu on your system, you should try running the liveCD to ensure that there are no hardware incompatibilities and to familiarize yourself with the Ubuntu OS.

Note: If you're installing Ubuntu to dualboot with Windows on a single hard drive, Windows MUST be on a partition located prior to Ubuntu...e.g. Windows on hda1, Ubuntu on hda2.
Last edited by confused57; October 13th, 2006 at 11:58 AM.. 
    	   
 August 1st, 2006 	  #3 
shoki 
Just Give Me the Beans!

 
 
 
Join Date: Jul 2006
Posts: 67 	 Re: Dualboot Two Hard Drives 
To everybody that brought this information to this place at this time... Thank you so much!!! What an awesome eloquent way to do this. Virgin Windows Install, Virgin ubuntu Install move one jumper, edit one text file and you are in heaven...  (with 2 virgins) sorry I couldn't resist.

Anyway than you very much. This kind of solution is what makes Liniux such a great OS.

--Shoki
    	   
 August 2nd, 2006 	  #4 
confused57 
Ubuntu addict and loving it

 
Join Date: Dec 2005
Location: Eden, N.C.
Posts: 4,502 
Ubuntu 8.04 Hardy Heron 	Re: Dualboot Two Hard Drives 
Quote:Originally Posted by shoki  
To everybody that brought this information to this place at this time... Thank you so much!!! What an awesome eloquent way to do this. Virgin Windows Install, Virgin ubuntu Install move one jumper, edit one text file and you are in heaven...  (with 2 virgins) sorry I couldn't resist.

Anyway than you very much. This kind of solution is what makes Liniux such a great OS.

--Shoki

Thanks, for me it was the more desirable option, don't have to worry about repairing your Windows mbr,etc and as you mentioned, it's quite easy to set up. You summed it up nicely.
    	   
 August 3rd, 2006 	  #5 
shakyone 
5 Cups of Ubuntu

 
Join Date: Jul 2006
Posts: 28 	Re: Dualboot Two Hard Drives 
Confused57,

I also want to thank you. I was trying to figure a method to insulate the wife from ever dealing with the fact that I put Ubuntu on the computer. Why, because she is dependent on Windows to remote-connect to her place of employment. She is very wary that I will screw up the computer permanently and for good reason. 

I have been searching for a method to use NTLDR with a Linux-Ubuntu option, but it was looking procedurally complicated and a little risky, since it involved tinkering with the Windows drive MBR. 

After reading your method I realized there is the “ever present” Windows recovery option of returning the Windows drive back to the Master IDE position from the slave position. Last night I demonstrated the recovery option to the wife after following your procedure for installing Ubuntu and modifying GRUB. She is satisfied since the recovery demonstration gave absolutely ZERO indication that the PC ever functioned using the Linux OS, nor did it indicate a hard drive was ever removed. All because the MBR in the Windows drive is left intact throughout your method. My Ubuntu/XP computer works like charm with XP set as the default OS on GRUB. Wife is happy, and I get to have my fun too. Have a great day!
    	   
 August 17th, 2006 	  #6 
Josh_b 
A Carafe of Ubuntu

 
Join Date: Jul 2006
Location: Australia
Posts: 91 
Ubuntu 6.06 	Re: Dualboot Two Hard Drives 
I'm pretty sure (Me=Linux Newbie) there is a quicker way, without having to change all the files and such as in your how-to. 
This is the way I did it:
I have a SATA drive for Windows XP and and IDE drive for Ubuntu 6.06. In the BIOS, I set the CD-ROM as first device (when installing Linux) and then the IDE drive to be the first hdd to start-up. After that just install Linux (with GRUB) and Bob's your uncle. 

If I go back into BIOS and set the SATA drive as default hdd, then the GRUB doesn't show, and if I set the IDE as default, then GRUB shows, with Linux as default OS.

Hope that helps,
Josh
    	   
 August 17th, 2006 	  #7 
confused57 
Ubuntu addict and loving it

 
Join Date: Dec 2005
Location: Eden, N.C.
Posts: 4,502 
Ubuntu 8.04 Hardy Heron 	Re: Dualboot Two Hard Drives 
Quote:Originally Posted by Josh_b  
I'm pretty sure (Me=Linux Newbie) there is a quicker way, without having to change all the files and such as in your how-to. 
This is the way I did it:
I have a SATA drive for Windows XP and and IDE drive for Ubuntu 6.06. In the BIOS, I set the CD-ROM as first device (when installing Linux) and then the IDE drive to be the first hdd to start-up. After that just install Linux (with GRUB) and Bob's your uncle. 

If I go back into BIOS and set the SATA drive as default hdd, then the GRUB doesn't show, and if I set the IDE as default, then GRUB shows, with Linux as default OS.

Hope that helps,
Josh

Thanks for sharing and your method has proven to be another method of setting up a 2 hard drive dualboot.
The Desktop Live CD doesn't allow you to select where to install grub, so the "howto" I described ensures that grub doesn't overwrite your Windows mbr...definitely takes a little longer disconnecting and reconnecting drives. I assumed there were other methods of setting up a dualboot(2 hard drives) without installing grub to the Windows mbr and I welcome anyone adding to this "howto" with an alternate installation option.

Update: Starting with Ubuntu Feisty 7.04, the Desktop Live CD does allow you to specify where to install grub by clicking on the "Advanced" button during installation & typing in a different location, instead of the default (hd0)...e.g. you could enter /dev/sda, /dev/sdb, etc.
Last edited by confused57; September 26th, 2008 at 10:40 AM.. 
    	   
 August 21st, 2006 	  #8 
GroverDill 
First Cup of Ubuntu

 
Join Date: Aug 2006
Posts: 1 	Re: Dualboot Two Hard Drives 
Code:
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
This worked great for me, except I orginally had these commands mistyped in grub. It should be noted that there is a SPACE between (hd0) and (hd1) in both the 'map' lines. Otherwise, Grub responds with an error 11: unrecognized device string.

That unix is so literal...  

Thanks for the solution, all. It's very cool.
    	   
 August 21st, 2006 	  #9 
confused57 
Ubuntu addict and loving it

 
Join Date: Dec 2005
Location: Eden, N.C.
Posts: 4,502 
Ubuntu 8.04 Hardy Heron 	Re: Dualboot Two Hard Drives 
It's actually better to copy & paste commands and entries, because it is difficult to tell where the spaces are in the typed commands, etc.
    	   
 September 5th, 2006 	  #10 
mxreader 
5 Cups of Ubuntu

 
Join Date: Jan 2005
Location: Australia
Posts: 24 
Ubuntu 6.06 	Re: Dualboot Two Hard Drives 
I am trying to find a solution to getting Ubuntu to boot off Grub on the IDE XP MBR (Ubuntu is on SATA). I am reading here to see if I can learn something that may help.

The early post gave a link
http://www.ubuntuforums.org/showthre...dual+boot+sata

but there the commands are: 
6. In Ubuntu go to Applications/System Tools/Terminal. You will need to open a text editor and change the grub menu file:
$cd /boot/grub
$sudo gedit menu.lst
now look for an entry (near the end) that reads like something like this:

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
chainloader +1

and change it to this:

title Microsoft Windows XP Professional
root (hd1,0)
map (hd1,hd0)
map (hd0,hd1)
chainloader +1

7. save the file
8. reboot and test boot into XP

Notice the difference in the map ..... commands?
man I am confused now.
    	
```

---

### Post by philcamlin on 2009-07-19
yes you can do what you want to do

---

