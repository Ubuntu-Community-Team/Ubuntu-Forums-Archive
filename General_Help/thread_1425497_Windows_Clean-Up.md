---
title: "Windows Clean-Up"
date: 2010-03-09
forum: General Help
---

### Post by giddyup306 on 2010-03-09
My Ubuntu partition is just about out of memory, and I need to do some cleaning of the windows.  I couldn't find a lot on here (maybe I wasn't using the right terms), and when I looked on google it seemed like the only results I found were from people that wanted to remove linux from windows.  What I'd like to do is create a very, very small partition for windows for when I need it (burning MP3s to CDA and my printer only).  I wouldn't mind re-installing windows and starting from scratch (I have all my software backed up) and then installing Ubuntu a backed up version of Ubuntu.  Except I can't get Clonezilla to install for the life of me after several attempts.  

So is their any (hopefully easy) way to clean up windows without going to extremes?

Thanks in advance.

PS I'm still pretty new so you might have to go slowly in explaining the process to me. ;)

---

### Post by zvacet on 2010-03-09
If you want to resize your Windows partition then first removeprograms you don't need.You can use [Revo]("http://www.revouninstaller.com/") or some other tool for that.After that defragment Windows partition few times.For shrinking you can use Ubuntu live CD or [Gparted live CD.]("http://gparted.sourceforge.net/") When you shrink Windows increase Ubuntu partition on that free space.

---

### Post by giddyup306 on 2010-03-09
After I installed Revo it gave me an Application Error Exception EAccessViolation in module RevoUninProSetup.tmp at 000016F3. Access violation at address 004016F3 in module 'RevoUninProSetup.tmp'. Write of address 00000000.

---

### Post by Kevbert on 2010-03-09
You may need to turn off the Windows swap file first (as this is normally at the end of the Windows partition. This can be found (for XP) under Settings-Control Panel-System-Advanced tab-Performance Settings button-Advanced tab. Change the Virtual Memory paging file to 'No Paging file'. Save this and reboot to make sure the settings are used. Next defrag the hard disk in Windows.
After you've resized Windows with Gparted, it may be worth booting Windows immediately afterwards, as it may complain and allow chkdsk to run to check the Windows partition integrity.

---

### Post by giddyup306 on 2010-03-09
I ran the disk defrag tool and when it was done it said that it couldn't move some files (I saw that there were some files still in the right hand side).  I then went to try and Gparted live, and it wouldn't do anything.  Now what?

---

### Post by HiRez_L on 2010-03-09
Have you tried getting cd burning and your printer to work from Ubuntu instead?  Then you could wipe windows . . . .

---

### Post by Kevbert on 2010-03-09
> **giddyup306 said:**
> I ran the disk defrag tool and when it was done it said that it couldn't move some files (I saw that there were some files still in the right hand side).  I then went to try and Gparted live, and it wouldn't do anything.  Now what?

Did you reboot between turning off the paging file and the defrag ?  If it still doesn't work then it may be that you have some protected software that can't be moved.

---

### Post by giddyup306 on 2010-03-09
> **HiRez_L said:**
> Have you tried getting cd burning and your printer to work from Ubuntu instead?  Then you could wipe windows . . . .

The only way I've heard of burning an MP3 to CDA in Linux is to convert it to WAV then CDA.  Too much work.  I could switch over to windows and convert it a lot faster.  Unless if there is a program that converts and burns directly this really isn't an option.

---

### Post by giddyup306 on 2010-03-09
> **Kevbert said:**
> Did you reboot between turning off the paging file and the defrag ?  If it still doesn't work then it may be that you have some protected software that can't be moved.
Yes, I rebooted between the paging file and defrag.

---

### Post by lisati on 2010-03-09
Try cleaning out Windows' "%temp%" directory - see the link in my sig.

edit: [SIZE="4"]**caution:**[/SIZE] The software available available through the link was originally written for Win98SE, and I've used it on XP & Vista without hassle but haven't had a chance to check for unintended side-effects on Win7 yet.....read cautions on web site **before** using it. Source code long lost during assorted upgrades to hardware.

---

### Post by giddyup306 on 2010-03-09
Okay guys I really messed something up,  When I went to install the windows temp cleaner I went back into windows and got the error message : Windows could not start because of a computer disk hardware configuration problem.  Could not read from the selected boot disk.  Check boot path and disk hardware.  Please check the windows documentation about hardware disk configuration and your hardware reference manuals for additional information.

Okay fine I at this point was just thinking about getting rid of windows completely.  Then I went to get back into Ubuntu and it said:  Install problem.  The configuration defaults for GNOME Power Management have not been installed correctly.  Please contact your computer administrator.  

HELPPPPP!

---

### Post by giddyup306 on 2010-03-09
I tried doing several things including re-installing the GNOME desktop.  Still nothing.  Please help!

---

### Post by kerbyn on 2010-03-10
> **giddyup306 said:**
> The only way I've heard of burning an MP3 to CDA in Linux is to convert it to WAV then CDA.  Too much work.  I could switch over to windows and convert it a lot faster.  Unless if there is a program that converts and burns directly this really isn't an option.

Brasero Disc Burner (Applications - Sound & Video) does a great job of burning audio CDs from mp3 source files.

And I bet you could get your printer working with a bit of tinkering - what model is it?

The ONLY thing I now use Windows for is to maintain my (pre-existing) Access databases. I run Windows 7 as a guest OS under Virtual Box. Works a treat and no messing around with partitions.... ;)

