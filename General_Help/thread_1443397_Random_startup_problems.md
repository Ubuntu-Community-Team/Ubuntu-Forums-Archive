---
title: "Random startup problems"
date: 2010-03-31
forum: General Help
---

### Post by crashus on 2010-03-31
OK so here's my problem. I'm having seemingly random startup problems. I;m running on karmic, and have the 2.6.31-20 and 2.6.31-14 kernel installed.

And up until now, this problem has occurred twice, both at random times, as to say, I did not do any major updates or installations prior to the reboot. Then when I want to start my computer, it automatically restarts even before getting to the ubuntu logo. after this auto restart I get to the kernel menu, where I can chose which one to boot. And I can try booting everyone, both the 2.6.31-20 and 2.6.31-24, both the recovery modes, and everything is the same- the computer autorestarts, right before the ubuntu logo. 

The first time this happened the problem magically dissipated, and I booted normally into ubuntu. this time, I also tried running memory test, during which the comp. again auto restarted and after that the problem was gone again...

Anyone has a clue what might be the problem?

thanks

---

### Post by dabby_yo on 2010-03-31
Are you sure it hasn't done a disk check?

---

### Post by crashus on 2010-03-31
The first time this problem happened I tried the disc check, it froze at about 17%. I had to forcibly restart. Then after a few more tries it just booted normally.

I can not be certain if the disk check was completed, because I wasn't in front of the computer- I started it, left for a minute or two, and when I came back, the computer was in the process of rebooting. then the problem went away..

however i think the entire disk check for sure cant be completed in 2 minutes...

---

### Post by dabby_yo on 2010-03-31
> **crashus said:**
> The first time this problem happened I tried the disc check, it froze at about 17%. I had to forcibly restart. Then after a few more tries it just booted normally.

I can not be certain if the disk check was completed, because I wasn't in front of the computer- I started it, left for a minute or two, and when I came back, the computer was in the process of rebooting. then the problem went away..

however i think the entire disk check for sure cant be completed in 2 minutes...

Do you know how to boot into recovery mode?

---

### Post by crashus on 2010-03-31
> **dabby_yo said:**
> Do you know how to boot into recovery mode?

I tried booting into recovery mode through the menu, where you chose which kernel to load. 

2.6.31-20 recovery mode- This is what it says. 

if you mean this, I tried it, however the result was the same, it autorestarted.

---

### Post by dabby_yo on 2010-03-31
> **crashus said:**
> I tried booting into recovery mode through the menu, where you chose which kernel to load. 

2.6.31-20 recovery mode- This is what it says. 

if you mean this, I tried it, however the result was the same, it autorestarted.

Boot into recovery mode, select the root shell/prompt option, and run;

```
fsck
```

That may help.

---

### Post by crashus on 2010-03-31
In the end this does not happen every time I boot- as I said randomly.. 
I will try the disk check next time this happens, but does anyone knows why this happens, what kind a problem this is? I would rather prevent it, than later try to fix it..

---

### Post by dabby_yo on 2010-03-31
> **crashus said:**
> In the end this does not happen every time I boot- as I said randomly.. 
I will try the disk check next time this happens, but does anyone knows why this happens, what kind a problem this is? I would rather prevent it, than later try to fix it..

I would seriously recommend giving _fsck_ a try.

---

### Post by Bungler on 2010-03-31
Perhaps you can read out the SMART data, to look for any logs on the system failure?

---

### Post by john newbuntu on 2010-03-31
This could be a grub problem if grub is installed into the boot sector of a different partition.  Or it could be a filesystem problem.  As several of them suggested, I'd start with the "esfsck" from a liveCD:
sudo e2fsck -C0 -p -f -v /dev/sda5
presuming /dev/sda5 to be your linux partition.

If this is free, please post the output of meirfra's post so that others can look at it.
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/)

---

