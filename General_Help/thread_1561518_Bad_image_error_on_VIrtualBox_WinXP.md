---
title: "Bad image error on VIrtualBox WinXP"
date: 2010-08-26
forum: General Help
---

### Post by sammy0131 on 2010-08-26
I'm using the Virtual box on Ubuntu which has Windows XP on it. Probably after WinXP was automatically updated, I started getting an error message: "DLL C:\WINDOWS\system32\DNSAPI.dll is not a valid windows image." and I cannot log on anymore. I tried to find a solution but since I'm using the Virtualbox, I don't know how to access the virtual "Windows folder" from Ubuntu. Please help!:(

Thanks in advance,

---

### Post by quizno50 on 2010-08-26
You could always mount the Ubuntu live CD on your virtual box and boot off of it to modify your windows hard disk image. I'm sure there's a way to mount the hard disk image directly; but I know virtual box can use 'automatically expanding' hard disk images, and I don't know of a way to mount these directly in Linux...

---

### Post by vitothegreat on 2010-08-26
Have you tried mounting xp image and repairing the installation?

---

### Post by sammy0131 on 2010-08-26
Thanks for the quick response! 

I haven't mounted the xp image yet (it just happened at work this morning and I don't have an installation CD here:-(

It seems to be a winxp specific problem (see the forum in the following link) and I'm wishing if I could copy and paste dnsapi.dll into system32.

[http://www.computing.net/answers/windows-xp/xp-wont-load-lassexe-dnsapidll/154023.html](http://www.computing.net/answers/windows-xp/xp-wont-load-lassexe-dnsapidll/154023.html)

---

### Post by quizno50 on 2010-08-26
> I'm wishing if I could copy and paste dnsapi.dll into system32.
If you boot the Ubuntu live cd you can do basically that. But you will need an original source of the file (I'm sure you can google it).

---

### Post by sammy0131 on 2010-08-26
Thanks for your advice again! I just came back home so I can try what you suggested. So should I mount the ubuntu Live CD on the Virtualbox that's supposed to run WinXp? I'm bit confused.

---

### Post by sammy0131 on 2010-08-26
Umm, I tried to mount the Ubuntu Live CD on Virtual WinXP, and the menu showed up but then it seems to be frozen. I couldn't select "Try Ubuntu without installing". What should I do???

---

### Post by quizno50 on 2010-08-27
Yeah; just mount the Live CD before you boot up the virtual box (with the broken XP); then have it boot off of it. Then when it's up and running, you can copy the needed file to your System32 directory. Just drag and drop.

---

