---
title: "HUGE problem with GUI"
date: 2011-11-11
forum: General Help
---

### Post by kswix on 2011-11-11
Hi!

I have ubuntu 11.04 with gnome. Recently I added two new users, then reboot and catch a big error.

My GUI not works. On Ctrl+Alt+F7 I see black screen. But also I can't login via text-mode (I don't know why).

Teoretically, I can trying to work with xorg(I think problem with it) manually, but I don't know how.

Regards, kswix

---

### Post by kswix on 2011-11-12
bump!

---

### Post by kswix on 2011-11-12
When I try start failsafeX in recovery, then I catch this:

```

md5sum: /etc/X11/xorg.conf: no such file or directory
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe --/usr/bin/X -br -once -config /etc/X11/xorg.conf ...
/tmp/.X11 - unix has suspicious mode (not 1777) or is not a directory

```

Content of my /etc/X11/xorg.conf is:
```

Section "Device"
 Identifier "Configured Video Service"
 Driver "fbdev"
EndSection

Section "Monitor"
 Identifier "Configred Monitor"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
EndSection

```

So, I tried to copy xorg.conf from my netbook, but I can't find xorg.conf here (I'm on 10.10). Here's my ls /etc/X11 -a result:
> .                        fonts    Xreset      Xsession.options
..                       rgb.txt  Xreset.d    Xwrapper.config
app-defaults             X        Xresources
cursors                  xinit    Xsession
default-display-manager  xkb      Xsession.d


---

### Post by kswix on 2011-11-12
bump!

---

### Post by kswix on 2011-11-13
bump!

---

### Post by kswix on 2011-11-13
bump! I really don't know what to do.

I copied files from my netbook to /etc/X11 on my comp, but it still don't work!

---

### Post by kswix on 2011-11-13
bump!

---

### Post by kswix on 2011-11-14
bump!

---

### Post by Cabalbl4 on 2011-11-14
What graphic card do you use? And which drivers?

---

### Post by kswix on 2011-11-14
**Cabalbl4**, thanks for answer!