---

### Post by kerbyn on 2010-03-10
> **giddyup306 said:**
> Okay guys I really messed something up,  When I went to install the windows temp cleaner I went back into windows and got the error message : Windows could not start because of a computer disk hardware configuration problem.  Could not read from the selected boot disk.  Check boot path and disk hardware.  Please check the windows documentation about hardware disk configuration and your hardware reference manuals for additional information.

Okay fine I at this point was just thinking about getting rid of windows completely.  Then I went to get back into Ubuntu and it said:  Install problem.  The configuration defaults for GNOME Power Management have not been installed correctly.  Please contact your computer administrator.  

HELPPPPP!

If you boot from the Live CD there is an option to repair a broken installation. That might do the trick. Good luck!

---

### Post by giddyup306 on 2010-03-10
> **kerbyn said:**
> If you boot from the Live CD there is an option to repair a broken installation. That might do the trick. Good luck!
The only options the Live CD give me are try without changes, install Ubuntu, check disc for defects, memory test, and boot first from hard disk.

---

### Post by giddyup306 on 2010-03-10
> **kerbyn said:**
> Brasero Disc Burner (Applications - Sound & Video) does a great job of burning audio CDs from mp3 source files.

And I bet you could get your printer working with a bit of tinkering - what model is it?

The ONLY thing I now use Windows for is to maintain my (pre-existing) Access databases. I run Windows 7 as a guest OS under Virtual Box. Works a treat and no messing around with partitions.... ;)

I've got VB running win2k installed inside Ubuntu.  It took forever to get the USB to work correctly in it tho.

---

### Post by giddyup306 on 2010-03-10
Okay I tried to do a fresh install, but my live CD and USB won't install.  I get to the install screens, and after I hit the make it happen button nothign happens.   I'm downloading a fresh copy of 9.10 and then going to make a boot USB off of that.  How can I wipe EVERYTHING clean and just install Ubuntu?  I'm really at ends wit here guys.  My laptop is history - broke it in half.

---

### Post by kerbyn on 2010-03-11
To wipe everything off your disk get yourself a Gparted bootable CD and then trash all/any partitions.

If you have problems with the Live CD try the alternate (text based) cd image...

---

### Post by karthick87 on 2010-03-11
Goto **Run-->Prefetch** and clean all files...

---

