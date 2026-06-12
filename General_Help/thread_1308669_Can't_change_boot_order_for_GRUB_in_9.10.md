---
title: "Can't change boot order for GRUB in 9.10"
date: 2009-10-31
forum: General Help
---

### Post by mxcrowe on 2009-10-31
I found several links explaining how to do this - for example:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)
But I cannot find any such file as /boot/grub/menu.lst on my installation of 9.10.  I just want to change the OS boot order, but cannot find any instructions beyond those that refer to a file that I can't find!

---

### Post by RedSquirrel on 2009-10-31
9.10 uses grub2. See this [guide]("http://ubuntuforums.org/showthread.php?t=1195275").

Edit: This one might be a bit better: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by mxcrowe on 2009-10-31
Thanks Red.  That definitely helped.  I changed my default to "saved", which seemed like the best option for me.  Should default to the last OS I booted with.  However, I tested booting to Win7 and then restarting, and it still defaults to Ubuntu in the first slot.  Not sure what I'm doing wrong because the file is definitely changed.

---

### Post by Chris0134 on 2009-10-31
I'm no expert, but me thinks the above is for grub 1, I did that above procedure for my jaunty install with no problems.  The new grub is far more dynamic, and far more complex. From what I've read that file is created anew on every boot, editing it is useless.

---

### Post by autocrosser on 2009-10-31
Look in Tutorials & Tips--there is a very good grub2 tutorial there.....

---

### Post by mxcrowe on 2009-11-01
Willee-Nillee suggested (on a separate post) downloading the startup manager via synaptic.  This worked great for me whereas making changes to the /etc/default/grub file did nothing, despite what the documentation indicates.  Thanks Willee-Nillee!

---

### Post by kaspin on 2009-11-02
As a pensioner knocking on to 70, I haven't got much time to read all these links.... So if you want to save some time, this is what you do in Ubuntu 9.10:

To change the boot order at start up in Ubuntu 9.10, first check, on boot up, how many lines of choice there are (including the "other operation systems" line) .
In a terminal, type

sudo gedit /etc/default/grub   {enter}

find the line

GRUB_DEFAULT=0

If you don't want to boot by default into Ubuntu, and say you had 5 lines of choice in all when you booted up, and Windows was the last line, you will have to change 0 to 4 to boot by default into Windows.

While you're there, if you want to reduce boot up time, find the line

GRUB_TIMEOUT="x"   
(where x is a number - probably 10)

x indicates how many seconds Grub waits before booting. If you change x from 10 to 5 you will save 5 seconds boot time.

After that, save the file.

Finally, to incorporate these changes in the system, type in a terminal

sudo update-grub             {enter}

Now, cross your fingers and reboot.................Kaspin

---

### Post by autocrosser on 2009-11-02
That only works if your are using Grub--9.10 is using 2 flavors --Grub & Grub2  It depends on if you upgraded (stay with Grub) or did a fresh install (you get the default Grub2). Everyone will be getting Grub2 with 10.04, so this is a transitional period.

---

### Post by Uncle Spellbinder on 2009-11-02
> **mxcrowe said:**
> Willee-Nillee suggested (on a separate post) downloading the startup manager via synaptic.  This worked great for me whereas making changes to the /etc/default/grub file did nothing, despite what the documentation indicates.  Thanks Willee-Nillee!

Indeed. In Synaptic, search *startupmanager*, install it.............

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/StartUpManager.jpg[/IMG]

---

### Post by kaspin on 2009-11-02
Hi Autocrosser,
Mine was a fresh install of 9.10, and I altered grub 2 as far as I know. The file menu.lst (used to change the order on previous versions) is as empty as my bank account...........Kaspin

---

### Post by smithintaiwan on 2009-12-12
Thanks Kaspin,
That worked fine for me and mine was also a fresh install of 9.10, netbook remix.

---

### Post by Pipps on 2010-01-03
Three cheers to Kaspin! But more importantly, three cheers to the Ubuntu Startup Manager!

Novice Ubuntu users have waited a long time for it. I am so glad to have it now especially since the advent of GRUB2! :)

---

### Post by boosterjet on 2010-01-03
Well it does not work on mine - see my thread a few entries below

---