> NVIDIA GeForce G200 Graphics with 320MB integrated shared graphics memory[http://www.amazon.com/HP-TouchSmart-600-1050-23-Inch-Desktop/dp/B002ONCDWY](http://www.amazon.com/HP-TouchSmart-600-1050-23-Inch-Desktop/dp/B002ONCDWY)** - **here is my comp.

I worked with Ubuntu on it about 6 months, but these problems was started when I added new user (I don't know why)

---

### Post by Cabalbl4 on 2011-11-14
As far as I can understand you have nvidia card with "out of the box" driver.

Once I have had a very similar situation with an ATI card. The GUI crashed every boot without any clue why. The thing that helped me was a complete driver reinstall.

I am not very familiar with nvidia, but I think you should try to boot in recovery mode ("single" kernel option), then use root console, and try this:
dpkg-reconfigure nvidia-current 
then reboot. This will reconfigure the driver, generating new xorg.conf.

I am not very sure about the package name, unfortunately.

Also, which display manager do you use? GDM or KDM?
If you do not know, try to setup gdm - "dpkg-reconfigure gdm" as root.

---

### Post by kswix on 2011-11-14
So, I have a second trouble (I write it in start of topic): I can't login in command-line(Ctrl+Alt+F1), I don't know why(I encrypted /home folders, maybe by this?).

How I can stay in manual recovery mode without signing in as root? (Sometimes Ubuntu offers me 'manual recovery mode' in the booting).

---

### Post by Cabalbl4 on 2011-11-14
If you have access to grub, try to pass these options to the kernel 
"single init=/bin/bash". Then you should login as a root in console mode.

Btw I think you should work as root to fix this, not as user.

---

### Post by kswix on 2011-11-14
> "single init=/bin/bash"So, must be *single init=/bin/bash* in quotes?

When I print 'e' in GRUB, I moved to "change commands before booting".

If I puts without quotes in any place in text, I see something like "unknown error single. Press any key...."
If expression puts 'in quotes, I see nothin if them in beginning of the text or "could not write bytes: Broken pipe" on Ctrl+Alt+F7 if expression in the end.

So, when GRUB commands are changes, It's pretty simple to go to manual recovery mode: I start loading, then "C" to cancel scanning of the disk drives errors and then M to enter to manual recovery as root. Other problem: pass to root not valid! So, I catch the message "Root filesystem check failed"

---

### Post by Cabalbl4 on 2011-11-14
It should look like 
linux /boot/vmlinuz-2.6.32-35-generic root=UUID=0aa672d1-6639-4da9-a808-897c7bba001e ro single init=/bin/bash

---

### Post by Cabalbl4 on 2011-11-14
this should give root access even with wrong root pass.

---

### Post by kswix on 2011-11-14
> linux /boot/vmlinuz-2.6.32-35-generic root=UUID=0aa672d1-6639-4da9-a808-897c7bba001e ro single init=/bin/bash
It works!

but:
> 
error: unexpectedly disconnected from boot status daemon
bash: cannot set terminal process group(-1): Inappropriate ioct1 for device
bash: no job control for this shell
groups: cannot find name for group ID 0

And I can't put anything to command shell. WTF?

---

### Post by Cabalbl4 on 2011-11-14
Hmm... "Root filesystem check failed" indicates a problem with your filesystem. 

And this output is another proof for that. You need to use fsck on this filesystem using live cd, i suppose.

---

### Post by Cabalbl4 on 2011-11-14
[http://ubuntuforums.org/showthread.php?t=422307&page=2](http://ubuntuforums.org/showthread.php?t=422307&page=2)

This thread is about using fsck. Should help )

---

### Post by kswix on 2011-11-14
So, I run fsck UUID=....

Fixed some inodes change , has a **** FILE SYSTEM WAS MODIFIED *****. Restarted without liveCD. Then logged in with single init=/bin/bash.

But still have the same error:
> error: unexpectedly disconnected from boot status daemon
bash: cannot set terminal process group(-1): Inappropriate ioct1 for device
bash: no job control for this shell
groups: cannot find name for group ID 0 			 		

---

### Post by Cabalbl4 on 2011-11-14
ok, try two things:

1) boot without word "single"
2) boot with single init=/bin/sh

Maybe this will help?

---

### Post by kswix on 2011-11-14
1) With init=/bin/bash (without single) I catch same error.
2) With single init=/bin/sh:
> error: unexpectedly disconnected from boot status daemon
/bin/sh: can't access tty; job control turned off

3) init=/bash/sh (without single) - Kernel panic!

Is it normal that I have 
```
initrd /boot/initrd.img-2.6.32-32-generic
```
after:
```
 			 				linux /boot/vmlinuz-2.6.32-35-generic root=UUID=0aa672d1-6639-4da9-a808-897c7bba001e ro single init=/bin/bash 			 		
```
?

---

### Post by Cabalbl4 on 2011-11-14
Yes, initrd /boot/initrd.img-2.6.32-32-generic is ok.
But it seems that the output device for console is damaged somehow... I suspect a severe filesystem damage or some strange mounting problems (yes, in ubuntu this can be a trouble :( ). 

1) Did you use fsck correctly?

2) There may be some problem with UUID correctness. 
Try to use root=/dev/(your device) 
instead of root=UUID=.....

To get the correct device path you can try to run gparted from life-cd. This can look like /dev/sda3 - where sda3 is your ext partition with ubuntu on it (look for the correct sda number using gparted).

P.S. you may encounter /dev/hda(N) in gparted. This is ok, use /dev/hda(N).

---

### Post by kswix on 2011-11-14
> Try to use root=/dev/(your device) 
instead of root=UUID=.....
Where I must use it?

In loader or in liveCD?

---

### Post by Cabalbl4 on 2011-11-15
You should use it in GRUB to fix incorrect UUID addressing (if this is a problem).

