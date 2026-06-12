---
title: "How often does ubuntu update hardware drivers?"
date: 2010-02-19
forum: General Help
---

### Post by osomphane on 2010-02-19
Hello,

Just wondering if anyone knew how often the ubuntu team updates [restricted] hardware drivers.. In particular, I noticed that ATI has just released new drivers (9.12) and the ubuntu hardware drivers list 9.11. Also, if I have already enabled them, are they just going to update via update manager?

---

### Post by Pjotr123 on 2010-02-19
In Ubuntu 9.10, they'll probably stick to the current restricted ATI driver version. Why do you want to have the new one? Doesn't the current version work well?

---

### Post by osomphane on 2010-02-19
Honestly, I haven't tried anything other then installing Ubuntu 9.10 on this machine yet. The only problem I'm having is trying to access ATI CCC (administrative), which is saying that some folder or file does not exist.

The reason I'm asking is that other people have reported better performance and less bugs out of 9.12 and 9.13 beta...

---

### Post by Pjotr123 on 2010-02-19
OK... :)

I think you'll have to wait a couple of months, until 10.04 Lucid Lynx arrives. Lucid will probably have a newer driver version in the software repositories.

Ubuntu isn't a "rolling release", which means that application versions in an Ubuntu version stay the way they were at release date, unless security problems or stability problems arise.

---

### Post by osomphane on 2010-02-20
Is there something you could recommend that gets support that is as good as ubuntu?

---

### Post by 3rdalbum on 2010-02-21
> **osomphane said:**
> Is there something you could recommend that gets support that is as good as ubuntu?

Not really, but it's certainly not impossible to keep software up-to-date on Ubuntu. The main method is by using PPAs - they're little repositories maintained by individuals or even Ubuntu developers, that allow you to install later software.

I can't find an ATI driver PPA, but you might have more luck.

---

### Post by jocko on 2010-02-21
> **osomphane said:**
> ... I noticed that ATI has just released new drivers (9.12) and the ubuntu hardware drivers list 9.11. ..
The current driver on ati's website is 10.2 (february 2010), not 9.12 (december 2009).

> **osomphane said:**
> Honestly, I haven't tried anything other then installing Ubuntu 9.10 on this machine yet. The only problem I'm having is trying to access ATI CCC (administrative), which is saying that some folder or file does not exist.

The reason I'm asking is that other people have reported better performance and less bugs out of 9.12 and 9.13 beta...
I don't know where you get "9.13 beta" from, but since 2009 only had twelve months, I don't think there ever was a 9.13 release. And even if there was, it would be outdated by first the 10.1 (january 2010), then the 10.2...

Why not tell us the error message you get from cccle? Maybe someone knows how to fix it?

And if you really want to try the latest driver, get it from [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English"). Then find instructions [here]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually") (but note that the guide was written for jaunty and the 9.12 driver, so you may need to change some of the commands to get them to work properly with karmic and 10.2).

---

### Post by osomphane on 2010-02-23
Could not launch 'ATI Catalyst Control Center (Administrative)'
Failed to execute child process "amdxdg-su" (No such file or directory)
_C_lose

Solution @ [http://ubuntuforums.org/showthread.php?t=1260188&highlight=Failed+execute+child+process+amdxdg-su](http://ubuntuforums.org/showthread.php?t=1260188&highlight=Failed+execute+child+process+amdxdg-su)

---

### Post by Mark Phelps on 2010-02-24
> **osomphane said:**
> Hello,

Just wondering if anyone knew how often the ubuntu team updates [restricted] hardware drivers.. In particular, I noticed that ATI has just released new drivers (9.12) and the ubuntu hardware drivers list 9.11. Also, if I have already enabled them, are they just going to update via update manager?

Not to split hairs, but in this case, it's AMD/ATI that is actually doing the driver update.  The "Ubuntu team" will only be updating the open source drivers.

Also, if the drivers you looked at showed 9.12 as the most current, you likely looked at the Legacy drivers. Unless you have one of the newer HD 3x/4x/5x cards, the Legacy drivers are the only ones that will work with your card.  But, they won't work under recent Ubuntu versions (i.e., 9.04 or 9.10) ... and they've not been updated since last year.

---

### Post by philinux on 2010-02-24
> **osomphane said:**
> Hello,

Just wondering if anyone knew how often the ubuntu team updates [restricted] hardware drivers.. In particular, I noticed that ATI has just released new drivers (9.12) and the ubuntu hardware drivers list 9.11. Also, if I have already enabled them, are they just going to update via update manager?

If they were updating the driver it **might**, no guarantee mind, come through the backports.

Click the link in my signature.

---

### Post by osomphane on 2010-02-24
Actually I am not sure if I quoted the correct version of the hardware drivers. It says catalyst control center version 2.11. I am unsure which driver version it is compared to the ones from the ati website.

So if I got it right from the replies, the drivers I get when the "Hardware Drivers" icon on the ubuntu menu are maintained by ATI?

---

