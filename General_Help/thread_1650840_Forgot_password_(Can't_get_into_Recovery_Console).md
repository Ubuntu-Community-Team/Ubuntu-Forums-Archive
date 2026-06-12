---
title: "Forgot password (Can't get into Recovery Console)"
date: 2010-12-22
forum: General Help
---

### Post by chrisch on 2010-12-22
I have seen a hundred post to just boot into the Recovery console and reset the users password, but when I do it asks for a password before I can do anything.  I know there are Windows Password hack utilities, are there any for Linux/Ubuntu?  Any other options?  Can I use a live cd to access the config file or something?

---

### Post by karthick87 on 2010-12-22
[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

---

### Post by aysiu on 2010-12-22
> **karthick87 said:**
> [http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)
I don't know if Esc works any more in the latest versions of Ubuntu. Theoretically, holding down the Shift key should allow you to get the Grub menu up. If that doesn't work, there's a much longer workaround to use a live CD to reset the password (scroll down to the bottom of this page):
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by chrisch on 2010-12-22
I can get into the Grub Menu, and when I do I select the 2nd option as you describe (Recovery mode), but before I can do anything at the command prompt it asks for an Administrative password.  So another words, I never get to the "Drop to root shell" option.

---

### Post by aysiu on 2010-12-22
> **chrisch said:**
> I can get into the Grub Menu, and when I do I select the 2nd option as you describe (Recovery mode), but before I can do anything at the command prompt it asks for an Administrative password.  So another words, I never get to the "Drop to root shell" option.
This is why when people ask how to set a root password in Ubuntu I always tell them not to do it--it renders the recovery mode useless if you forget the root password. Ubuntu does **not** have a root password by default.

So scroll down to the absolute bottom of the page I linked to and use the live CD workaround.

---

### Post by chrisch on 2010-12-22
Perfect, will give it a shot.  Thank you.

---

### Post by Dave_L on 2010-12-22
> **aysiu said:**
> ...recovery mode useless if you forget the root password.

So recovery mode is not the same as single-user mode (runlevel=1)?  That should bypass any user authentication and drop directly into a root shell.

(I'm not advocating setting a root password, but just trying to learn Ubuntu.)

---

### Post by psusi on 2010-12-22
Or you can press e at the grub prompt to edit the command and add init=/bin/bash to the kernel command line, which will drop you directly to a root shell.

---

### Post by psusi on 2010-12-22
> **Dave_L said:**
> So recovery mode is not the same as single-user mode (runlevel=1)?  That should bypass any user authentication and drop directly into a root shell.

(I'm not advocating setting a root password, but just trying to learn Ubuntu.)

Single user mode has always prompted for the root password.  Recovery mode used to just go to single user mode, but now it actually presents you with a menu prompt giving a few other choices in addition to dropping to the root shell.

---

### Post by Dave_L on 2010-12-22
> **psusi said:**
> Single user mode has always prompted for the root password.

You mean in Ubuntu?

In a couple of other distributions I've used, that was not the case. In fact, single-user mode was one of the ways of resetting a forgotten root password.

---

### Post by psusi on 2010-12-22
> **Dave_L said:**
> You mean in Ubuntu?

In a couple of other distributions I've used, that was not the case. In fact, single-user mode was one of the ways of resetting a forgotten root password.

In every unix system.  By default in Ubuntu, there is no root password, hence, no prompt.  If you set a root password, you get prompted for it.

---

### Post by Dave_L on 2010-12-22
> **psusi said:**
> In every unix system.  By default in Ubuntu, there is no root password, hence, no prompt.  If you set a root password, you get prompted for it.

That is not correct.  I've used GNU/Linux distributions other than Ubuntu, with root login enabled (with password), and booting into single-user mode (runlevel 1) bypassed the need to provide a password.

That's why I was asking whether the situation is different for Ubuntu. Or maybe it's a recent feature change for grub 2 and/or newer kernels.

---

### Post by karthick87 on 2010-12-22
In ubuntu root password is disabled by default..

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Dave_L on 2010-12-22
Yes, karthick87, that's true, but it has nothing to do with the question asked.  I'll repeat it, since perhaps you missed reading it:

> So recovery mode is not the same as single-user mode (runlevel=1)? That should bypass any user authentication and drop directly into a root shell.

(I'm not advocating setting a root password, but just trying to learn Ubuntu.)

---

### Post by sisco311 on 2010-12-22
> **Dave_L said:**
> That is not correct.  I've used GNU/Linux distributions other than Ubuntu, with root login enabled (with password), and booting into single-user mode (runlevel 1) bypassed the need to provide a password.

That's why I was asking whether the situation is different for Ubuntu. Or maybe it's a recent feature change for grub 2 and/or newer kernels.

Yeh, some distributions simply start a root shell in single user mode. Others, like Ubuntu or Suse, use sulogin. The vanilla sulogin prompts you for the root password even if it's locked, but in Ubuntu it's patched to handle the default case of a locked root password.

In Fedora you can use the SINGLE=value kernel parameter to select the single-user mode type.  The value has to be either /sbin/sulogin (a user will be prompted for a password to log in), or /sbin/sushell (the user will be logged in directly). I'm not sure which one is the default.

---

### Post by psusi on 2010-12-22
> **Dave_L said:**
> That is not correct.  I've used GNU/Linux distributions other than Ubuntu, with root login enabled (with password), and booting into single-user mode (runlevel 1) bypassed the need to provide a password.

That's why I was asking whether the situation is different for Ubuntu. Or maybe it's a recent feature change for grub 2 and/or newer kernels.

What distribution was that?  Because that's not how it worked in debian, slackware, and at&t system V, all of which run /sbin/sulogin when you boot to single user mode, which prompts for the root password to enter maintainence mode, or press ctrl-d for normal startup.

---

### Post by chrisch on 2010-12-23
Eiting the Shadow file worked perfectly, thank you for the help.

---

