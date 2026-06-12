---
title: "Removed user from all groups, no sudo, help!"
date: 2012-01-17
forum: General Help
---

### Post by weighty_foe on 2012-01-17
Hi all,

I hope you can help me.  What has happened is this:

I've removed the sole user on this laptop from all groups except "users" and "vboxusers"!!  I can't now use sudo, or access any administrative functions :(

How it happened:
I'm trying to install virtualbox on my wife's laptop, so I can install windows so I can install iTunes so she can set up her brand new iPod. (I have now got vbox & windows 7 & iTunes installed)

The VBox OSE version (which I initially installed) from the official repos does not support USB, so I removed it & downloaded the closed source version for 10.10 & installed that.

A warning popped up which said that my user is not a member of the "vboxusers" group so it couldn't access the USB subsystem.  I googled & found a blog "how to install windows on virtualbox for itunes on ubuntu 10.10" which said to run this command:
```
sudo usermod -G vboxusers danielle
```
Which I did & then logged out and in again.  Windows in VB now sees the ipod.  Yay.

But now:
```
danielle@Blondie:~$ id
uid=1000(danielle) gid=1000(danielle) groups=1000(danielle),123(vboxusers)
```

And:
```
danielle@Blondie:~$ sudo ls
<password>
danielle is not in the sudoers file.  This incident will be reported.
```

So, how do I fix it back to how it was?  I think danielle needs to be in the admin group to use sudo, but how to do it?

Wifes laptop:
Ubuntu 10.10 32bit, all updates applied yesterday.
One user, danielle

Resources I have:
Wifes laptop with cdrom
A windows PC with a fast internet connection, a cd burner and a stack of CDs.

I think I need to load a live cd, chroot in and alter either the sudoers file or change the user "danielle" back to how it should be.  I don't quite know how though.

Help!

---

### Post by nothingspecial on 2012-01-17
Hi, do not panic :)

The usermod command when used with the -G option will remove the user from all current groups and place them in the ones listed. To avoid this you need to use the -a option (append). See ```
man usermod
```

Restart the computer and boot into recovery mode, select a root shell

```
adduser danielle admin
```

```
exit
```

Then resume normal boot.

Then you will need to add her to all the other groups

---

### Post by weighty_foe on 2012-01-17
Hi, thanks.  I should have searched first.

I think I have sorted it:

Booted to recovery (root shell)
ran the following:

```
usermod -a -G adm,dialout,cdrom,floppy,audio,dip,fuse,video,plugdev,sambashare,lpadmin,admin danielle
```

That seems to have sorted it.  Are those the default groups or have I missed any out?

---

### Post by nothingspecial on 2012-01-17
You have some that aren't default (but that doesn't matter).

---

