---
title: "Ctrl-alt-f1 ... f6 shows black screen"
date: 2010-01-27
forum: General Help
---

### Post by lordskid on 2010-01-27
I seem to be getting a blank screen when I press ctrl-alt-f2

As the first thing is always the login prompt, I tried to login and did an ls > dummy.txt followed by a whoami >> dummy.txt

next I checked my home directory for the file dummy.txt and inside is the output of ls and woami on my home directory.

so I believe the console is there it is either the background and foreground colors are the same or maybe the fonts are too small, anyway can anyone help me get my tty up and running again? 

Thanks.

---

### Post by omeraygor on 2010-01-27
hi. They are terminal screen without x-window. when u press ctrl-alt-f7, can go back your working window.

---

### Post by alwayshere on 2010-01-27
I have no idea what your on about here ????

---

### Post by lordskid on 2010-01-27
> **omeraygor said:**
> hi. They are terminal screen without x-window. when u press ctrl-alt-f7, can go back your working window.

yeah but I need at least one tty to do some stuff.

---

### Post by lordskid on 2010-01-27
> **alwayshere said:**
> I have no idea what your on about here ????

sorry if I am being vague. well I used to have a functioning ctrl-alt-f2 where it will show me white text on black background. ask me to login and gives me a console outside of X windows. 

Only recently it seems to have disappeared or the text does not show I only get the black background.

---

### Post by omeraygor on 2010-01-27
i understand clearly now. &#304;t is interesting. i pressed ctrl-alt-f2 then i logged in. my terminal is working. it seems.

---

### Post by lordskid on 2010-01-27
sorry for my speech impediment. what I mean is I only get a blank screen instead of the normal console.

---

### Post by rnerwein on 2010-01-27
hi 
it looks like every thing is working. your ls and whoami is working only you got no echo on your tty.
try following after login:
stty sane  ( better ? )
stty echo  
may be this help you
ciao

---

### Post by lordskid on 2010-01-27
> **rnerwein said:**
> hi 
it looks like every thing is working. your ls and whoami is working only you got no echo on your tty.
try following after login:
stty sane  ( better ? )
stty echo  
may be this help you
ciao

I tried this but it didn't change anything. I tried stty > fname

saved "speed 38400 baud; line = 0;" to fname

---

### Post by prshah on 2010-01-27
> **lordskid said:**
> I seem to be getting a blank screen when I press ctrl-alt-f2

hi please see [[SOLVED] Ctrl+Alt+F1 doesn't open a new shell]("http://ubuntuforums.org/showpost.php?p=7973082&postcount=3") for a possible solution.

---

### Post by lordskid on 2010-01-27
> **prshah said:**
> hi please see [[SOLVED] Ctrl+Alt+F1 doesn't open a new shell]("http://ubuntuforums.org/showpost.php?p=7973082&postcount=3") for a possible solution.

thanks will try.

edit:

well I tried I edited grub.cfg and added the vga=ask kernel parameter, when I reboot I got an error saying the vga=ask parameter is no longer supported. I will try using an old kernel for now. and see if it works.

---

### Post by prshah on 2010-01-27
> **lordskid said:**
> I got an error saying the vga=ask parameter is no longer supported. I will try using an old kernel for now

No please don't do this. I will try to think of something else and post back here if I have any ideas.

---

### Post by rnerwein on 2010-01-27
hi welcome in the club
i want to figure out wat's my line discipline is. switched to console using cltr alt f1 (f2 ..) and what a surprise - i have the same dilema now - even my monitor is realy disconnected but i can come back with f7. i'm sure it works before (running 9.10 karmic koala). must came with an update.
ups --> never change a runing system :-)
ciao
i forgot --> the getty processes are running:
root      1316     1  0 09:35 tty4     00:00:00 /sbin/getty -8 38400 tty4
root      1319     1  0 09:35 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1342     1  0 09:35 tty3     00:00:00 /sbin/getty -8 38400 tty3
root      1347     1  0 09:35 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1998     1  0 09:35 tty1     00:00:00 /sbin/getty -8 38400 tty1
root      4252     1  0 13:31 tty2     00:00:00 /sbin/getty -8 38400 tty2

---

### Post by lordskid on 2010-01-27
same here too, I am trying to compare my laptop packages with my netbook packages, hoping to isolate what package or hopefully it is just a driver.

I am now trying to find a software to compare....

edit:
trying meld diffviewer now

edit2: no luck I might just reinstall, it is the quicker way always...

---

### Post by lordskid on 2010-02-02
I believe now that it has something to do with my graphic card driver. I ended up reinstalling ubuntu, everything is okay now.

---

### Post by Reboli_NL on 2010-02-23
Hi there,
I run Xubuntu 9.10 64-bit.
I just don't get a login. Just a blinking cursor.
I checked /et/init/tty1.conf...tty6.conf.
Al seems OK, but I don't get a login prompt.
Here a tty2.conf
> # tty2 - getty
#
# This service maintains a getty on tty2 from the point the system is
# started until it is shut down again.

start on runlevel [23]
stop on runlevel [!23]

respawn
exec /sbin/getty -8 38400 tty2getty does not run. Period.
A re-installing ubuntu might help, but it's a bit strange that it is needed.... right? ;-)

---

### Post by Reboli_NL on 2010-02-23
Ok, I can call 'sudo start tty1', but where is 'tty1'? I only see the config files as described above. Trying to add tty1 to runlevel 2 gets me this:> root@Think-Reboli:~# update-rc.d tty1 2
update-rc.d: /etc/init.d/tty1: file does not existIdeas? :confused:

---

### Post by Reboli_NL on 2010-02-27
Ok, got it re-installed. Problem solved indeed.  
Too weired  ](*,)

