---
title: "Slow Startup, Plymouth not showing, slow desktop load"
date: 2010-05-03
forum: General Help
---

### Post by raffaele181188 on 2010-05-03
I'm an Ubuntu user since Jaunty, and I've always upgraded my system (NOT fresh install). Everything went fine, but yesterday I upgraded to Lucid. My only concern -for now- deals with startup time. I'm a desktop user (Core2@3GHz) so I think I should boot in less than 10 seconds. Anyway, **boot time is 30 seconds** - not too much, but there is definetly something wrong with tools I don't know (ureadahead, plymouth, etc.). Attached is my bootchart: can anyone explain me what's wrong?

Also, I don't even see a plymouth Ubuntu themed bootsplash: I only see a blank (black) screen standing for seconds, then I see the bootsplash for less then half a second, then GDM appears :S Not crucial -I know- but how can I fix it? (I don't know if it's related, but I can see the animation at shutdown)

Finally, GNOME desktop takes too long to load. I don't know why, but there are 15/30 seconds in between login sound and a usable desktop (with panels and icons, I mean). Any idea?

Please help me, I don't want to do a fresh install. Boot speed is not a dial with desktops - I know - but it can be a symptom that my system is a bit a messy (and I don't like it, since I installed Jaunty less then 1 year ago). (!Forgot! I also installed grub2 by hand :S)

Cheers :D

[--->> See bootchart <<---]("http://imagebin.ca/view/loTGTGr.html")

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
/etc/default/grub

---

### Post by jerenept on 2010-05-03
Same with me :( The only solution is a fresh install as upgrading from karmic leaves a lot of legacy stuff behind (HAL) etc. These slow down the boot and desktop load times.

---

### Post by melkespreng on 2010-05-03
Saw in another thread that slow startup can be fixed by disabling floppy disks in bios. I did and it works. When it comes to plymouth it has loads of threads and seems to have it's share of issues. 

Just be patient with it. :)

---

### Post by afrodeity on 2010-05-20
Some of the fixes in [lucid workarounds]("http://ubuntuforums.org/showthread.php?t=1469475") helped me with low res startup, black screen and blinking curser wait etc, but loading of desktop is painful.

---

### Post by BrockStrongo on 2010-08-16
I had this problem too. To fix it, or at least workaround it, I made plymouth splash screen load earlier by entering these commands in terminal

echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
then
update-initramfs -u

To speed up the boot process I created a boot profile by editing grub

sudo gedit /etc/default/grub

make this line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

look like this GRUB_CMDLINE_LINUX_DEFAULT="quiet splash profile"

then  sudo update-grub2

reboot

edit grub again to remove the word profile where you added it and run update-grub2 again.

I realize this is an old thread but wanted to share what helped me.

---

### Post by Rawnblade on 2011-02-08
> **BrockStrongo said:**
> I had this problem too. To fix it, or at least workaround it, I made plymouth splash screen load earlier by entering these commands in terminal

echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
then
update-initramfs -u

To speed up the boot process I created a boot profile by editing grub

sudo gedit /etc/default/grub

make this line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

look like this GRUB_CMDLINE_LINUX_DEFAULT="quiet splash profile"

then  sudo update-grub2

reboot

edit grub again to remove the word profile where you added it and run update-grub2 again.

I realize this is an old thread but wanted to share what helped me.


Thanks, this worked for me. All I needed were the first two commands.

---

### Post by herbie643 on 2011-03-18
Just leaving a comment to the effect that even if you don't have the /etc/initramfs-tools/conf.d/splash file, just execute and it will create one.  That did it for my computer.  Toshiba Satellite L355-S7902 Dual core.   I also installed the Intel Microcode.
System is way faster now.   Boots were about 55sec, now 35.

---

### Post by meconio on 2011-11-01
> **BrockStrongo said:**
> I had this problem too. To fix it, or at least workaround it, I made plymouth splash screen load earlier by entering these commands in terminal

echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
then
update-initramfs -u

To speed up the boot process I created a boot profile by editing grub

sudo gedit /etc/default/grub

make this line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

look like this GRUB_CMDLINE_LINUX_DEFAULT="quiet splash profile"

then  sudo update-grub2

reboot

edit grub again to remove the word profile where you added it and run update-grub2 again.

I realize this is an old thread but wanted to share what helped me.

Just in case someone gets the permission denied message while entering the above lines, you should try them as a root user to do that just type:
#sudo su
then you type your password and then you do paste the lines.

---

