---
title: "File manager not responding"
date: 2011-05-28
forum: General Help
---

### Post by uwe.koch.k on 2011-05-28
Hi, I have installed 4 accounts on my acer aspire 4520 laptop. OS is natty (2.6.38-9-generic), 64 bit distro. Only on one account I can not access the directories / files placed on my desktop. Clicking on Places, in order to open My Documents, for example, does not work.

Typing nautilus on the command line, gives the following output:

uwe@koch-laptop:~$ nautilus

(nautilus:18297): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:18297): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
uwe@koch-laptop:~$ 

Removing and reinstalling nautilus solves the problem for that specific session, but not for the following.

Rebooting or shutting-down always is accompanied with a file manager not responding message.

---

### Post by linuxinstalledfromhdd on 2011-05-28
I haven't seen this before.  Did this ever happen with Ubuntu 10.10?

---

### Post by uwe.koch.k on 2011-05-28
No. Never ever.

---

### Post by wildmanne39 on 2011-05-29
> **uwe.koch.k said:**
> Hi, I have installed 4 accounts on my acer aspire 4520 laptop. OS is natty (2.6.38-9-generic), 64 bit distro. Only on one account I can not access the directories / files placed on my desktop. Clicking on Places, in order to open My Documents, for example, does not work.

Typing nautilus on the command line, gives the following output:

uwe@koch-laptop:~$ nautilus

(nautilus:18297): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:18297): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
uwe@koch-laptop:~$ 

Removing and reinstalling nautilus solves the problem for that specific session, but not for the following.

Rebooting or shutting-down always is accompanied with a file manager not responding message.Hi maybe you should create another user account and see if it works, then just switch over to that account.

---

### Post by uwe.koch.k on 2011-07-19
I took two decisions:

a) to remove every file on my Desktop in my account, which proved that one of the files was causing the problem, but don't know which one. Nautilus worked perfectly since.

b) to reinstall the hole OS from scratch, but with the 32 bit versions, since I have had big troubles with the wi-fi connection on this specific machine (Atheros chipset), but this has nothing to do with this thread.

So, as a conclusion, I consider this thread as closed ans solved.

---

