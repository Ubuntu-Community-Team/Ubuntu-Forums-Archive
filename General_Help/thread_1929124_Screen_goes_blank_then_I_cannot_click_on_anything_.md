---
title: "Screen goes blank then I cannot click on anything with mouse and must reboot..."
date: 2012-02-21
forum: General Help
---

### Post by Rytron on 2012-02-21
Hi.

This has happened a number of times now.

Today Ubuntu 10.04 went blank for about 2 seconds and then comes back by itself. I can then use mouse but cannot click on anything.

Could this be a graphics card problem or a problem with Ubuntu or Xorg?

I hit **Alt Gr + k + Print** keys to force a log out. It logs out but I cannot do anything thus the only remedy is a reboot.

This has twice today. Most days it never happens but on occasion it may happen 2 or 3 times.

---

### Post by roelforg on 2012-02-21
Try pressing CTRL-ALT-F1 to get to a console,
login with your normal username.
sudo to root
mount an USB-drive
copy /var/log/Xorg.0.log to the USB drive,
repeat for dmesg
Post the contents
PM me because i'm bad at keeping up with posts.

---

### Post by Rytron on 2012-02-22
> **roelforg said:**
> Try pressing CTRL-ALT-F1 to get to a console,
login with your normal username.
sudo to root
mount an USB-drive
copy /var/log/Xorg.0.log to the USB drive,
repeat for dmesg
Post the contents
PM me because i'm bad at keeping up with posts.

Previously when this happened I could not use the keyboard thus Ctrl+Alt+F3 was impossible. Ctrl+Alt+F3 was suggested by someone (I presume CTRL-ALT-F1 will not be possible but I will give it a shot).

---

### Post by roelforg on 2012-02-22
> **Rytron said:**
> Previously when this happened I could not use the keyboard thus Ctrl+Alt+F3 was impossible. Ctrl+Alt+F3 was suggested by someone (I presume CTRL-ALT-F1 will not be possible but I will give it a shot).
The only difference is that my version will switch to VT1 instead of VT3
It doesn't matter.

---

### Post by Rytron on 2012-03-20
> **roelforg said:**
> Try pressing CTRL-ALT-F1 to get to a console,
login with your normal username.
sudo to root
mount an USB-drive
copy /var/log/Xorg.0.log to the USB drive,
repeat for dmesg
Post the contents
PM me because i'm bad at keeping up with posts.

The problem happened again. I pressed CTRL-ALT-F1 but to no avail.

---

### Post by WasMeHere on 2012-03-20
> **Rytron said:**
> The problem happened again. I pressed CTRL-ALT-F1 but to no avail.
Can you log in to your computer via ssh? In that case, what happens right now (does it work also when you get this kind of black-out)?

I have been able to shut down my main computer with Ubuntu 10.04 LTS desktop in a controlled way several times in similar situations via ssh (when the screen has stopped responding). Sometimes I have even been able to shut down and restart the processes behind the screen graphics. And sometimes roelforg's method with a local text screen works for me too.

*Edit: I have had problems with the screensaver, causing black-outs in 10.04.*

---

### Post by sudodus on 2012-03-20
Hi,

It's difficult to find what's wrong when it happens seldom. But it would be nice to find some way to tell if it is hardware or software related. If it happens maybe once a day on average, could you run another system with another graphics driver (live or from a small internal partition) for a few days (total time)? If it happens with that system, it's probably the hardware. If it doesn't happen, you can't be sure it's the software, but the longer time without a black-out, the more probable ...

Or can you borrow another grahics card and test it for a week?

Hope this can help, or give you some other similar idea to test :-)

---

### Post by Rytron on 2012-03-20
> **Olle Wiklund said:**
> Can you log in to your computer via ssh?

Sorry, I don't know how to login with ssh. But how would I do that if the screen went blank? Would I need to have the other PC connected and turned on ready to go?

> **Olle Wiklund said:**
> 
*Edit: I have had problems with the screensaver, causing black-outs in 10.04.*

Perhaps this is just a Lucid Lynx issue.

---

### Post by Rytron on 2012-03-20
> **sudodus said:**
> Hi,

It's difficult to find what's wrong when it happens seldom. But it would be nice to find some way to tell if it is hardware or software related. If it happens maybe once a day on average, could you run another system with another graphics driver (live or from a small internal partition) for a few days (total time)? If it happens with that system, it's probably the hardware. If it doesn't happen, you can't be sure it's the software, but the longer time without a black-out, the more probable ...

Or can you borrow another grahics card and test it for a week?

Hope this can help, or give you some other similar idea to test :-)

It may happen once in a month or can occur 3 times in the same day. It seems totally random.

I may change my Distro at the end of next month. If it does not happen again then it is an issue/bug with Lucid.

Unfortunately I do not have another graphics card at hand.

---

### Post by WasMeHere on 2012-03-20
> **Rytron said:**
> Sorry, I don't know how to login with ssh. But how would I do that if the screen went blank? Would I need to have the other PC connected and turned on ready to go?

Perhaps this is just a Lucid Lynx issue.

You need to install the whole ssh package and have the server program ***sshd*** running.
I think you simply run
```
sudo apt-get install ssh
``` to install it.
Then login via the network from another computer. You can run the simple command line interface ```
ssh
``` or something like ```
ssh rytron@your-computer
```

---

### Post by robbie 348 on 2012-03-20
Interesting. This has just started happening to me in the last few days, also using 10.04. The first time it did it, it wiped all my log-ins and passwords, but that hasn't happened since. It went blank twice about 30 mins. ago, only seconds apart. Now I just re-boot.

---

### Post by Rytron on 2012-03-20
> **Olle Wiklund said:**
> You need to install the whole ssh package...

Thanks.

---

### Post by sudodus on 2012-03-20
> **Rytron said:**
> It may happen once in a month or can occur 3 times in the same day. It seems totally random.

I may change my Distro at the end of next month. If it does not happen again then it is an issue/bug with Lucid.

Unfortunately I do not have another graphics card at hand.

Ubuntu 10.04 works with 'blank screen' as screensaver, but I have also had issues with the real screensaver programs. I guess you are waiting for the next LTS release, 12.04, and then switch to that version.

---

### Post by Rytron on 2012-03-20
> **sudodus said:**
> Ubuntu 10.04 works with 'blank screen' as screensaver, but I have also had issues with the real screensaver programs. I guess you are waiting for the next LTS release, 12.04, and then switch to that version.

Yes, but not the main Ubuntu. I dislike Unity. I may goto Lubuntu or Xubuntu 12.04 or a derivative.

---

### Post by sudodus on 2012-03-20
> **rytron said:**
> yes, but not the main ubuntu. I dislike unity. I may goto lubuntu or xubuntu 12.04 or a derivative.
+1

---

