---
title: "How would I make a command that inputs something to terminal?"
date: 2012-07-11
forum: General Help
---

### Post by Hydera5 on 2012-07-11
Hello, I have Ubuntu on a flash drive.  The one problem I have is when I log off of the default account (Ubuntu) and onto my personal it wont shut down or restart when I tell it to.  I have read that I can issue "sudo shutdown -P now" and it will shut it down.  However I would like to be able to click something on my desktop or something of that nature to shut the machine off.  I would do the same with with "sudo reboot"

Help is appreciated,
Thanks

---

### Post by dino99 on 2012-07-11
enter that command BEFORE logging out

---

### Post by Hydera5 on 2012-07-12
> **dino99 said:**
> enter that command BEFORE logging out

Is there a way I can make the command click able?

---

### Post by black veils on 2012-07-12
yes  [http://ubuntuforums.org/showthread.php?t=2007247&highlight=bodhi+easier](http://ubuntuforums.org/showthread.php?t=2007247&highlight=bodhi+easier)

---

### Post by steeldriver on 2012-07-12
Hi,  afaik a standard (non-sudo) user *should* be able to shutdown / reboot via the taskbar "power button" by default - what happens when you try?

[http://askubuntu.com/questions/158668/how-can-i-allow-unprivileged-users-to-shutdown-from-the-panel-no-sudo](http://askubuntu.com/questions/158668/how-can-i-allow-unprivileged-users-to-shutdown-from-the-panel-no-sudo)

The only exception should be if another user is also logged in - in which case root is required (i.e. only root is allowed to kill *another* user's session).

---

### Post by David Andersson on 2012-07-12
This is 2 different problems

> **Hydera5 said:**
> Hello, I have Ubuntu on a flash drive.  The one problem I have is when I log off of the default account (Ubuntu) and onto my personal it wont shut down or restart when I tell it to. 

(I don't know why normal shutdown does not work for you. Maybe permissions are set up differently on a live-system than on a normal system.)

> **Hydera5 said:**
>  I have read that I can issue "sudo shutdown -P now" and it will shut it down.  However I would like to be able to click something on my desktop or something of that nature to shut the machine off.  I would do the same with with "sudo reboot"


You can place a Launcher in the panel or on the desktop. In the command field of the launcher, enter the command
```
gksu shutdown -P now
```
When you press that button it will ask for a password and then (hopefully) shut down.

(Explanation: *gksu* is required instead of *sudo*, because sudo assumes there is a terminal where the password is entered.)

(Techno mumbo jumbo name dropping: The title is misleading because nothing needs to be input to a *terminal*. The *launcher* invokes a *shell* to execute the *command*, or issues an *exec* system call directly.)

---

