---
title: "will I have problems with Flash if I install Ubuntu 64-bit?"
date: 2011-03-25
forum: General Help
---

### Post by nrundy on 2011-03-25
it appears to me that I'm unlikely to encounter very many problems running 64-bit Ubuntu (please correct me if I'm wrong). I've read that Flash can be a problem though. Anyone have experience? should i install 32-bit to avoid any problems?

What problems can I expect if I run 64-bit?

I will have 4GB of RAM. I want to have zero problems if possible. My understanding is that 32-bit will only allow me to use 3GB RAM for applications. But the 64-bit install will allow me to use all 4GB RAM for applications. I expect 3GB to be enough, but thought I'd ask since I'd gain 1GB from 64-bit.

---

### Post by Spyderkid on 2011-03-25
just install ubuntu restricted extras, flash works fine for me with that on 64bit.

---

### Post by ubudog on 2011-03-25
Yep, I think they've got that issue fixed now (10.10).  I'm not sure, but I think so.

---

### Post by ZJE123 on 2011-03-25
I am currently running a 64bit version of Linux (even though I only have 3gb of Ram) and I have had problems with Flash.  I had never heard of any problems with it, but I can't seem to get it to work in any web browser I've tried, I have created a thread about this problem about 10 minutes ago with no responses yet, but keep a look out here ([http://ubuntuforums.org/showthread.php?p=10600563#post10600563](http://ubuntuforums.org/showthread.php?p=10600563#post10600563)) to see if anyone answers.  I say that Ubuntu uses very little RAM (about 800 MB at most) so coming from someone with 3 GB of Ram, I say go with the 32bit, as 3.2 GB of Ram is plenty for Ubuntu, unless you plan on running many applications at once.

---

### Post by nrundy on 2011-03-25
have you tried "Flash-Aid" extension for Firefox?

It has helped me out with Flash stuff.

---

### Post by ZJE123 on 2011-03-25
> **nrundy said:**
> have you tried "Flash-Aid" extension for Firefox?

It has helped me out with Flash stuff.

Tried it and it didn't work for me, as nothing has.  Maybe I'm just unlucky with it:p.

---

### Post by nrundy on 2011-03-25
have u ever run 32-bit? didn't have problems then with 32-bit? are u sure its 64-bit related?

---

### Post by tgm4883 on 2011-03-25
> **ZJE123 said:**
> Tried it and it didn't work for me, as nothing has.  Maybe I'm just unlucky with it:p.

have you tried the 64-bit version of flash

---

### Post by ZJE123 on 2011-03-25
> **nrundy said:**
> have u ever run 32-bit? didn't have problems then with 32-bit? are u sure its 64-bit related?

I'm not 100% sure its 64bit related, but I did used to use the 32 bit version (off a flash drive) and had no problems then.  It's even worked on the 64bit version I currently use, but for some random reason, it has just stopped working for me.

---

### Post by ZJE123 on 2011-03-25
Here: ([http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)) I found a solution to my flash problems and maybe it will help anyone else who might have a problem or might potentially have a problem.

---

### Post by ZJE123 on 2011-03-25
> **tgm4883 said:**
> have you tried the 64-bit version of flash

Just did now, and it's been working ever since, thanks!  I didn't realize there was a 32bit and 64bit version of flash, I just thought it went with the operating system.

---

### Post by nrundy on 2011-03-26
When will Flash 64-bit-Stable be released? When it is, will it be a regular download like the 32-bit Flash is today?

---

### Post by oldos2er on 2011-03-26
> **nrundy said:**
> When will Flash 64-bit-Stable be released? 

You'd need to ask Adobe. Just a guess, but I'm sure it won't be anytime soon.

---

### Post by nrundy on 2011-03-27
does running 64-bit Flash player require using the 64-bit Browser? like for Firefox? or can 64-bit Flash run in a 32-bit browser?

It seems like hardly any browsers are 64-bit. Looks like this might be a headache.

---

### Post by Vaphell on 2011-03-27
hardly any? pretty much all are available in 64bit version for linux. Half-assed versioning for 32/64bit systems is a reality of windows universe.

in general it goes like this:
bits_of_system >= bits_of_firefox >= bits_of_flash

64bit system can run both 64 and 32bit software (64 by default), 64bit firefox can run both 64bit flash and wrapped 32bit flash (32 is default because 64 is considered beta). 32bit system can't run anything 64bit, same thing with 32bit browser.

---

### Post by oldfred on 2011-03-27
A nice comparison of the versions:

Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Essentially says if you can use the 64bit kernel you should.

---

### Post by Rob_H on 2011-03-27
> **nrundy said:**
> When will Flash 64-bit-Stable be released? When it is, will it be a regular download like the 32-bit Flash is today?

Adobe seems to run hot and cold on 64-bit Flash for Linux. They'll put out a "pre-release" version, everybody gets excited, then they abandon it for a long time (no security fixes), then the cycle repeats a year or so later. So while there is a 64-bit version of Flash, Adobe hasn't shown a strong commitment to keeping it updated.

---

### Post by nrundy on 2011-03-27
> **Vaphell said:**
> hardly any? pretty much all are available in 64bit version for linux. Half-assed versioning for 32/64bit systems is a reality of windows universe.

in general it goes like this:
bits_of_system >= bits_of_firefox >= bits_of_flash

64bit system can run both 64 and 32bit software (64 by default), 64bit firefox can run both 64bit flash and wrapped 32bit flash (32 is default because 64 is considered beta). 32bit system can't run anything 64bit, same thing with 32bit browser.

Thanks for letting me know. I went to Firefox website and couldn't find any download option for a 64 bit. I'm running 32 bit now, does it "sense" i'm 32 bit and not offer 64 bit because of this?

---

### Post by nrundy on 2011-03-27
> **Rob_H said:**
> Adobe seems to run hot and cold on 64-bit Flash for Linux. They'll put out a "pre-release" version, everybody gets excited, then they abandon it for a long time (no security fixes), then the cycle repeats a year or so later. So while there is a 64-bit version of Flash, Adobe hasn't shown a strong commitment to keeping it updated.

but I won't have any problems if I run 32 bit flash with a 64bit OS right?

---

### Post by Irony on 2011-03-27
Go here for 64 bit flash; [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

Simply unzip the flash download and put it in the appropriate place.

---

### Post by Rob_H on 2011-03-27
> **nrundy said:**
> but I won't have any problems if I run 32 bit flash with a 64bit OS right?

No, I can't confirm that. I have had stability and performance problems running 32-bit Flash under 64-bit Linux. I've stuck with 32-bit across the board as a result.

**BUT**, the good news is that you **CAN** take advantage of 4+ GB of RAM if you run 32-bit Ubuntu. The reason is the [PAE]("https://secure.wikimedia.org/wikipedia/en/wiki/Physical_Address_Extension") kernel, which enables you to access up to 64 GB or so of RAM in a 32-bit OS. On my 4 GB laptop, the **free** command shows a full 4 GB total RAM. So don't sweat it.

---

### Post by oldos2er on 2011-03-27
> **nrundy said:**
> It seems like hardly any browsers are 64-bit. Looks like this might be a headache.

Firefox, Chrome, and rekonq are all 64-bit. I haven't tried any others recently.

> but I won't have any problems if I run 32 bit flash with a 64bit OS right?

64-bit flash runs better for me than 32-bit + nspluginwrapper.

---

### Post by tgm4883 on 2011-03-27
> **Rob_H said:**
> No, I can't confirm that. I have had stability and performance problems running 32-bit Flash under 64-bit Linux. I've stuck with 32-bit across the board as a result.

**BUT**, the good news is that you **CAN** take advantage of 4+ GB of RAM if you run 32-bit Ubuntu. The reason is the [PAE]("https://secure.wikimedia.org/wikipedia/en/wiki/Physical_Address_Extension") kernel, which enables you to access up to 64 GB or so of RAM in a 32-bit OS. On my 4 GB laptop, the **free** command shows a full 4 GB total RAM. So don't sweat it.

While it is technially possible, if you have 64GB of RAM (or really anything above ~16GB) you should either probably should be running a 64-bit OS, or have way more RAM than you actually need.

---

### Post by nrundy on 2011-03-27
guys, can I expect the 64-bit Firefox to perform as well as 32-bit firefox? I've seen some contradictory benchmarks. Just wondering if I'll be taking a performance hit if I go 64-bit. Be nice to be able to use all 4GB of my ram.

---

### Post by nrundy on 2011-03-27
> **Irony said:**
> Go here for 64 bit flash; [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

Simply unzip the flash download and put it in the appropriate place.

Square hasn't been updated since Nov. 2010? I freaking hate adobe. It's a travesty we are forced to use their stinking software. Small programs that let me do Banking stuff for my credit cards won't even run without Flash.

---

### Post by Cracklepop on 2011-03-27
@OP, no you won't have problems.  Adobe has a 64 bit version of Flash [here]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz").

Download it, rightclick, extract the .so file, put the .so file in ~/.mozilla/plugins (go View > ShowHidden inside ~ to see .mozilla, and if there's no plugins folder then create one yourself).

All done. Restart Firefox.

---

