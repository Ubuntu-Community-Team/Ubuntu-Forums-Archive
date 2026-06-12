---
title: "Can't Automount USB Drive - LXDE Only Installed"
date: 2010-05-05
forum: General Help
---

### Post by DasFox on 2010-05-05
I did a custom install of Ubuntu with the alternate iso, only installing LXDE and I can't get a USB drive to automount, unless I log out of LXDE and log back in with it plugged in, then it works.

I was told to check that dbus, udisks and gvfs are running correct at this point in time from the LXDE developers, but I don't know how to check this.

Any other advise would be appreciated too, to also check for?


THANKS
__

---

### Post by kerry_s on 2010-05-05
try lubuntu, it's minimal+lxde, no need to struggle, they done most of the work.

[http://people.ubuntu.com/~gilir/lubuntu-10.04.iso](http://people.ubuntu.com/~gilir/lubuntu-10.04.iso)

---

### Post by DasFox on 2010-05-05
> **kerry_s said:**
> try lubuntu, it's minimal+lxde, no need to struggle, they done most of the work.

[http://people.ubuntu.com/~gilir/lubuntu-10.04.iso]("http://people.ubuntu.com/%7Egilir/lubuntu-10.04.iso")

I'm not struggling, been using Linux many years, just a bit rusty with some things is all.

Lubuntu is only i386 and I want x86_64...

I'm a Linux geek so I like to tinker...

---

### Post by theozzlives on 2010-05-05
> **DasFox said:**
> I'm not struggling, been using Linux many years, just a bit rusty with some things is all.

Lubuntu is only i386 and I want x86_64...

I'm a Linux geek so I like to tinker...

If you know what your doing, why are you asking for help? If you got less than 4 GB RAM, you don't need AMD64, also Lubuntu isn't ready for release yet.

---

### Post by DasFox on 2010-05-05
> **theozzlives said:**
> If you know what your doing, why are you asking for help? If you got less than 4 GB RAM, you don't need AMD64, also Lubuntu isn't ready for release yet.


I said I'm a bit rusty is all...

Can I PLEASE just get someone to answer the post?


THANKS

---

### Post by theozzlives on 2010-05-05
> **DasFox said:**
> I said I'm a bit rusty is all...

Can I PLEASE just get someone to answer the post?


THANKS

Do you have GDM installed, or do you go to the CLI when you login? You might do better installing Ubuntu, then add LXDE. You might be able to remove GNOME after that.

---

### Post by DasFox on 2010-05-05
> **theozzlives said:**
> Do you have GDM installed, or do you go to the CLI when you login? You might do better installing Ubuntu, then add LXDE. You might be able to remove GNOME after that.

LXDE uses the LXDM, not GDM, so I have a GUI login...

---

### Post by bodhi.zazen on 2010-05-05
You will need to install an application that performs the mounting for you.

You can use the command line (pmount) 

You can install usbmount (it is in the Ubuntu repos)

[http://usbmount.alioth.debian.org/](http://usbmount.alioth.debian.org/)

Or if you want some something a bit heavier go with Thunar.

---

### Post by DasFox on 2010-05-05
> **bodhi.zazen said:**
> You will need to install an application that performs the mounting for you.

You can use the command line (pmount) 

You can install usbmount (it is in the Ubuntu repos)

[http://usbmount.alioth.debian.org/](http://usbmount.alioth.debian.org/)

Or if you want some something a bit heavier go with Thunar.

I have pmount installed, I didn't like usbmount, which you don't need installed.

PCManFM does the job just fine, don't need Thunar.

Something else is going on...

Right now I'm just trying to check that dbus, udisks and gvfs are running correct, then take it from there...

---

### Post by bodhi.zazen on 2010-05-05
Sounds like you prefer to debug dbus then , hopefully someone with some experience with dbus will see your thread.

I would have used a more descriptive title such as "help with dbus". The title you chose is unlikely to attract the kind of assistance you need.

You will also need to post some more technical information, simply stating that it is not working, or that you prefer PCManFM without some error messages, logs, hardware information, filesystem, etc, etc makes it difficult to offer much help.

Problems automounting NTFS != problems mounting ext2 for example.

---

### Post by DasFox on 2010-05-05
> **bodhi.zazen said:**
> Sounds like you prefer to debug dbus then , hopefully someone with some experience with dbus will see your thread.

I would have used a more descriptive title such as "help with dbus". The title you chose is unlikely to attract the kind of assistance you need.

You will also need to post some more technical information, simply stating that it is not working, or that you prefer PCManFM without some error messages, logs, hardware information, filesystem, etc, etc makes it difficult to offer much help.

Problems automounting NTFS != problems mounting ext2 for example.

It's not just help with dbus, as I said in the post, I was told to check that dbus, udisks and gvfs are running correct at  this point in time from the LXDE developers.

In the logs there are no errors messages...

---

### Post by loko on 2010-05-05
It´s a known bug.
Go to your bios and disable the floppy controler ( even if you don´t have a floppy)
Automount should work then.

You can find this bug on launchpad, but don´t ask me where

---

### Post by DasFox on 2010-05-05
> **loko said:**
> It´s a known bug.
Go to your bios and disable the floppy controler ( even if you don´t have a floppy)
Automount should work then.

You can find this bug on launchpad, but don´t ask me where

I have a laptop, no bios with a floppy controller here, but thanks...

---

### Post by DasFox on 2010-05-05
I was told this is a bug in PCManFM 0.5.2

Anyhow this is the syslog: ( All I see is the **Test WP failed, assume Write Enabled**, not sure that will effect it).


May  5 14:09:53 localhost kernel: [  243.614487] usb-storage: device found at 3
May  5 14:09:53 localhost kernel: [  243.614494] usb-storage: waiting for device to settle before scanning
May  5 14:09:58 localhost kernel: [  248.610504] usb-storage: device scan complete
May  5 14:09:58 localhost kernel: [  248.655345] scsi 6:0:0:0: Direct-Access     FUJITSU  MHV2060AH        0811 PQ: 0 ANSI: 0
May  5 14:09:58 localhost kernel: [  248.661552] sd 6:0:0:0: Attached scsi generic sg2 type 0
May  5 14:09:58 localhost kernel: [  248.677335] sd 6:0:0:0: [sdb] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
May  5 14:09:58 localhost kernel: [  248.678320] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
May  5 14:09:58 localhost kernel: [  248.678328] sd 6:0:0:0: [sdb] Assuming drive cache: write through
May  5 14:09:58 localhost kernel: [  248.680853] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
May  5 14:09:58 localhost kernel: [  248.680864] sd 6:0:0:0: [sdb] Assuming drive cache: write through
May  5 14:09:58 localhost kernel: [  248.680874]  sdb: sdb1 sdb2
May  5 14:09:58 localhost kernel: [  248.706594] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
May  5 14:09:58 localhost kernel: [  248.706605] sd 6:0:0:0: [sdb] Assuming drive cache: write through
May  5 14:09:58 localhost kernel: [  248.706616] sd 6:0:0:0: [sdb] Attached SCSI disk

---

### Post by seeker5528 on 2010-05-05
Could you install GDM and use it as the display manager to see what happens?

On my Lubuntu system, if I use LXDM, both Nautilus and PCManFM fail to mount my flash drive with some window popping up with a message saying something about not having permission.

If I use GDM as my display manger, the mounting and unmmounting work as expected.

To muddy the waters up even more....

On another machine where I run Gnome as my desktop and use lxdm. Mounting the flash drive was failing the same way.

After switching the display manager to GDM, then rebooting, mounting and unmounting work as expected.

After switching the display manager back to lxdm, then rebooting, mounting and unmounting still work as expected. 

On the Lubuntu machine, switching, then switching back didn't change anything, it works when I use GDM, doesn't work when I use lxdm. :???:

Later, Seeker

---

### Post by seeker5528 on 2010-05-06
> **seeker5528 said:**
> After switching the display manager back to lxdm, then rebooting, mounting and unmounting still work as expected.

Oops, there seems to be some inconsistency when using dpkg-reconfigure to select a different default display manager.

Somehow GDM was still being started but using a different display. Since I had already did 'dpkg-reconfigure lxdm', I did 'dpkg-reconfigure gdm', then selected lxdm as my default. Then GDM didn't come up anymore, but for some reason on the next boot KDM was started instead, so I logged in and mounting and unmounting worked as expected.

So now after having done 'dpkg-reconfigure kdm' and selecting lxdm, things seem to be the way they should have been after doing 'dpkg-reconfigure lxdm', lxdm at the login, no other display mangers running on another display. Attempting to mount the drive gives the dialog about not having permission.

Another interesting side note, maybe because KDE still uses hal, Dolphin can mount the partition on the flash drive, but complains when I want to unmount it.

EDIT: There is some stuff about ck-launch-session that seems relevant to the situation. 

[http://www.google.com/search?client=ubuntu&channel=fs&q=ck-launch-session&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=ck-launch-session&ie=utf-8&oe=utf-8)

Later, Seeker

---

### Post by DasFox on 2010-05-08
As I said before I was told this is a bug in PCManFM 0.5.2.

The LXDE people will tell you... ;)

0.9x resolves this issue, so I hope the Ubuntu team will get out PCManFM2 soon...

---

### Post by kerry_s on 2010-05-08
> **DasFox said:**
> As I said before I was told this is a bug in PCManFM 0.5.2.

The LXDE people will tell you... ;)

0.9x resolves this issue, so I hope the Ubuntu team will get out PCManFM2 soon...

you can add the lubuntu ppa & install pcmanfm2, i don't have much luck with pcmanfm, always to crashy no matter what version, i'm using nautilus in lubuntu.

```
ppa:lubuntu-desktop/ppa
```

---

### Post by PCMan on 2010-05-08
I'm sure that almost all of the details you need to know are documented.
[http://wiki.lxde.org/en/PCManFM_build_and_setup_guide](http://wiki.lxde.org/en/PCManFM_build_and_setup_guide)

Good luck!
Send mails to LXDE mailing list or utilize lxde irc channel when this guide doesn't help.

---

### Post by DasFox on 2010-05-08
> **PCMan said:**
> I'm sure that almost all of the details you need to know are documented.
[http://wiki.lxde.org/en/PCManFM_build_and_setup_guide](http://wiki.lxde.org/en/PCManFM_build_and_setup_guide)

Good luck!
Send mails to LXDE mailing list or utilize lxde irc channel when this guide doesn't help.

I followed the guide and compiled menu-cache, libfm and pcmanfm 0.9.5 but when I plug in a USB drive I get 'Not Authorized' popup.

I have gvfs installed I compiled pcmanfm against, I have hal, dbus, udisks and pmount installed. Hal isn't running only dbus and here is my /etc/group:

```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:sar
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:sar
fax:x:21:
voice:x:22:
cdrom:x:24:sar
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:sar
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:sar
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:sar
mlocate:x:105:
ssh:x:106:
sar:x:1000:
lpadmin:x:107:sar
sambashare:x:108:sar
admin:x:109:sar
messagebus:x:110:
haldaemon:x:111:
netdev:x:112:sar

```

How can I get usb drive to automount and allow me access?

THANKS

---

### Post by seeker5528 on 2010-05-08
> **DasFox said:**
> As I said before I was told this is a bug in PCManFM 0.5.2.

I can't help what you were told about it being a bug in PCManFM. 

Maybe the bug is in PCManFM, maybe it isn't. 

Just telling you what the case is for me, maybe it works that way for you too. :p ;)

I installed PCManFM from the repositories on my Lubuntu machine to see how that compares to the PCManFM2 package from the PPA.

Just as was the case with PCManFM2 on the Lubuntu machine, Nautilus on the other machine and to a lesser extent Dolphin on the other machine, the mounting stuff works for me with PCManFM if I use GDM or KDM as my display manager, doesn't work for me if I use LXDM as my display manager.

I have seen another thread or 2 where there was a problem with automounting in the stock Ubuntu, where automounting failed but going to places and clicking on the drive would still work, which is where going into the bios and disabling the floppy was found to work for some people. If something like this is what is happening, and you don't have to option to turn off the floppy in your bios, then I don't know that PCManFM 5.2 has the built in function to deal with it. When I use LXDM as the display manager, PCManFM doesn't even show my flash drive, when I use another display manager, the flash drive shows up with the option to mount or unmount it.

> **DasFox said:**
> I followed the guide and compiled menu-cache, libfm and pcmanfm 0.9.5 but when I plug in a USB drive I get 'Not Authorized' popup.

Yep, that's what I see on all my machines if I use lxdm as the display manager. ;)

Appears to be something with console kit integration, but I couldn't get the ck-launch-session thing to work, only works for me if I switch to a different display manager. 

Later, Seeker

---

### Post by DasFox on 2010-05-08
This is basically a permission problem and LXDE was designed to run as a stand alone desktop, not with other display managers.

PCMan is the guy who is working on this, developing it, so hopefully will get some word back.

THANKS

---

### Post by PCMan on 2010-05-09
> **DasFox said:**
> This is basically a permission problem and LXDE was designed to run as a stand alone desktop, not with other display managers.

PCMan is the guy who is working on this, developing it, so hopefully will get some word back.

THANKS

I suspected that it's a ubuntu bug. During Lubuntu beta 2 - beta 3, after one upgrade, I lost the ability to mount drives, too and I got the same error. Nor did nautilus work. It's possibly related to incorrect policykit configuration but I don't know how to fix this. PCManFM simply calls gvfs for mounting so it's definitely not a PCManFM bug but a configuration problem or a gvfs bug.

PCManFM should work with any login manager or desktop. The only problem is, gvfs requires correctly working dbus + policykit, which if not configured or intialized correctly can make gvfs broken. This is a policykit-related issue.

After I re-installed Lubuntu, everything works again, with the same file manager. So it's not my bug, but a Ubuntu bug possibly related to policykit.

---

### Post by DasFox on 2010-05-09
> **PCMan said:**
> I suspected that it's a ubuntu bug. During Lubuntu beta 2 - beta 3, after one upgrade, I lost the ability to mount drives, too and I got the same error. Nor did nautilus work. It's possibly related to incorrect policykit configuration but I don't know how to fix this. PCManFM simply calls gvfs for mounting so it's definitely not a PCManFM bug but a configuration problem or a gvfs bug.

PCManFM should work with any login manager or desktop. The only problem is, gvfs requires correctly working dbus + policykit, which if not configured or intialized correctly can make gvfs broken. This is a policykit-related issue.

After I re-installed Lubuntu, everything works again, with the same file manager. So it's not my bug, but a Ubuntu bug possibly related to policykit.

I can mount them by hand in the terminal, it just says root must mount and I was able to mount them as root.

Yes this seems to be a policykit issue, what packages related to the policykit do you have installed on Lubuntu, so I can check?

Here's dbus, from what I can tell is running fine:

[B]sar@localhost:~$ ps -ef | grep dbus
102        454     1  0 16:16  ?        00:00:41 dbus-daemon --system --fork
sar       1036  1003  0  16:16 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch  --exit-with-session startlxde
sar       1039     1  0 16:16 ?        00:00:00 /usr/bin/dbus-launch  --exit-with-session startlxde
sar       1048     1  0 16:16 ?         00:00:00 /bin/dbus-daemon --fork --print-pid 7 --print-address 9  --session
sar      11305 10131  0 20:33 pts/0    00:00:00 grep  --color=auto dbus[/B]

At this point I think I'm just missing some packages is all.

Have a look here:

[http://pastebin.com/DdgZZf2T](http://pastebin.com/DdgZZf2T)

What do you have installed from these on Lubuntu?

I noticed that I don't have libpolkit-dbus2 installed and that's a lib for accessing PolicyKit via D-Bus.

THANKS

---

### Post by Athunye on 2010-05-10
I have a minimal install as well. I'll describe what I do to mount my pendrive and my mp3 player.

My hard disk is sda. I have sda1 for /, sad2 for /home and sda3 for swap.
Every time I plug an usb device, and I do ls /dev/sd<tab><tab> I see that my usb is recognized as sdb, and the usb partition is actually sdb1. dmesg | tail proves that.


What I then do is to add this to /etc/fstab:
```

/dev/sdb1 /home/my_user/usb_mount vfat users,noauto 0 0

```

Then:
```

mkdir $HOME/usb_mount

```

After that all I have to do is to run **mount usb_mount** as user.
If I click on that folder using rox-filer, it actually auto mounts that mount point for me.

I know it is not exactly the solution you are looking for, but I think it is still useful.```

```

---

### Post by seeker5528 on 2010-05-10
> **PCMan said:**
> PCManFM should work with any login manager or desktop. The only problem is, gvfs requires correctly working dbus + policykit, which if not configured or intialized correctly can make gvfs broken. This is a policykit-related issue.

I don't know what this means, but if I have KDM or GDM set as the display manager, log in normally, the run ck-list-session, it shows me something like:

```
Session1:
        unix-user = '1000'
        realname = 'seeker'
        seat = 'Seat1'
        session-type = ''
        active = TRUE
        x11-display = ':0'
        x11-display-device = '/dev/tty7'
        display-device = ''
        remote-host-name = ''
        is-local = TRUE
        on-since = '2010-05-10T23:32:27.499310Z'
        login-session-id = ''
```

If I do this while lxdm is the display manager I get something like:

```
Session1:
        unix-user = '1000'
        realname = 'seeker'
        seat = 'Seat1'
        session-type = ''
        active = TRUE
        x11-display = ''
        x11-display-device = ''
        display-device = '/dev/tty7'
        remote-host-name = ''
        is-local = TRUE
        on-since = '2010-05-10T23:14:31.209353Z'
        login-session-id = ''
        idle-since-hint = '2010-05-10T23:15:01.001934Z'
Session2:
        unix-user = '1000'
        realname = 'seeker'
        seat = 'Seat1'
        session-type = ''
        active = FALSE
        x11-display = ':0'
        x11-display-device = '/dev/tty7'
        display-device = ''
        remote-host-name = ''
        is-local = TRUE
        on-since = '2010-05-10T23:14:31.290814Z'
        login-session-id = ''
```

Purged LXDM and re-installed it, and ck-list-session shows same type of result and same results when attempting to mount something.

Later, Seeker

---

### Post by Athunye on 2010-05-12
I managed to get usb devices mounting automatically by having this line in my $HOME/.xinitrc:

```

exec ck-launch-session dbus-launch startlxde

```

... instead of 'exec startlxde'.

I hope it works for you as well.

---

### Post by seeker5528 on 2010-05-12
> **Athunye said:**
> I managed to get usb devices mounting automatically by having this line in my $HOME/.xinitrc:
```

exec ck-launch-session dbus-launch startlxde

```

Somewhere along the way, during the Lucid development cycle, the default session seems to have gotten nuked on all my machines, GDM and KDM did not even show a option.

What LXDM claimed is Default always starts LXDM and ignores the copies of .xinitrc and .xsession in my home directory.

If I create a desktop entry in '/usr/share/xsessions' name it default-xsession.desktop, with the contents:

```
Name=Default Xsession
Comment=Default X session that uses ~/.xsession if found.
Exec=/etc/X11/Xsession
```

This gives me an entry in the Display Manger that shows up as 'Default Xsession' and works the way I expect in regard to '~/.xsession', doesn't recognize '~/.xinitrd'.

Doesn't matter which of these I use when I create the .xsession file in my home directory.....

```
exec ck-launch-session dbus-launch startlxde

or

exec ck-launch-session startlxde
```

ck-list-session shows something like this:

```
Session1:
	unix-user = '1000'
	realname = 'seeker'
	seat = 'Seat1'
	session-type = ''
	active = TRUE
	x11-display = ''
	x11-display-device = ''
	display-device = '/dev/tty7'
	remote-host-name = ''
	is-local = TRUE
	on-since = '2010-05-12T20:45:20.965399Z'
	login-session-id = ''
	idle-since-hint = '2010-05-12T20:45:51.005885Z'
Session2:
	unix-user = '1000'
	realname = 'seeker'
	seat = 'Seat1'
	session-type = ''
	active = FALSE
	x11-display = ':0'
	x11-display-device = '/dev/tty7'
	display-device = ''
	remote-host-name = ''
	is-local = TRUE
	on-since = '2010-05-12T20:45:21.049334Z'
	login-session-id = ''
Session3:
	unix-user = '1000'
	realname = 'seeker'
	seat = 'Seat1'
	session-type = ''
	active = FALSE
	x11-display = ':0'
	x11-display-device = '/dev/tty7'
	display-device = ''
	remote-host-name = ''
	is-local = TRUE
	on-since = '2010-05-12T20:45:21.469720Z'
	login-session-id = ''
```

Instead of one 'active = FALSE' session that looks like it would have worked if it was active, I get 2 that looked like they would have worked if they had been active and one 'active = TRUE' session that looks wrong.

I have transmission downloading the DVD now, so I can update my installation disk to Lucid and do a clean install on the Lubuntu machine.

It might even complete before I go home so I can burn it and possibly have a window of opportunity to install it in the morning.

Later, Seeker

---

### Post by seeker5528 on 2010-05-12
> **Athunye said:**
> I managed to get usb devices mounting automatically by having this line in my $HOME/.xinitrc:
```

exec ck-launch-session dbus-launch startlxde

```

Somewhere along the way, during the Lucid development cycle, the default session seems to have gotten nuked on all my machines, GDM and KDM did not even show a option.

What LXDM claimed is Default always starts LXDM and ignores the copies of .xinitrc and .xsession in my home directory.

If I create a desktop entry in '/usr/share/xsessions' name it default-xsession.desktop, with the contents:

```
Name=Default Xsession
Comment=Default X session that uses ~/.xsession if found.
Exec=/etc/X11/Xsession
```

This gives me an entry in the Display Manger that shows up as 'Default Xsession' and works the way I expect in regard to '~/.xsession', doesn't recognize '~/.xinitrd'.

Doesn't matter which of these I use when I create the .xsession file in my home directory.....

```
exec ck-launch-session dbus-launch startlxde

or

exec ck-launch-session startlxde
```

ck-list-session shows something like this:

```
Session1:
	unix-user = '1000'
	realname = 'seeker'
	seat = 'Seat1'
	session-type = ''
	active = TRUE
	x11-display = ''
	x11-display-device = ''
	display-device = '/dev/tty7'
	remote-host-name = ''
	is-local = TRUE
	on-since = '2010-05-12T20:45:20.965399Z'
	login-session-id = ''
	idle-since-hint = '2010-05-12T20:45:51.005885Z'
Session2:
	unix-user = '1000'
	realname = 'seeker'
	seat = 'Seat1'
	session-type = ''
	active = FALSE
	x11-display = ':0'
	x11-display-device = '/dev/tty7'
	display-device = ''
	remote-host-name = ''
	is-local = TRUE
	on-since = '2010-05-12T20:45:21.049334Z'
	login-session-id = ''
Session3:
	unix-user = '1000'
	realname = 'seeker'
	seat = 'Seat1'
	session-type = ''
	active = FALSE
	x11-display = ':0'
	x11-display-device = '/dev/tty7'
	display-device = ''
	remote-host-name = ''
	is-local = TRUE
	on-since = '2010-05-12T20:45:21.469720Z'
	login-session-id = ''
```

Instead of one 'active = FALSE' session that looks like it would have worked if it was active, I get 2 that looked like they would have worked if they had been active and one 'active = TRUE' session that looks wrong.

I have transmission downloading the DVD now, so I can update my installation disk to Lucid and do a clean install on the Lubuntu machine.

It might even complete before I go home so I can burn it and possibly have a window of opportunity to install it in the morning.

Later, Seeker

---

### Post by seeker5528 on 2010-05-13
Did new install by booting from DVD, choosing the text mode installation, did minimal install. 

After logging in to the minimal install, installed aptsh, in aptsh typed ```
install lubuntu-*
```.

Rebooted and logged in.

No flash drive showing up. Installed pmount, still no flash drive showing up.

Unchecked the option in Synaptic to treat recommends as dependencies and installed Nautilus and KDM.

Nautilus complains about permission when attempting to mount the flash drive.

After logging out and switching to a VT, stopping lxdm, starting KDM, logging back in to the GUI.

Flash drive shows up in PCManFM.

And ck-list-sessions shows the same situation as well with a session that looks correct being listed as inactive and one that looks wrong being listed as active, where with KDM there is only a single session listed.

Later, Seeker

---

### Post by Athunye on 2010-05-13
I finally got it to mount automatically just by starting lxde from ~/.xinitrc using this line:
```

exec ck-launch-session dbus-launch startlxde

```

Then I open pcmanfm, and wait for my usb device to show up in the left-side list. Just have to click on it.

---

### Post by eeried on 2010-05-20
Hello there,

I'm running Lubuntu. I haven't got a ~/.xinitrc file. Should I make one?

I want to say that I've used PCManFM on SliTaz and it is just beautiful: you can see all your drives and sticks listed in the side panel and one clic mounts any of them. Perhaps it's an older version of PCManFM, I haven't checked.

Cheers,

Edit: In fact, I started with a simple piece of advice I read in the thread: disabling the floppy in the Bios, and perhaps installing pmount did the trick. When I inserted the USB stick, a dialog box opened and asking me if I want to open the stick in the filemanager.

I launched PCManFM and in the side panel, I can see my second HDD (which I had to sudo mount in Ubuntu Jaunty), the USB stick and only one floppy icon (instead of 2 previously).

I didn't install GDM and didn't add a line to any file. Hope this good thing won't vanish on the next boot :-/

---

### Post by Athunye on 2010-05-27
You just have to create a ~/.xinitrc file if you don't have one.

Here's mine:
```

#!/usr/bin/bash
xrdb -merge ~/.Xdefaults # My Xdefaults sets my Mouse Cursor Theme.
feh --bg-scale ~/Pictures/Backgrounds/Aqua_Graphite.jpg
# sleep 1 && nm-applet & # I don't use network managers anymore.
sleep 1 && conky &
exec ck-launch-session dbus-launch startlxde

```

---

### Post by vancheese on 2010-06-01
My issue is a simular problem except I've a 64bit version of ubuntu  which doesn't work whilst a previous 32-bit install was fine

---

### Post by angelsguitar on 2011-01-21
I realize this thread is old, but if it is of any help, the solution stated [here]("http://ubuntuforums.org/showpost.php?p=9973195&postcount=23") worked for me:

> 
This is a general Ubuntu problem that nobody seems to have any real way to fix, but I do have a workaround that did the trick in Linux Mint 9 and Ubuntu 10.04. All the other suggestions that I've read here and other threads have been useless for me.

sudo gedit /etc/modules

add this at the bottom -
hid
usbhid
usb_storage

reboot, enjoy your functioning automount.

---

### Post by Fraoch on 2011-04-12
I've installed lubuntu in a VM and I'm having the same problem as outlined in this thread - can't automount.

Well, I can automount CDs, but I can't automount shared drives.  The drives have full sharing and guest permissions.

PCManFM can see the shared drive but can't mount it, giving the permissions error mentioned many times in this thread.

I found something that was not mentioned in this thread:

[https://wiki.archlinux.org/index.php/PCManFM#Mounting_as_normal_user](https://wiki.archlinux.org/index.php/PCManFM#Mounting_as_normal_user)

which does alter the policy kit, but unfortunately it had no effect.

It's definitely a permissions problem on lubuntu - if I mount the drive as root it works fine.  But I just cannot get a regular user to mount it.

Any ideas?

---