---

### Post by kswix on 2011-11-15
When I try with root=/dev/sda1 with single init=/bin/bash or without it, I get the same situations with UUID

I think, maybe it will simpler when I'll reinstall Ubuntu? But how I can get the secured data from encrypted folder?

---

### Post by Cabalbl4 on 2011-11-15
Well, reinstall may be an option. When I did some search on your problem, there was a lot of mentioning of damaged console symlinks. I do not know how to restore them correctly in your ubuntu version, so if you can find the way to restore console without reinstall (by adding needed symlinks) - try it first. If this step is not available, I suggest you copy all the data needed and do a drive format.

About encrypted folders - I have never used them :(
But this thread should help you retrieve your data: [http://ubuntuforums.org/showthread.php?t=1337693](http://ubuntuforums.org/showthread.php?t=1337693)

And one more thing. Simple "useradd" can not cause such damage to your system. There should be another reason, I think. An incorrect shutdown (power loss etc.), some system software misbehavior or hardware failure.

---

### Post by kswix on 2011-11-15
> Well, reinstall may be an option. When I did some search on your  problem, there was a lot of mentioning of damaged console symlinks. I do  not know how to restore them correctly in your ubuntu version, so if  you can find the way to restore console without reinstall (by adding  needed symlinks) - try it first. If this step is not available, I  suggest you copy all the data needed and do a drive format.

I think I don't know what is symlink.

> About encrypted folders - I have never used them :sad:
But this thread should help you retrieve your data: [http://ubuntuforums.org/showthread.php?t=1337693](http://ubuntuforums.org/showthread.php?t=1337693)
So, I work with them now. I answer here where will have success.

> And one more thing. Simple "useradd" can not cause such damage to your  system. There should be another reason, I think. An incorrect shutdown  (power loss etc.), some system software misbehavior or hardware failure. 	
I understand this, thanks.

---

### Post by Cabalbl4 on 2011-11-15
A symlink is a "symbolic link" - a way to connect files with each other. A bit similar with windows link files, which point to an .exe file from another location (e.g. desktop). In unix, symlinks are used to redirect output from one device to another and many other things.
However, if you are not familiar with them - it is better to do what you know how to do :)

Good luck in recovering your data.

---

### Post by Cabalbl4 on 2011-11-15
I am an idiot. :) Right now I have understood one thing - we may be chasing a wrong error.
While trying to fix shell and other stuff I skipped a very interesting message:
"groups: cannot find name for group ID 0"
It means that your root access group can not be found in /etc/group
ensure that the first line of this file is
```
root:x:0:
```

---

### Post by kswix on 2011-11-15
> I am an idiot. :smile: Right now I have understood one thing - we may be chasing a wrong error.
While trying to fix shell and other stuff I skipped a very interesting message:
"groups: cannot find name for group ID 0"
It means that your root access group can not be found in /etc/group
ensure that the first line of this file isSo, I started to learn about /etc/shadow et.c.

1) Is it normal that's my /etc/shadow file consist of lines like this:
```
root:x:0:0:root:/root:/bin/bash
agx:x:1001:1002:A something other user,,,,::/home/agx:/bin/bash

```

2) My /etc/group file is empty?

Why this situation was arise?
How I can change these files?

---

### Post by Cabalbl4 on 2011-11-15
> **kswix said:**
> So, I started to learn about /etc/shadow et.c.

1) Is it normal that's my /etc/shadow file consist of lines like this:
```
root:x:0:0:root:/root:/bin/bash
agx:x:1001:1002:A something other user,,,,::/home/agx:/bin/bash

```

2) My /etc/group file is empty?

Why this situation was arise?
How I can change these files?

Wow... this is kinda... unexpected.

So, we seem to have a problem with at least 
/etc/shadow
/etc/group

I don't know why, but somehow your user adding mixed all the userdata, including that one for root.

