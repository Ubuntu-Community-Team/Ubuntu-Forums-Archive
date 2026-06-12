---
title: "mouse malfunctioning!!!"
date: 2006-05-28
forum: General Help
---

### Post by anubix on 2006-05-28
my mouse is fuxored on the x-axis negatively (draw down FAST) and the y-axis negatively (draw left, 1/10th as bad as x)
I have a Toshiba Tecra 8100 laptop with a stick thingey in the middle of the keyboard. it all of a sudden just started pulling off.  I am using an USB mouse now, and sometimes it pulls while i move it, sometimes it doesn't (when it does i have to push up and right on the stick, then i can freely move the usb.)
my question is: i'm pretty sure this is not a hardware malfunction, how can i re-detect my mouse, or re-install a driver?
What can i do?
pz

---

### Post by starkes on 2006-05-28
I think this command should work for you i hope

```
sudo dpkg-reconfigure xserver-xorg
```

It will recofigure x entirely and you should be able to set the options for your mouse and whatnot. i'm guessing it's set up for the wrong mouse maybe?

I know i've used it before, but i had a partitioning program for windows hose my linux partition, and i installed over it and now that command doesnt work for me, so i can't verify for you, but i know i've used it before and it asks a lot about the mouse.

---

### Post by anubix on 2006-05-28
didn't work :(
any other ideas?

---

### Post by starkes on 2006-05-28
did anything happen when you typed that command?

---

### Post by anubix on 2006-05-28
it took me through the whole autoconfig process for xserver
it asked some questions about the mouse, but nothing came of it.

---

### Post by dmizer on 2006-06-16
maybe this is your problem?
[http://askiris.toshiba.com/ToshibaSupportSite/search.do?cmd=displayKC&docType=kc&externalId=108519xml&sliceId=&dialogID=11680975&stateId=1%200%2011678498](http://askiris.toshiba.com/ToshibaSupportSite/search.do?cmd=displayKC&docType=kc&externalId=108519xml&sliceId=&dialogID=11680975&stateId=1%200%2011678498)

i have your exact same computer.  does your cpu fan ever come on?  if not, you'll need to install all the toshiba related stuff via synaptic.  even then, i still have to manually toggle my cpu fan on and off.

---

