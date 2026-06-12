---
title: "Ubuntu is running in low-graphics mode - Ubuntu 10.4 LTS"
date: 2010-06-10
forum: General Help
---

### Post by sajumuhamma on 2010-06-10
My computer installed with Ubuntu 10.04 LTS. To the last day it was working well. But after online upgrade when i restarted the computer it showing following error message.

[COLOR=DarkRed]Ubuntu is running in low-graphics mode

Your screen, graphics card and input device settings could not be detected correctly. You will need to configure these yourself.[/COLOR]

Hence I can not boot the system.

Any way to rectify this using live CD. Please help me.

---

### Post by itsols on 2010-06-11
Hey, I had the same problem and I fixed it with some help.

My config is: Dell Inspiron 2.8Hhz P-IV laptop.

Apparently, the new kernel of 10.04 has a problem with my hardware and this includes the display card. So I had to change the kernel.

Here's the link to get he fix. How to solve.

1. Visit the link: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/) from another computer.
2. download the relevant files. In my case, the three .deb files - two ending with i386 and one ending with 'all'
3. boot the BAD ubuntu installation into recovery-mode. It's text only. If it does not work, try booting into an older kernel's recovery console.
4. Take the files either via CD, pen drive or LAN to defective Ubuntu unit.
5. dpkg and install them. Since all downloads here start with 'linux', you can use dpkg -i linux*
6. reboot.

NOTE: This is what I did on MY computer. And it works fine. I mean it boots into graphics mode. and it's beautiful. But there are still issues and I'll post it in a different thread.

Happy Computing!

---

### Post by sajumuhamma on 2010-06-12
Thanks for the replay

But I can not boot the system from hard disk. Since i am using only Ubuntu there is no grub menu to get recovery mode. I am now using Live CD for working.

---

### Post by itsols on 2010-06-13
You can try this:

1. Boot with live cd.

2. Update kernel using terminal

3. Reboot from HDD.

Additionally, check the system log to see for any errors in boot. Usually the upgrade has had errors in the following:

1. corrupt flash plugin
2. Incompatible kernel
3. Incompatible graphics drivers.

Cheers!

---

### Post by sajumuhamma on 2010-06-13
I am not so experienced in Ubuntu. Hence please let me know step by step procedure.

---

### Post by teilnehmer on 2010-06-13
I'm not very experienced myself, but try holding down Shift during start-up, this is supposed to show GRUB so you can choose recovery mode. Didn't work on my machine, but it's what I read. 

Where do you end up after boot? Black screen or command line or something else?

Best regards!

---

### Post by itsols on 2010-06-13
Yes, you can hold down the SHIFT key as the system restarts. But if it won't work, try hitting the ESCAPE key. You should get the same menu.

---

### Post by owners4life5 on 2010-07-22
thank you for i think i know how to do this... but there are two .debs that end in all... the first or the 2nd one?

---

### Post by itsols on 2010-07-22
Yes there are two files ending with 'all'... But the one you need is the one that reads 'linux-headers' and not 'linux-source'.

Hope it helps.

Cheers!

---

### Post by owners4life5 on 2010-07-22
okay. so i followed your directions after installing the three packages. i plug in my pendrive, and go to the recovery console. i drop a root, and this is what happens:

```
root@brian-laptop:~# dpkg -i linux*
dpkg: error processing linux* (--install):
 cannot access archive: No such file or director
Errors were encountered while processing:
 linux*
```

so what do i do now? i have a dell mini 9 if that helps

---

### Post by itsols on 2010-07-22
You're trying dpgk in the wrong path. before running dpkg, you've got to move in to the path where the files are located. To ensure that the files are there, try typing "ls" in the command line to see if your files are there.

If you can't find the files there, maybe you've moved them to a folder. If for example you've got a folder called /home/khalid, you've got to use the CD command to change into that directory like this:

cd /home/khalid

And then use 'ls' again to see if the downloaded files are there. If they're not there, you've not copied the files correctly.

---

### Post by owners4life5 on 2010-07-23
everything worked and unpacked itself this time... i got excited, reboot. still there. "ubuntu is running in low graphics mode."... 

such a disappointment....

---

### Post by itsols on 2010-07-23
The message about low graphics mode - is it on command line or is it in graphics mode? Does the OS boot in to ANY graphical environment?

---

### Post by owners4life5 on 2010-07-23
well i try to boot as usual, of course.

then, when it is booting, it goes through BIOS, etc. then it shows my plymouth screen (you know, the progress screen)..

then once that goes away, it brings me to an environment with a mouse, somewhat GUI.

it gives the message about low-graphics... and it gives me 5 options which are:
1)run ubuntu in low-graphics mode for just one session
2)reconfigure graphics
3)troubleshoot the error
4)exit to console login
5)restart X

i.ve tried all of them to no avail... maybe i. just doing something wrong

---

### Post by itsols on 2010-07-23
OK, first, get yourself together... I don't think you're going to like what I'm going to say.

Honestly, I don't think you're doing anything wrong now. If the installation went off well, following these steps:

1. Full shutdown.
2. Cold start (reboot afresh).
3. Wait for the disaster screen - the one that states you're in low graphics mode.
4. I think the first option is to continue to use the low-graphics mode. Don't panic... wait a few seconds - maybe even 30 seconds.
5. In the mean time, TRY to spot the mouse pointer by moving the mouse slowly across the screen. Sooner than expected, you should see the pointer like a cross (x).
6. When you get the pointer, make sure you've selected low-graphics mode and click the OK button.
7. Now you should be in Ubuntu with the GUI.

If the above did not work, I have the following suggestions (you may not like it though) :

1. Contact your vendor/manufacturer or try to see if there's a driver from them. Usually Dell, HP and the like have drivers online.
2. The truth is that version 10.4 has major issues. I'm stuck with it because I don't have time to go back to the older version. It involves reinstalling so many packages and I'd look at sacrificing at least three days to restore all my development files, etc... So I have no choice. But if you DO have a choice, I'd advise you to grab the last version - I think it was 9.10 - just check it out.

In the mean time, even I'm hoping that I get a fix...

Just because I'm on 10.4, it does not mean that it's the coolest version. I boot everyday without an issue, but the system does not fail to crash in the middle of work at least 4 times per week.

Just so that you'll know, I do the following on my Inspiron 1150:

C# Mono
PHP - LAMP
DreamWeaver 8 - on Wine
GIMP
Open Office 3.x
Skype
C - G++ compiler
Brasero
RealPlayer 11
Flashplayer - plugin for FF
Chrome
Skype
GnomeBaker
TuxMath + TuxTyping - for my kids
FileZilla
ClamAV

All the best with your upgrade/fix.

---

### Post by owners4life5 on 2010-07-23
thank you for all of your help... but i think i.m just going to do a fresh install of lucid again... sorry for all of the trouble

---

### Post by vpatanka on 2010-09-26
This was really helpful. I followed the steps and was able to upgrade my linux kernel to fix the low-graphics mode problem for good. thanks a lot for a useful posting

---

### Post by itsols on 2010-09-26
It's good to know you benefited. Now here's something you ought to do...

In the event the system reports the problem again, please do let us know. And also let us know what hardware configuration you're using, stating the graphics devices in particular.

And, you're welcome!

---

