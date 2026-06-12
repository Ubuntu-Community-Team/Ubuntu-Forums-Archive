---
title: "Tried to enable a password-less login in Lubuntu now I can't boot"
date: 2011-11-29
forum: General Help
---

### Post by TheBearNecessities on 2011-11-29
EDITED:  Just to say that the thread title is out of date and it should now say "I tried to enable password-less login and now my lubuntu won't boot at all"

**the info in this first post is from when i was wanting to enable password-less login so not much point in reading this first post; skip to post number three to see more details of my broken lubuntu**

Not sure if this is the correct place but here goes.

I'd like to be able to choose a user at login but all users have no passwords.

I'm using Lubuntu and there is an option titled "Don't ask for password on logon" in System Tools > Users and Groups.

This is EXACTLY what i need, but unfortunately it is greyed out.

I have found instructions on the fix here [http://lanxin0106.wordpress.com/2010/10/04/password-less-login-on-ubuntu-9-10-karmic-koala/](http://lanxin0106.wordpress.com/2010/10/04/password-less-login-on-ubuntu-9-10-karmic-koala/) but it is for a different Distro of Ubuntu.

Basically I need some help from someone because A) the instructions are for a different distro and B) i have never used the linux terminal before so not sure what to do with it.

When i follow the linked instructions above the terminal does nothing when i type in "gksu gedit /etc/pam.d/gdm"

ive looked in /etc/pam and there is no gdm file.

anyone able to see where im going wrong?

---

### Post by amjjawad on 2011-11-29
Hello and Welcome :)

Lubuntu is an official variant for Ubuntu and you can start your thread under Absolute Beginner Talk or General Help :)

Lubuntu and Ubuntu are both share the same core system but the desktop and the applications are different.

I think you'll find what you are looking for in:
Lubuntu One Stop Thread (my signature) > Section C > [#2]("https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides")

Hope that will help :)

If you need anything else, please let me know!

---

### Post by TheBearNecessities on 2011-11-30
> **amjjawad said:**
> Hello and Welcome :)

Lubuntu is an official variant for Ubuntu and you can start your thread under Absolute Beginner Talk or General Help :)

Lubuntu and Ubuntu are both share the same core system but the desktop and the applications are different.

I think you'll find what you are looking for in:
Lubuntu One Stop Thread (my signature) > Section C > [#2]("https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides")

Hope that will help :)

If you need anything else, please let me know!

Hi, thanks for taking the time to post.  I followed the instructions as you suggested ([https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LXDM](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LXDM)) but when i rebooted lubuntu no longer boots!

I'm a bit of a noob when it comes to linux so i have no idea how to troubleshoot and solve my problem.

Can anyone help?  Do i need to get lubuntu onto a usb stick, boot from that, and then edit the /etc/lxdm/default.conf file back to  what it was?  someone help me! :D

---

### Post by nothingspecial on 2011-11-30
Moved to General Help.

Lubuntu is supported here :)

---

### Post by TheBearNecessities on 2011-11-30
> **nothingspecial said:**
> Moved to General Help.

Lubuntu is supported here :)

Great, thanks for moving it.

Anyone know how i get lubuntu working again?  if i create a usb with lubuntu on it, can i just re-install lubuntu without losing documents and software i've downloaded?

---

### Post by nothingspecial on 2011-11-30
> **TheBearNecessities said:**
> 

Can anyone help?  Do i need to get lubuntu onto a usb stick, boot from that, and then edit the /etc/lxdm/default.conf file back to  what it was?  someone help me! :D

Yes that would be one option allthough you will probably be able to do it without that.

When you say you can't boot do you mean at all?

Or, when you try to boot can you press Ctrl-Alt-F1 and bring up a console login. If you can, login (when you type your password you won't see it).

Then type ```
sudo nano /etc/lxdm/default.conf
``` and edit the file. When you are done press Ctrl-O followed by enter to save and then Ctrl-X to exit then ```
sudo reboot
``` to restart.

You could also do that from recovery mode without sudo.

---

### Post by TheBearNecessities on 2011-11-30
ctrl-alt-f1 didn't work. but i managed to get into Recovery mode, then selected "shell prompt"

I then edited the file, but when i tried to save it says "error writing" and "read only file system"

I wasn't presented with an oppourtunity to login.  Is there a COMMAND I SHOULD TYPE IN TO THE SHELL PROMPT IN ORDER TO LOGIN.

(excuse the caps).

Sorry i'm needing a bit of hand holding here but i have next to no experience in linux at all.

Appreciate your help

---

### Post by nothingspecial on 2011-11-30
Try "root shell prompt" or whatever it says (something like that).

---

### Post by nothingspecial on 2011-11-30
> **TheBearNecessities said:**
> EDITED:  Just to say that the thread title is out of date and it should now say "I tried to enable password-less login and now my lubuntu won't boot at all"

Fixed :)

---

### Post by TheBearNecessities on 2011-11-30
still no luck i'm afraid.  I went to recovery mode

chose 'drop to shell prompt'

managed to login as myself

edited the file

but when i click on ctrl X it asks me if i want to save cached changes and i say yes, i am told that  same message "error writing sudo nano /etc/lxdm/default.conf read-only file system"

do you think i need to boot from a lubuntu usb and edit the file from there?

---

### Post by nothingspecial on 2011-11-30
Go back to recovery mode.

First choose "Remount / read write and mount all other file systems"

You select ok using the tab key.

Then choose "Drop to root shell prompt". Don't log in as yourself stay as root. Then edit the file _without_ sudo.

Be careful because logging in as root means you can do anything including deleting essential system files.

Then type exit.

---

### Post by TheBearNecessities on 2011-11-30
Fixed!

Managed to successfully edit the file by choosing "recovery mode", then choosing to "check disks [this will exit read only mode]", logged into, edited file, saved file, and rebooted.

I realised that my problem was that the /etc/lxdm/default.conf file was missing a heading.  it was missing the "[base]" heading.  Obviously i'm denying all resposibility :P  it's clear to me that i didn't accidently remove that heading, it must have been someone elses fault :lolflag:

Anyway thanks for helping me out mate.

Ps.  once [base] was back in i have managed to setup the file so i can login without a password.  Jackpot.

Only issue is I thought it would offer me the option of which user to login as, but instead it is just going straight into lubuntu as me, without offering the choice of logging in as my wife.

Is there something i'm missing, is it possible to be offered the choice of users but without any passwords?

---

