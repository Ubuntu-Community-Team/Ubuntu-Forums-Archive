---
title: "Ethernet Problem (Following Update?)"
date: 2006-03-27
forum: General Help
---

### Post by n00buntu on 2006-03-27
Hello,

  My Ubuntu 5.10 was running fine, until the ethernet suddenly died. As far as I can tell, the last thing I did before this happened was to update the system. My apologies, but I don't even know what details I should post about it; I tried to do so in [http://www.ubuntuforums.org/showthread.php?t=150847](http://www.ubuntuforums.org/showthread.php?t=150847) yesterday, but there haven't been any replies. If someone could help me out I'd really appreciate it.

  Thanks!

---

### Post by izmaelis on 2006-03-27
What kind of network card do you have on your computer?

---

### Post by n00buntu on 2006-03-27
[QUOTE=izmaelis]What kind of network card do you have on your computer?[/QUOTE]

  Hello,

  Thanks for your reply.

  I typed:
```
lspci | grep Ethernet
```
and got:
```
0000:00:04.0 Ethernet  controller: Solicon Integrated Systems [Sis] SiS900 PCI Fast Ethernet (rev 91)

```
  Does this answer the type of card I have? If not, what please should I type?

  Thanks

  n00buntu

---

### Post by jerrykenny on 2006-03-27
Can you got <System> <Administration>  <Networking> and see if the ethernet is active, if it is, try "stopping" then restarting the connection, you might try reconfiguring the connection as well. . . . Dont suppose its a cabling or hardware fault ? ethernet is usually no problem ?

---

### Post by n00buntu on 2006-03-27
Hi,

  Thanks for your reply.

[QUOTE=jerrykenny]Can you got <System> <Administration>  <Networking> and see if the ethernet is active, if it is, try "stopping" then restarting the connection, [/quote]

  I actually tried deactivating/activating the connection several times (also rebooting in between). This does not help, unfortunately.

[quote=jerrykenny]you might try reconfiguring the connection as well. . . . Dont suppose its a cabling or hardware fault ? ethernet is usually no problem ?[/QUOTE]

  Regarding the obvious causes (e.g., unconnected cables, router off, etc.): I am actually sure that this is not the problem, as the machine is a dual boot, and Windows connects just fine (I tried this between different Ubuntu reboots). In fact, Ubuntu was just fine until I updated it with the reddish icon on the top bar of the desktop (not that I know that that's the cause of the problem, but that's the last thing I did before it stopped working).

  About your comment that ethernet is usually no problem - you are probably correct. I probably should have called this "internet connectivity problem" (I don't know that the problem is with the ethernet).

  Thanks,

  n00buntu

---

### Post by n00buntu on 2006-03-28
Hello,

  Thanks to those who tried to assist. I gave up and reinstalled Ubuntu, eventually.

---

### Post by izmaelis on 2006-03-28
Did reinstallation of Ubuntu help to solve your problem?

---