```
sudo cat /etc/shadow
 
root:!:14930:0:99999:7:::
daemon:*:14728:0:99999:7:::
bin:*:14728:0:99999:7:::
sys:*:14728:0:99999:7:::
sync:*:14728:0:99999:7:::
...
and all users with passwords come here
```

For more info read here: [http://www.cyberciti.biz/faq/understanding-etcshadow-file/](http://www.cyberciti.biz/faq/understanding-etcshadow-file/)

The way your /etc/shadow looks now is more like /etc/passwd

This is user configuration related error... but I just cannot understand HOW.

Well... you may try to get root access then by the following (only for test purposes, I do not know if it will work):
backup
/etc/passwd
/etc/shadow
/etc/group

modify /etc/passwd
it should only contain:
```
root:x:0:0:root:/root:/bin/bash

```

modify /etc/shadow
it should only contain:
```
root:!:14930:0:99999:7:::

```

modify /etc/group
it should only contain:
```
root:x:0:

```

it is just for test. Boot with single init=/bin/bash
I wonder if you will have a working terminal. Revert everything otherwise.

---

### Post by Cabalbl4 on 2011-11-15
And by the way... maybe there is any backup left from previous editor?
Look for
/etc/group~
/etc/passwd~
/etc/shadow~

A small chance always exist :)

---

### Post by Cabalbl4 on 2011-11-15
And the final thing. I do not know the way to regenerate these files. I do not think it really exist one. If you can not find backups for these files, you should backup your own data and reinstall. Copying these from another system MAY help, but there is a very big probability that many packages will be broken because of incorrect user settings.

You may also try to look here... 
[http://ubuntuforums.org/showthread.php?t=1078462](http://ubuntuforums.org/showthread.php?t=1078462)

> And by the way... maybe there is any backup left from previous editor?
Look for
/etc/group~
/etc/passwd~
/etc/shadow~


also, there may be another backup files, use:
ls -la /etc/group*
ls -la /etc/shadow*
ls -la /etc/passwd*

the "~" symbol may differ, "-" for example

---

### Post by kswix on 2011-11-15
Hooray!

My passwd, group, shadow files exists and valid! Only one trouble - root password, but it is the same as one of user password, and I just copy it from to root.

Now I need cp files?

---

### Post by Cabalbl4 on 2011-11-15
> **kswix said:**
> Hooray!

My passwd, group, shadow files exists and valid! Only one trouble - root password, but it is the same as one of user password, and I just copy it from to root.

Now I need cp files?

**_NOO._** Do not copy root password. Root account in ubuntu is not enabled by default and has no password. By sudo or init=/bin/bash you are forcing root with no password check. But you can not actually login as a root on ubuntu normal way.
Use the strings I have provided in posts earlier, they are from my working system.

But if they are valid, why do you have troubles with console then?

---

### Post by kswix on 2011-11-15
> But if they are valid, why do you have troubles with console then? 	
So, I haven't troubles with console and with graphics now. Thanks, all works! :P I write you via 

But, some problem: when I print Ctrl+Alt+L, I have a display block. When I try to unblock it, authentication fail. I need to click "Switch user" button and then write password, only then have a successful login. How I can avoid this?

---

### Post by Cabalbl4 on 2011-11-15
> **kswix said:**
> So, I haven't troubles with console and with graphics now. Thanks, all works! :P I write you via 

But, some problem: when I print Ctrl+Alt+L, I have a display block. When I try to unblock it, authentication fail. I need to click "Switch user" button and then write password, only then have a successful login. How I can avoid this?

This seems to be an open bug
[https://answers.launchpad.net/ubuntu/+source/gnome-screensaver/+question/113394](https://answers.launchpad.net/ubuntu/+source/gnome-screensaver/+question/113394)

By the way, you may mark this thread as solved and start another one, because now it is only gnome-screensaver related (I think :) )

---

### Post by kswix on 2011-11-15
Yes, of course, you right! ;)

---

