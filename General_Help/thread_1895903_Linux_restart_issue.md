---
title: "Linux restart issue"
date: 2011-12-15
forum: General Help
---

### Post by sanityvoid on 2011-12-15
Hello everyone,

Recently I've been switching some older hardware to Linux. Ubuntu 10.04.03 LTS to be exact.

Anyway, I have numerous laptops switched over, and in doing this I told a co-worker I could get her older Dell working as if brand new.

Everything with the installation goes fine. Problem arises when you go to shutdown the computer. The desktop will not stay off. It just restarts no matter if you pick hibernate, suspend or shutdown. This is the only PC I've run into where this happens. 

I tried doing some google searches but I haven't come up with an answer. I've tried to reinstall a couple times. I've also tried the new Mint distro, but had no luck with that either.

Ideas or suggestions? If I've missed something in a search my apologies, and could you point out a thread?

Thanks so much.

1st post, woot!

---

### Post by astrognome on 2011-12-15
That is sure a strange one.  In the mean time, have you tried an alternative installation of ubuntu?

[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

---

### Post by Lars Noodén on 2011-12-16
Have you looked in the BIOS settings to see if there are any clues there?

---

### Post by sanityvoid on 2011-12-16
Yup, there is no bios setting. I've tried default and optimized settings. Nothing works. Has to be an ubuntu installation issue.

---

### Post by mxmcc on 2011-12-16
> **sanityvoid said:**
> Yup, there is no bios setting. I've tried default and optimized settings. Nothing works. Has to be an ubuntu installation issue.

I'm a new guy to ubuntu, but have some windows....the hardware problem may cause some very strange problems,  I have no good  idea,  bad idea is  making a link on the desktop of ubuntu to shutdown?

---

### Post by SlugSlug on 2011-12-16
try a bios update?

---

### Post by sanityvoid on 2011-12-16
I've tried to delete then add the shutdown functions on top, it was a no go. 

The bios is the latest released from Dell, I suppose I could try to do a reinstall of the bios.

Any other ideas?

---

### Post by sanityvoid on 2011-12-20
Ok I thought I'd give an update on what was happening with this.

I formatted the HDD and started over by putting winXP on the machine again. It worked perfectly and did not restart when I shut it down. It worked like a PC should.

I then tried to put 4 different linux distro's on the machine.

Mint 9, Mint 12, Ubuntu 10.04, Ubuntu 11.10

Nothing worked. Every single Linux distro had the same restart issue when shutting down. Shutdown, suspend, hibernate all resulted in the machine immediately restarting instead of staying 'down'.

Ideas or solutions anyone?

---

### Post by blackbird34 on 2011-12-20
Huh??
Tried shutting down with command line? 

```
sudo shutdown -h now
```

Good luck...

---

### Post by holycow131415 on 2011-12-20
Try a distro that is not *buntu based. Mint is *buntu based.

Opensuse, fedora, Mandriva.

---

### Post by sanityvoid on 2011-12-20
I'll try both of the last two replies. Thanks for the advice.

---

### Post by sanityvoid on 2011-12-21
Well, I tried Fedora and the command line. Neither worked. The machine still restarts after shutting it down. Very weird.

Regardless, I've settled on ubuntu 10.04 and a power strip to shut it down. Thanks for all the help.

---

