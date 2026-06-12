---
title: "Wiping a new hard drive"
date: 2010-12-22
forum: General Help
---

### Post by jsvidyad on 2010-12-22
Hello,

   I recently read that a few years back, new hard drives shipped with a virus(Look here: [http://www.infoworld.com/d/security-central/seagate-ships-virus-laden-hard-drives-119](http://www.infoworld.com/d/security-central/seagate-ships-virus-laden-hard-drives-119) ) . Now, my question is, do we need to wipe out brand new hard drives purchased from computer stores? If yes, how do we go about doing it? Is it enough if we just wipe out the storage areas of the drives? They also have a buffer area which has some storage capacity. How do we ensure that there is no malware in there?

---

### Post by WorMzy on 2010-12-22
So long as you don't buy your new hard drive(s) from Seagate three years ago, I think you'll be fine.

If you're insanely paranoid, you can run

```
dd if=/dev/zero of=/dev/sd#
```

to wipe a drive (replace sd# with your new drive's identifier).

---

### Post by wilee-nilee on 2010-12-22
> **jsvidyad said:**
> Hello,

   I recently read that a few years back, new hard drives shipped with a virus(Look here: [http://www.infoworld.com/d/security-central/seagate-ships-virus-laden-hard-drives-119](http://www.infoworld.com/d/security-central/seagate-ships-virus-laden-hard-drives-119) ) . Now, my question is, do we need to wipe out brand new hard drives purchased from computer stores? If yes, how do we go about doing it? Is it enough if we just wipe out the storage areas of the drives? They also have a buffer area which has some storage capacity. How do we ensure that there is no malware in there?

What are you planning to install on it?

Is it a external HD?

Your link is not to the actual article.

To be honest thats a MS skewed site anyway.

---

### Post by jsvidyad on 2010-12-22
I am planning to install ubuntu 9.10 64 bit version on it. I had the same (in a dual-boot situation) on my earlier hard drive. I have decided to leave out windows because of a boot-sector virus scare that I had. I even flashed my BIOS to ensure that it wasn't infected. 

  Anyway, because of all the above experiences, I am a bit ultra-sensitive to the possibility of any malware infection.

  I am going to use it as the only internal drive on my laptop.

---

### Post by jsvidyad on 2010-12-22
I forgot to mention that my new hard drive is also from seagate.

---

### Post by wilee-nilee on 2010-12-22
> **jsvidyad said:**
> I am planning to install ubuntu 9.10 64 bit version on it. I had the same (in a dual-boot situation) on my earlier hard drive. I have decided to leave out windows because of a boot-sector virus scare that I had. I even flashed my BIOS to ensure that it wasn't infected. 

  Anyway, because of all the above experiences, I am a bit ultra-sensitive to the possibility of any malware infection.

  I am going to use it as the only internal drive on my laptop.

9.10 is end of life April 2011, probably not a good choice. f your just going to use it a internal what ever you install to it will overwrite the mbr and the rest to.

I really doubt that a new HD is going to be infected and even so a install would make it null and void.

---

### Post by jsvidyad on 2010-12-22
You are saying that just an ordinary install of ubuntu will wipe the entire hard drive clean? 

Is there any possibility of malware hiding in the 16MB buffer(cache) of the hard drive?

---

### Post by wilee-nilee on 2010-12-22
> **jsvidyad said:**
> You are saying that just an ordinary install of ubuntu will wipe the entire hard drive clean? 

Is there any possibility of malware hiding in the 16MB buffer(cache) of the hard drive?

I doubt it.

---

### Post by jsvidyad on 2010-12-22
Hello,

   I didn't get what you meant to say. Are you saying that you doubt that a normal installation of ubuntu will wipe the entire hard drive clean? Or did you mean to say that you doubt that there will be any malware in the buffer area of the hard drive?

Is it worth the while trying to wipe the new hard drive using dd? If so, how would I go about it?

---

### Post by wilee-nilee on 2010-12-22
I think your being paranoid install to the disc and get it over with. You have very little to worry about here, a new HD and a operating system that is not the same as MS.

Ubuntu has the root locked with a password, the only way anything could get in is with user error, basically, and even then not hardly anything will actually work. Yes there are cross platform rootkits and flash stuff, but they need root access and you have little to worry about.

Yeah yeah I know you code freaks think you can hack into Linux but it is a waste of time for many reasons. :)

66% percent of the servers on the web run a variant of Unix or BSD or Linux...etc open source or like open source, Google runs Linux Relax and enjoy the safety.

---

### Post by CharlesA on 2010-12-22
If you overwrite a drive, there is no way anything will still be on the drive.

IMO you are being a bit paranoid. A "news" story from 3 years ago is hardly newsworthy now.

Regardless, if you install Ubuntu to a hard drive, it'll format the drive and install it there.

---

### Post by jsvidyad on 2010-12-22
Thanks for the Info:D

---

### Post by jsvidyad on 2011-04-23
Sorry to post to this thread again. But, I wanted to know if anyone had some advice to give regarding this.

---

### Post by CharlesA on 2011-04-23
If it's that much of a problem, just run DBAN or dd on the drive.

[http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux](http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux)

**Note: Both destroy data, so be careful when running them.**

---

### Post by jsvidyad on 2011-04-23
Hello,

  Its not that its much of a problem. My question is just whether its something that needs to be done from a security point of view. For example, will a government dept. wipe new drives before using them? 

  Earlier posts in this thread had said that installing ubuntu will wipe the drive. But, from what I have read on some other web sites, I got the idea that formatting the drive before installing ubuntu only changes the partition table and does not actually do anything to the partitions. Any comments about this?

  I am worried about this because of a boot sector virus scare I had earlier. I can always wipe the boot sector first. But, I am a little bit worried that if there is malware somewhere other than on the boot sector(MBR), will that be removed when installing ubuntu? 

Also, I haven't decided whether to dual boot with windows 7. So, I am even more worried about the possibility of malware.

---

### Post by |{urse on 2011-04-23
If you want to know there absolutely positively nothing but layer upon layer of 0's on that drive use Darin's boot and nuke.

[www.dban.org/](www.dban.org/)

It is complete overkill on a brand new disk though.

---

### Post by jsvidyad on 2011-04-23
So, what do you think should be done to a brand new hard disk before using it?

---

### Post by WorMzy on 2011-04-23
Well, I just bought a new terabyte drive. I just connected it up, changed the partition table to GPT, then created two XFS partitions. So far my PC hasn't exploded or been kidnapped by ninja toasters, so I think we'll mark that up as a success.

---

### Post by jsvidyad on 2011-04-23
So, you are saying that its not necessary to wipe a new hard drive clean before using it?

---

### Post by PhillyPhil on 2011-04-23
No, not necessary.  You are being paranoid.  But overwrite the whole thing with dd if it makes you feel better.
Re your older posts, the virus you linked to is Windows software not Linux, and I assume your disk cache is volatile, so nothing can be in there.

---

### Post by Jerry N on 2011-04-23
> **jsvidyad said:**
> So, what do you think should be done to a brand new hard disk before using it?

Connect it to your computer

Jerry

---

### Post by jsvidyad on 2011-04-23
> **PhillyPhil said:**
> No, not necessary.  You are being paranoid.  But overwrite the whole thing with dd if it makes you feel better.
Re your older posts, the virus you linked to is Windows software not Linux, and I assume your disk cache is volatile, so nothing can be in there.

The thing is, I might make it a dual boot system with windows 7. That makes me even more concerned about any possible malware.

---

### Post by dcstar on 2011-04-24
> **jsvidyad said:**
> So, you are saying that its not necessary to wipe a new hard drive clean before using it?

You can effectively "wipe" any drive by using gparted to write a new partition table to the drive - it will take a couple of seconds.

---

