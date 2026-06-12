---
title: "Hibernate froze, so restarted.  Now, hangs at boot splash"
date: 2009-09-20
forum: General Help
---

### Post by stir-crazy on 2009-09-20
This is on a 64bit desktop running Ubuntu UE (I think 2.2, or 2.3, whatever's most recent).

I selected hibernate, and walked away.  About 5 minutes later I come by and notice that the computer is still on.  Think the only thing on the display was a blinking underscore in the top left corner.  I power off at the case.

Now, when I try to go into a normal Ubuntu boot, it locks up once I get to the UE boot splash, gets maybe a third of the way through so far as that little progress meter is concerned.

If I go into recovery mode, then select normal boot, I get straight into the login prompt (GUI) and all runs normally.

But I have to do this sequence every time now.:mad:  

As an aside, there's no suspend option, which would be useful to me more often than hibernate anyway.  Why isn't this shown in the power applet?

---

### Post by stir-crazy on 2009-09-20
Poke around online a day or two, post here, poke around 5 more minutes online, then find it.  *sigh* :oops:

Had to clear out my swap space.  Here's what I did:

```
sudo swapoff /dev/sda5
(Use whatever partition was labeled as “Linux swap” in fdisk. For me, this was /dev/sda5)
sudo mkswap /dev/sda5
sudo update-initramfs -u
```

Here's where I found it [Matt Cutts blog]("http://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/")

---

