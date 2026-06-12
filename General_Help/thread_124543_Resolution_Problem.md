---
title: "Resolution Problem"
date: 2006-02-01
forum: General Help
---

### Post by Bakuryu on 2006-02-01
I trying to run Ubuntu on Virtual PC, but the resolution keeps getting messed up no matter what I set it to before it boots up.

---

### Post by frodon on 2006-02-02
Could you give us more informations about your problem ? , here is a nice guide with a lot of useful informations : [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by blakkandekka on 2006-02-02
It's because Virtual PC doesn't support a 24 bit colour depth, which for some reason is what the Ubuntu installer defaults to.  To fix it:

[LIST]
[*]Start the Ubuntu VPC session and press ESC when Grub (the Linux bootloader) appears.  Select Recovery mode and press return.  Ubuntu should then boot to a root command prompt. (I'm a bit of a noob, but this strikes me as a pretty big security hole.  I can't get administrator access to my Windows box by pressing one key on boot, but I digress...)

[*]You need to edit the xorg configuration file.  Even though it's only VPC I should copy the file first

**cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup**


[*]Then edit the file

**pico /etc/X11/xorg.conf**


[*]Page down to Section "Screen" and change the DefaultDepth value from 24 to 16 (VPC should also support 32-bit, but I can't make it work).

[*]ctrl-x to exit ('Y' to save the file when prompted), type 'reboot' at the prompt to restart Ubuntu and it should work.

[/LIST]

Phil

---

### Post by Bakuryu on 2006-02-02
Hitting ESC while in the bootload does nothing =\

---

### Post by blakkandekka on 2006-02-02
[QUOTE=Bakuryu]Hitting ESC while in the bootload does nothing =\[/QUOTE]
Wait until the initial POST screen has gone (maybe 2 or 3 seconds).  You should see a line of text saying 'Grub Loading Stage1.5'.  Press ESC when you see it.

---

### Post by Bakuryu on 2006-02-03
Im not sure I know what your talking about, maybe a screenshot would help?

---

### Post by blakkandekka on 2006-02-03
[QUOTE=Bakuryu]Im not sure I know what your talking about, maybe a screenshot would help?[/QUOTE]

Sorry, my VPC machine is at home, so you'll have to wait until this evening for a screenshot.

I'm running Microsoft Virtual PC 2004 on XP Pro and the VPC session runs Ubuntu 5.10.  256MB of memory assigned to the session.  I'm assuming that you've run the Ubuntu installation program in a virtual PC session and it's installed itself OK, but the graphical login screen won't display after it boots.  If you can't run the install program then that's a different problem.

Start Virtual PC fom the Windows 'All Programs' menu, you should see the VPC Console with your Ubuntu sesion listed.  Select Ubuntu and click on the Start button.  A text mode window should appear, the first few seconds of which should be the virtual PC session listing its memory, video, virtual disks etc - that the POST (Power On Self Test).  After that's run you should see a line of text beginning with 'Grub' appear.  That's when you hit ESC.

---

### Post by Bakuryu on 2006-02-04
Sorry I forgot to mention Im running the live version no installing, i usually have trouble when trying to install things with VPC.

---

### Post by blakkandekka on 2006-02-04
[QUOTE=Bakuryu]Sorry I forgot to mention Im running the live version no installing.[/QUOTE]

Sorry, I've no experience of that, but the problem is probably the same - you need to edit xorg.conf and change the depth to 16-bit.  Try getting a console by using Ctrl-Alt-F1, editing the file and then **/etc/init.d/gdm start** to restart Gnome.

> i usually have trouble when trying to install things with VPC

Sounds like you're having trouble using the live CD too, so you might as well put the effort into a full install:-D

---

### Post by Bakuryu on 2006-02-05
So close, I went into /etc/X11/xorg.conf and change 24 to 16, but it wont right the changes >< what am I doing wrong?

---

### Post by blakkandekka on 2006-02-05
[QUOTE=Bakuryu]So close, I went into /etc/X11/xorg.conf and change 24 to 16, but it wont right the changes >< what am I doing wrong?[/QUOTE]
Do you mean that Pico won't write to the file?  It could be that you're not editing as root - try **sudo pico /etc/X11/xorg.conf** and entering your password.  I'm not sure what might be happening if you're running the live CD under Virtual PC though, I'll have a go with it to see what happens.

---

### Post by blakkandekka on 2006-02-05
I've just had a go with the Live CD - very, very slow (15 minutes to boot) and I couldn't seem to get a console from the wonky graphical login screen, so not much success there.

Unless you have a very good reason for running it under VPC you're going to be much better off either doing a full Ubuntu install under VPC and editing xorg.conf as described above, or just running the Live CD on your actual (not virtual) PC - it won't touch the installed OS and it'll be about 10 times quicker.

The Ubuntu Live CD is very slow booting compared with [Knoppix]("http://www.knoppix.org/"), so if you have to go the VPC route I should have a go with that, though it may not solve the screen resolution problem as it's also based on Debian.

---

### Post by Bakuryu on 2006-02-05
It sorta worked but its still black and white and stretched im going to try the install one on VPC, I just want to try it out before I restart my computer to use it.

---

### Post by Bakuryu on 2006-02-06
Ok i did the install version same problem went in to etc/X11/xorg.conf and changed it to 16 it looks a little better but it black and white and a little stretch how do I fix?

---

### Post by Ptero-4 on 2006-02-06
> 
I'm running Microsoft Virtual PC 2004 on XP Pro and the VPC session runs Ubuntu 5.10. 256MB of memory assigned to the session.

Are you really using Ubuntu in M$ V$PC? You must be really clever to pull that off.
I mean, using a non-M$ OS in the M$ version of VPC is AFAIK near impossible b/c of limitations that M$ have intentionally put into V$PC, and to be able to even boot it you have to do some serious hacking in the V$PC app and libraries. If you're using a PC you should consider Qemu-fast or VMware, they're standard PC emulation software which means that the PC emulator doesn't try to keep you from using non-M$ OS's on it. Also those two emulators use raw virtualization on the x86 Platform so the speed of the emulated session is pretty close to the speed of your PC. Now if you're on a Mac with PowerPC CPU, you won't be able to use qemu-fast or VMware due to the difference in CPU type in your box. But I got the connectix VPC 6.0.1 installer package (That is the real VPC, not the PIECE OF CRAP thing M$ calls VPC) for OS9/OSX in a CD if you want it. It's not as fast as qemu-fast or VMware, but it's faster than M$ V$PC and as standard as qemu(-fast)/VMware. Or if you got a x86 Mac. You can use qemu-fast (VMware developers haven't yet released VMware for x86 OSX, but it can be done).

---

### Post by Bakuryu on 2006-02-06
Ok.... what do you recommend? Ive gotten other linux distros to work fine with MS VPC so why not Ubuntu?

---

### Post by Ptero-4 on 2006-02-07
My recomendation for both blakkandekka and Bakuryu is that you use the Qemu-fast PC emulator or the VMware one instead of M$ V$PC. And since you're in x86 boxes those PC emulators can run at native speeds (which the M$ one doesn't AFAIK). The reason for switching emulator software is that running Linux in qemu-fast and VMware is relativelly easy while in M$ V$PC you need to do lots of reverse enginnering just to figure out how to trick the emulator to allow you to boot a "not supported" (non-M$) OS.

---

### Post by Bakuryu on 2006-02-08
Although VMware or w/e works great with Ubuntu or course when its pre desigend for it, Id like to use VPC because it takes up less room while VM needs like 1.52 gb files the VPC only uses and ISO which is like 600 MB. So what can I do to make it work on VPC?

---

### Post by Ptero-4 on 2006-02-09
Nothing. Booting linux on V$PC is harder than Booting OS9 in an Intel-Mac.
M$ has encoded instructions into the M$ V$PC software to prevent the V$PC users from using non-M$ OS's on it. So the short answer is no. You can't use ubuntu in V$PC. If you want try it but you won't succed on that one.

---

### Post by Ebantu on 2006-02-09
Hey fellas, Newb here.. don't mean to hijack this thread, but i'm having the exact same problem as "Bakuryu" screen res is messed up, streched with only a few colors. Im not using any emulator or a live cd to run ubuntu. This problem started when i first installed SUSE 10.0, screen was fine i was happy with how everything worked, couple days later, I boot SUSE with no changed made to anything, and the screen res. was all screwed up. I've installed Ubuntu 5.1 now and i still have the same problem, couple buddies of mine tried to fix this for me by telling me what to edit in the xorg.conf file but nothin so far has helped. This is really weird and very frustrating..

Any other ideas? besides the things mentioned above... :-k 

much thanks,

---

### Post by Ptero-4 on 2006-02-10
How recent is your computer?
What specs it have?
Do you have Windoze installed next to Linux?

I ask b/c recent computers tend to have some nasty BIOS "features" designed to block your ability of using non-M$ apps or OS's.
Also sometimes those "features" can come disabled or be overriden, but sometimes a Windoze "critical update" actually updates, or enables those nasty "features" causing that an already working Linux stops working suddenly.

---

### Post by Ebantu on 2006-02-11
I do have windows installed as a 2nd OS.

PC is pretty recent, just built it couple months ago.

Specs are:

Asus A8N32-SLI-Deluxe - Mobo
Opteron 170 Dual Core - Proc
x2 Nvidia Geforce 6800GS in SLI
x2 1gb Patriot DDR-RAM @ 400mhz

As far as I remember I haven't installed any updates in Windowz before or after this happened.

Any known specific options in BIOS that can cause this?

---

### Post by Ebantu on 2006-02-11
Problem solved! thanks anyway guys.

This helped
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=apt+source](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=apt+source)

Method one i believe is what did the trick, thanks to a buddy of mine that helped me through the proccess, since im a major newb when it comes to linux.

---

### Post by funkythumb on 2006-02-22
The default *ubuntu *login doesn't have the privileges to change the file.

Type:  **sudo vi /etc/X11/xorg.conf ** (to use vi editor)  or...
**sudo nano /etc/X11/xorg.conf** (to use nano editor) :cool:

---

### Post by funkythumb on 2006-02-22
[QUOTE=Bakuryu]So close, I went into /etc/X11/xorg.conf and change 24 to 16, but it wont right the changes >< what am I doing wrong?[/QUOTE]


The default *ubuntu *(or whatever) login doesn't have the privileges to change the file.

Type:  **sudo vi /etc/X11/xorg.conf ** (to use vi editor)  or...
**sudo nano /etc/X11/xorg.conf** (to use nano editor) :cool:

---

### Post by altisssimo on 2006-03-24
[QUOTE=blakkandekka]It's because Virtual PC doesn't support a 24 bit colour depth, which for some reason is what the Ubuntu installer defaults to.  To fix it:

[LIST]
[*]Start the Ubuntu VPC session and press ESC when Grub (the Linux bootloader) appears.  Select Recovery mode and press return.  Ubuntu should then boot to a root command prompt. 

[*]You need to edit the xorg configuration file.  Even though it's only VPC I should copy the file first

**cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup**


[*]Then edit the file

**pico /etc/X11/xorg.conf**


[*]Page down to Section "Screen" and change the DefaultDepth value from 24 to 16 (VPC should also support 32-bit, but I can't make it work).

[*]ctrl-x to exit ('Y' to save the file when prompted), type 'reboot' at the prompt to restart Ubuntu and it should work.

[/LIST]

Phil[/QUOTE]

This worked great for me, although I would love to get other screen resolutions in addition to the default 3 options (e.g. 1680x1050). Thanks Phil, good workaround.

---

### Post by valius on 2006-04-17
Thank You. The problem really was  with color depth. :)

---

