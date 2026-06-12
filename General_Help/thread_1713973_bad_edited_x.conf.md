---
title: "bad edited x.conf"
date: 2011-03-24
forum: General Help
---

### Post by GABIKA6 on 2011-03-24
Hi!

I've read a thread about ATI cards, and editing X.conf. But it isn't working on Ubuntu 9.04 and I used it, so my system is bad now. 
When I boot, I only see a crap sreen, some clours... so nothing. I tried to boot LiveCD and edit this file etc/X11/x.config, but I found there the old one, which was good, so I could not reedit it to fix it.

I don't know what to do, I am new to Ubuntu and to Linux too, please help. I am using Dell D600.

Thanks a lot,
GAbika

---

### Post by Buntumatic on 2011-03-24
If you switch to a console using Ctrl+Alt+F2, is the screen still garbled?

---

### Post by GABIKA6 on 2011-03-25
> **Buntumatic said:**
> If you switch to a console using Ctrl+Alt+F2, is the screen still garbled?

I can't use my keyboard because my laptop is freezed. No reaction to caps lock, num lock, and on nothing. So it's impossible to press Ctrl+Alt+F2.

I tried to run it in recovery mode, so i can use the terminal. I was looking up with nano to reedit the xconf, but the when i opened it, there was the old one, which was working, so... I don't know what to do.

When I tried to fix, in the xconf file there was written:

```
sudo dpkg-reconfigure -phigh xserver-xorg 
```

I ran LIVECD, and tried to edit the xconf file. It doesnt needs to be edited, only a backup of this is edited. So I don't know what to do now. I cant delete this bad backup file, from nano neither.

It run safetly, but nothing happens, when i rebooted, the computer was still freezed.

---

### Post by Buntumatic on 2011-03-25
Normally, you should edit /etc/X11/xorg.conf - but you have to be root to do this. If you need further help please post what changes you want to do and reference to the source where you learned it. You can do ```
sudo -i
``` to gain root access after you log in as user.

---

