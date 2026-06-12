---
title: "'error: unknown filesystem.  grub rescue&gt;' after messed up hibernation"
date: 2011-02-21
forum: General Help
---

### Post by omerp on 2011-02-21
Hello all,

I just had what seemed like a catastrophe with my Ubuntu installation, but was in fact able to recover from it completely (not to mention, within an hour or so), and now everything is up and running.

Here's what happened:

I was playing around with the "hibernate" function (a.k.a. "suspend to disk"), doing rather evil things, and at some point managed to make my computer hang. So I did a hard poweroff (holding down power switch, etc.).

However, when I powered the machine back up, instead of the normal GRUB menu, I got the following message:

```
error: unknown filesystem. 
grub rescue>

```

:icon_frown:

It gets worse: I booted from a LiveCD and ran *gparted*. In the list of partitions, where my main ext4 system partition usually sits, was 350GB marked as type "unknown".

Looks like a total loss, right? Have to reinstall Ubuntu from scratch? Nope! Here's what I did to solve it:

1. Install the *testdisk* package. This is unfortunately not part of the standard LiveCD, so you have to install it once the LiveCD system is up and running:[INDENT]a. Go to the system menu, choose "System-->Administration-->Software Sources", and check the option "Community-maintained Open Source software (universe)"
b. open a terminal (from the system menu, "Applications-->Accessories", and type: *sudo apt-get install testdisk*
[/INDENT]

2. run *sudo testdisk*, and follow the instructions [[COLOR="Navy"]_here_[/COLOR]]("www.cgsecurity.org/wiki/Advanced_Find_ext2_ext3_Backup_SuperBlock") (substitute *ext4* where this page says *ext3*, if you're indeed running an *ext4* system).

3. Reboot! (the LiveCD system will automatically eject your CD and prompt you to continue)

:D

---

