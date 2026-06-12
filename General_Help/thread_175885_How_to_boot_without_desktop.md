---
title: "How to boot without desktop"
date: 2006-05-14
forum: General Help
---

### Post by msibleyj on 2006-05-14
How can I configure ubuntu to boot up without loading the desktop?  I want to boot directly to the command line.

Thanks,

Mark

---

### Post by Gomek on 2006-05-14
What I did:

Install sysv-rc-conf:
```
sudo apt-get update
sudo apt-get install sysv-rc-conf
```

Launch the tool:
```
sudo sysv-rc-conf
```

Scroll down to **gdm** and turn it off for all the runlevels except 5.

Now, since Ubuntu's default runlevel is 2, you'll boot up with no Gnome.  If you'd like to change the default runlevel to 5 so that you do boot into Gnome, you can edit **/etc/inittab** as follows:

Find the line that says
```
id:2:initdefault:
```
and change it to
```
id:**5**:initdefault:
```

Also, to make sure all your getty's still start, scroll down until you see
```
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6
```
and change it to
```
1:**2345**:respawn:/sbin/getty 38400 tty1
2:**2345**:respawn:/sbin/getty 38400 tty2
3:**2345**:respawn:/sbin/getty 38400 tty3
4:**2345**:respawn:/sbin/getty 38400 tty4
5:**2345**:respawn:/sbin/getty 38400 tty5
6:**2345**:respawn:/sbin/getty 38400 tty6
```

Ta-da!  Hope you find this helpful.

---

### Post by tonyr on 2006-05-14
EDIT: **retracted**. What I suggested used to work for me in Ubuntu, but it doesn't seem to
anymore.  Just go with the previous post from **Gomek**.

---

### Post by msibleyj on 2006-05-14
I'm not able to install sysv-rc-conf:

$sudo apt-get upate
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get: 2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 3B in 1s (3B/s)
Reading package lists...Done

$sudo apt-get install sysv-rc-conf
Reading package lists...
Building dependency tree...
Package sysv-rc-conf is not available, but is referred to by another 
package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

I checked in the package manager in gnome and it shows that sysv-rc is installed.

Mark

---

### Post by Gomek on 2006-05-14
Argh, Dapper...  I'm not sure what they've changed.  I'd assume that it has to do with your repositories, so try changing your **/etc/apt/sources.list** to look like this:

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe **multiverse**
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe **multiverse**
#
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

---

### Post by Phreaker on 2006-05-14
just boot to a runlevel that is not 5

---

### Post by Gomek on 2006-05-14
[QUOTE=Phreaker]just boot to a runlevel that is not 5[/QUOTE]
That doesn't work.  In fact, Ubuntu's default runlevel is 2.

---

### Post by tonyr on 2006-05-14
At this late date I'll re-instate my original post (I think there's some
poetry in there somewhere).

If you just want at console terminal without **gdm** or **kdm**,
after you do a regular login you can do **CTL-ALT-F1**, and you'll go out of 
**gdm/kdm** to a non-gui console terminal with a login prompt.  
Your other login session in **gdm/kdm** is not gone; you can get back there 
with **CTL-ALT-F7**.

If you really want no **gdm/kdm** to ever start, do it **Gomek's** way, or just
edit **/etc/inittab**, change **id:2:initdefault:**  to **id:1:initdefault:**,
and reboot.  It should  boot you into a non-gui terminal in single-user
mode, as root. 

**There are a couple of gotchas here that got me.**.
1. I had to remove my boot splash in **lilo** (maybe **grub** for you).
I don't know if that affects everyone or just my particular machine
graphics /configuration: KDE, nvidia-glx on GeForce2 GO.
2. If you have enabled root login, the boot process will stop and ask you
for the root password.  If you want to disable the root login, use
**sudo passwd -l root**.

Both of these things conspired to stop my boot process from completing for
some reason.  It works now that I removed the boot splash.

There is no difference currently in the choice of values 2,3,4,5 for the **inittab**
modification.  They are there for admins to use for local login management
policies.   That is not to say there won't be differences in the future.  Mandriva
choose a different original arrangment.

---

### Post by msibleyj on 2006-05-14
OK, I got it work Gomek's way, after changing sources.list and changing things with sysv-rc-conf.

But, I now cannot start gnome when I want to from the command line with /etc/init.d/gdm start.  I was hoping that I could start it without rebooting for the times when I occasionally want to use it.

I still get the splash screen when booting.  It is using GRUB.  How do I eliminate that?

Mark

---

### Post by tonyr on 2006-05-14
[QUOTE=msibleyj]
I still get the splash screen when booting.  It is using GRUB.  How do I eliminate that?
Mark[/QUOTE]

In your grub menu **/boot/grub/menu.list** there should be lines that look
more or less like this:
```

kernel        /boot/vmlinuz root=/dev/hdb1 ro console=tty0 quiet splash 

```

Remove the **splash**.

---

### Post by tonyr on 2006-05-14
You might also need to turn off the **usplash** service and comment out
anything in **/boot/grub/menu.list** that says **splashimage**.  I had to
install the **bum** package (**B**oot**U**p **M**anager) to get at 
**usplash** service control.

---

### Post by Gomek on 2006-05-14
To get your desktop to start up once you've booted into the default runlevel 2, try typing in **init 5**.  That'll switch you to runlevel 5.

---

