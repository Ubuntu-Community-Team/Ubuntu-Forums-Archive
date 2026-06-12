---
title: "Keyboard and mouse not working and dpkg-reconfigure fails"
date: 2009-07-15
forum: General Help
---

### Post by Xavier_To on 2009-07-15
Hi everyone, I really hope someone can help with my issue.

After booting this afternoon, I found that most stuff I had that was reachable was down (like apache and git). I verified that all application were running and they were. Since I thought i was a config issue, i ran 

sudo dpkg-reconfigure --all choosing the default value when asked.

I rebooted and my laptops keyboard and mouse stopped working. I thought it was a hardware issue (its an old laptop...) so i plugged in a usb mouse and keyboard and it responded. I tried entering my username and password, and it all froze. (i'm using a livecd right now).

Figuring something was wrong, i went in to the root shell in recovery mode and ran dpkg-reconfigure --all again but I get the following error 

*Starting deferred execution scheduler atd
invoke-rc.d : initscript atd, action "start" failed

Can anyone help me ? Is my system doomed for a re-install or can my system be saved ?

---

### Post by lisati on 2009-07-16
Try:
```
sudo dpkg --reconfigure -a
```

---

### Post by Xavier_To on 2009-07-16
I might be ignorant on this, so forgive me if this sounds stupid :

What's the difference between "sudo dpkg-reconfigure --all" and "sudo dpkg --reconfigure -a" ?

To me, it just seems like different ways to call the same command...

---

### Post by lisati on 2009-07-16
> **Xavier_To said:**
> I might be ignorant on this, so forgive me if this sounds stupid :

What's the difference between "sudo dpkg-reconfigure --all" and "sudo dpkg --reconfigure -a" ?

To me, it just seems like different ways to call the same command...

There are sometimes more than one way to skin a cat. I'm not fully clued up on all the "behind the scenes" stuff, but they are (theoretically) separate commands. One is the dpkg command, and the other is the dpkg-configure command.

---