---

### Post by BatteryKing on 2010-07-24
I experienced the same problem on the latest 10.04 update.  For me it fouled up just as I was switching around my eth0 interface on my notebook from manual control back to NetworkManager control.  After a couple test reboots I tried to go back to a getty terminal (Ctrl+Alt+FX) to run xdmcp to a more powerful computer through xinit only to get a blinking cursor instead of a login screen.  (I have been relying heavily on xdmcp to a more powerful computer over gig Ethernet to extend the useful service life of my notebook, so this is being used every day and the xinit method does not work directly inside of X, so a getty terminal has to be used.)

Re-installing the coreutils package by itself and rebooting fixed the problem for now.

---

### Post by paalz on 2010-11-07
I also had black screen for Ctrl-Alt-F<1..6> after update from 9.10 to 10.04. My solution to this problem was a variant of approach, described here: [http://ubuntuforums.org/showthread.php?t=999550.]("http://ubuntuforums.org/showthread.php?t=999550")

my video card is ATI radeon 7500 (ibm thinkpad), vesafb did not work for me.
what i did was the following.

1. executing **lsmod** for framebuffer modules loaded gave smth like this
```
user@comp:~$ lsmod | grep fb
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
vga16fb                85280  1 
fb_ddc                  1418  1 vga16fb

```while video modules listed were all radeon-driver associated.
2. i remember i read somere in this forum that the legacy VGA video modes are not compatibe with modern kernel module drivers. this meant we (possibly) cannot use **vga16fb** with radeon kernel mode drivers. (i may be wrong here though)
3. i looked thru **/etc/modprobe.d/blacklist-framebuffer** and found **radeonfb** module among others, so my thought was it should be rather natural to use **radeonfb** instead of **vga16fb**. so i uncommented this blacklist entry, and added vga16fb to the blacklist instead
```
# blacklist radeonfb
blacklist vga16fb
```4. following the [tmastran]("http://ubuntuforums.org/member.php?u=118198")'s post [http://ubuntuforums.org/showthread.php?t=999550](http://ubuntuforums.org/showthread.php?t=999550) i added **radeonfb** to **/etc/initramfs-tools/modules**. i skipped adding **fbcon** cause it was already there when i **lsmod**ed. then i updated initrd image with **sudo update-initramfs -u**.
5. additional changes that i made concerned grub. i added **video=radeonfb:1024x768-32@60** to the grub config (use grub2)
```
GRUB_CMDLINE_LINUX_DEFAULT="video=radeonfb:1024x768-32@60 quiet"
GRUB_CMDLINE_LINUX="radeon.modeset=1"

```i don't know if the second line is needed for **radeonfb** to work, but _maybe_ you will need to add it if you don't have it. so the grub entry now looks like 
```
linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=fe3c4ee6-b8c4-44ba-a9c5-2ea677315d31 ro radeon.modeset=1 video=radeonfb:1024x768-32@60 quiet
```[I]
without this change nothing worked[/I]. although modules where really loaded, but the output text-mode was not displayed by radeonfb. i found this rather accidently at[ http://zadvornykh.com/blog/fedora-plymouth-krasivyi-zagruzchik]("http://zadvornykh.com/blog/fedora-plymouth-krasivyi-zagruzchik") (in russian). you could use **video=radeonfb** simply, but in my case without this explicit resolution setting the text mode was only 640x480px 80x25chars standard placed in the center of the screen.

after rebooting i got working **tty1-6**. although it uses font which is a bit different to the sharp font i used to see before - it looks now more as the native pc text mode. but anyway i can see was i type, even the **nonlatin** characters, which is very-very pleasant.

---

