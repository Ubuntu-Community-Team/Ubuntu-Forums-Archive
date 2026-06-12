---
title: "Ubuntu lucid linux 10.04 help"
date: 2011-08-11
forum: General Help
---

### Post by qpmzal on 2011-08-11
Ubuntu
[INDENT]Release 10.04 (lucid)[/INDENT]
[INDENT]Kernel Linux 2.6.32-33-generic[/INDENT]
[INDENT]GNOME 2.30.3[/INDENT]
^ That is the system info under system monitor

Ok so, Here is the story. I WAS running windows XP on my tablet PC until it decided to crash on me. I didn't have the time to fix it so one of my techie friends fixed it for me except he did everything backwards. He put Ubuntu as the main operating system and installed windows XP under virtual Box. 

Now I have the Windows XP Pro ISO on my computer and I want to install that as a dual boot option at the very least, but how do I mount it in Ubuntu in order to install windows xp. I dont want to run xp under virtual box, I either want a dual boot OR to run Ubuntu in virtual box under xp os. 

So I try to mount the ISO with Gmount-ISO and this is what I get when I click on setup in the windows xp iso mount folder....

Archive:  /media/SETUP.EXE
[/media/SETUP.EXE]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/SETUP.EXE may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/SETUP.EXE or
          /media/SETUP.EXE.zip, and cannot find /media/SETUP.EXE.ZIP, period.
........

I know I can install a different windows os while running the computer with Magic Disc Virtual Drive (Running a windows OS) because I have done it before, but I dont know how to do that from ubuntu. Right now I am incredibly pissed at ubuntu and starting to hate it cause I don't know the os at ALL.... At the very least I want to learn it first before I have it as my main OS. But having it as my main os is just driving me away from it <.<

I would go back to my friend but he doesn't know linux that well either. 

Is there a way to run the ISO and get my windows XP back as my main os from an ISO while on ubuntu?

May it also help I don't have a CD drive on this laptop either :(.... It is old and runs off a 40GB IDE Hardrive..... 

Any Ideas?

---

### Post by ~!geek!~ on 2011-08-11
If you want to have a dual boot system, allocate sufficient space for windows using gparted (or any other partition manager). Try some guide to create a bootable disk using windows iso you have or arrange some other bootable disk of windows. Now boot using this disk and install the windows on the space you allocated earlier. If you are able to follow upto this, you will be able to run windows when you start your machine with no option to select ubuntu. 
Now if you want to access ubuntu, use another guide to recover grub after installing windows on a machine already having ubuntu. (Google it, its quite a general problem with the people who install windows after installing gnu-linux). 
or if you don't want ubuntu as dual boot with windows and want to run ubuntu in virtual box, you may use a partition manager in windows and delete the partition having ubuntu and format it to ntfs. Start virtual box and mount ubuntu iso and use it.

---

### Post by karlson on 2011-08-11
> **qpmzal said:**
> 
Ok so, Here is the story. I WAS running windows XP on my tablet PC until it decided to crash on me. I didn't have the time to fix it so one of my techie friends fixed it for me except he did everything backwards. He put Ubuntu as the main operating system and installed windows XP under virtual Box. 


So far so good.

> 
Now I have the Windows XP Pro ISO on my computer and I want to install that as a dual boot option at the very least, but how do I mount it in Ubuntu in order to install windows xp. I dont want to run xp under virtual box, I either want a dual boot OR to run Ubuntu in virtual box under xp os.


First let me caution you about doing this.  Windows doesn't like to be a secondary OS on any computer, so after you install Windows you will need to reinstall GRUB to be able to boot Linux.

> 
So I try to mount the ISO with Gmount-ISO and this is what I get when I click on setup in the windows xp iso mount folder....

Archive:  /media/SETUP.EXE
[/media/SETUP.EXE]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/SETUP.EXE may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/SETUP.EXE or
          /media/SETUP.EXE.zip, and cannot find /media/SETUP.EXE.ZIP, period.
........

I know I can install a different windows os while running the computer with Magic Disc Virtual Drive (Running a windows OS) because I have done it before, but I dont know how to do that from ubuntu. Right now I am incredibly pissed at ubuntu and starting to hate it cause I don't know the os at ALL.... At the very least I want to learn it first before I have it as my main OS. But having it as my main os is just driving me away from it <.<

I would go back to my friend but he doesn't know linux that well either. 

Is there a way to run the ISO and get my windows XP back as my main os from an ISO while on ubuntu?

May it also help I don't have a CD drive on this laptop either :(.... It is old and runs off a 40GB IDE Hardrive..... 

Any Ideas?

The idea of what you want to do is very simple.  Burn the ISO onto a DVD and boot your system from it to install Windows XP if you don't want Ubuntu on it.  If you want Ubuntu to play with I would suggest running it in a Virtual Environment rather then doing dual booting.

---

### Post by qpmzal on 2011-08-11
Ok both ideas are good minus 1 problem, I have no CD drive :/ 

I was trying to use SD cards for this (make it bootable from the SD card) but I cant get Ubuntu to read them, I have 4 of them;
A Kingston micro sd adapter with a 1Gb Micro scan disc card
A Hama 2Gb highspeed SecureDigital card
A Micro Center 1Gb SD Flash Card
and A PNY SDHC 4Gb that came with my camera. 
It is a Built in SD card reader. 
I tried to download drivers for the reader but I have NO idea how to install them :/, I have even looked at manuals online and tutorials, but didn't have any luck <.<.
I usually can figure stuff like this out but Ubuntu seems to be closely related to Mac OS and that OS is confusing as hell to me.  
It seems to be the same concept as modding a game, but I don't know Ubuntu, which makes it INCREDIBLY difficult <.<

Edit: I am going to use XP as my main OS with Ubuntu as a secondary OS either dual boot or us it in VirtualBox on XP

---

### Post by qpmzal on 2011-08-11
-Bump- for more opinions

---

