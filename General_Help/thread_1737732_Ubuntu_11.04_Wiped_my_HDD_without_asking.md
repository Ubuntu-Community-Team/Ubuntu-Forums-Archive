---
title: "Ubuntu 11.04 Wiped my HDD without asking"
date: 2011-04-23
forum: General Help
---

### Post by Pacoup on 2011-04-23
Alright, so I was installing the Beta 2 of Ubuntu 11.04 and it asked if I wanted to install it side-by-side with Windows 7, so I click "Yes", and before I could react, without any prior confirmation, not even a show of the resulting auto disk partition layout, Ubuntu had partitioned and formatted my hard drives in the way it wanted without asking me and had started the installation.

Ok, so far so good. I thought to myself, well, I did choose to install SIDE BY SIDE, so in theory, it should not delete any data and just shrink my current Windows 7 partitions, or so I thought.

In reality, while Ubuntu did install Grub on the primary disk, the one with Windows 7 on it, it took one of my portal HDD that was attached via USB, formatted it and consequently wiped all of my data, and installed itself on that disk.

Am I happy? No. This has prompted me to step back on my decision of hosting my mission-critical Web servers with Ubuntu. The simple fact is, an installation should be simple, but not to the point of doing things that might not be wanted without telling the user. This is very un-Linux like.

I got taught never to trust the Windows installer and to always unplug any drive I do not want Windows to be installed on, but I never thought this could happen on Linux, especially not on Ubuntu, but I'm starting to comprehend why a large part of my Linux friends have left Ubuntu, myself not being a Linux geek, just a user out of curiosity and necessity (Web servers).

Fortunately, the format was a quick format, and I could recover most of my data after an NTFS file recovery in Windows, although some of it was lost because Ubuntu overwrote at least 7 GiB of my data, but I don't have any statistics on this yet as I'm still filtering through the incredibly long list of files that are now lacking a folder structure after recovery. Some folder-dependent works will be very hard or impossible to recover.

I also have backups of the really important stuff, so it's not like my whole digital life just went over, but I really didn't expect Ubuntu to screw up my video library.

In other words, here's my message: Fix this before 11.04's release! This is a crazy important implementation problem. Do you really think users will be willing to ever trust Ubuntu again if it wipes their HDDs clean without asking? No. Fortunately I blame myself more for using the automatic option than I blame Ubuntu and its developers for what it did, but it's not like I don't blame Microsoft for makings stupid OS installers as well.

Nevertheless, I have made my choice and gone back with Debian. I've been burned too many times with Ubuntu's UX decisions and have decided that this distribution is as good as dead to me unless it changes this very Apple-like tendency to design stupidity.

---

### Post by brpylko on 2011-04-23
It is a BETA, you might want to tell Canonical about this, but I would also think that maybe when you chose side-by-side it erased everything except the OS it was supposed to be side-by-side with. In the future, I would not use a beta as a server(If I understand correctly, that is what you are trying to do) I would use Hardy(the newest LTS version) or Karmic (The latest version that is as stable as one would want for uses other than testing, in my opinion).

EDIT: I think Karmic is the newest one without the so-called "Apple like tendencies"

---

### Post by Vaphell on 2011-04-23
in your scenario side by side sounds quite ambiguous. Technically, depending on definition it did what you asked for, because why resize partitions when there is one 'free', with enough space already? You got side-by-side (which can be in other words described as dual boot), don't you? 
Don't ever let installer do some automagical stuff if your partitions contain any valuable data you can't afford to lose. Software can do only so much when a lot of guesswork is included and results can be disastrous. If you want full control, go the manual configuration route - do the resizing yourself and carefully pick every partition by hand.

---

### Post by wilee-nilee on 2011-04-23
Read the post carefully with one bean, and the knowledge described in general; this is a troll post.

Or somebody unwilling to recognize user error.

---

### Post by drewsus on 2011-04-23
> **wilee-nilee said:**
> Read the post carefully with one bean, and the knowledge described in general; this is a troll post.

Or somebody unwilling to recognize user error.

I don't think they are a troll, but otherwise I think you are right. 
However, Canonical should definitely be more verbose in their warnings. They should definitely suggest that ppl remove external devices.

---

### Post by LowSky on 2011-04-23
You installed a BETA. You installed an Operating System with no implied or guaranteed warranty it would work correctly.

I miss the days when the Forums had huge banners telling people not to post questions  about development releases in the beginners or general help portions of the forums.


Betas  or even stable operating systems should not being installed on hard drives where data is critical. Further more all users should backup there data.

There is no way a install would erase two whole drives in an installation. unless the user set it to do so


> **brpylko said:**
> It is a BETA, you might want to tell Canonical about this, but I would also think that maybe when you chose side-by-side it erased everything except the OS it was supposed to be side-by-side with. In the future, I would not use a beta as a server(If I understand correctly, that is what you are trying to do) I would use Hardy(the newest LTS version) or Karmic (The latest version that is as stable as one would want for uses other than testing, in my opinion).

EDIT: I think Karmic is the newest one without the so-called "Apple like tendencies"


10.04 (aka Lucid Lynx) is the newest Long term support (LTS) version. LTS are no more stable than normal releases. The only differences is the length of the support. To add to that LTS only means support form canonical. The community, like ubuntuforums.org, are usually only helping the latest release as its user base is mostly using the newest.

---

### Post by Pacoup on 2011-04-24
Ok, so, a bit of specifics:
No, of course, I did not use Beta software on a server! This whole story happened on my desktop PC.

Also, I am not a troll; the incident actually happened and is problematic. Don't you think it would be nice to actually listen to problems and try to fix them instead of blaming of troll at every occasion anyone who has an issue with your product of choice? I would be very pleased to see the open source community more intent on user retention. The hostility is tiring. I would like to promote open source more in my life, but its very promoters don't seem intent on helping me do that at all.

I would also like to point out that this is not by any means User Error. The OS didn't ask me what I wanted to do, it just said it would auto-install side-by-side with Windows 7. Had the OS allowed me to review my partition layout first, and had I then realized the mistakes in the auto-partitioning, sure, I would call this an error on my own. After-all, there's a limit to what an automatic process can figure out, but this is precisely why it should not be that automatic, as in it should warn the user that some data might be lost and that is it highly recommended to review the partitioning layout.

As for the server issue, this is an entirely other ballpark. Yes, I agree Ubuntu is a solid server offering, but such a behavior in User Experience (my data wiping issue) when installing a desktop Ubuntu is, let's say, not the most encouraging experience one can have to promote using Ubuntu on the server as well.

For the record, we've always been on Debian before. We were just thinking of moving to Ubuntu but then this incident happened, and no one wants to touch Ubuntu again, fearing automated tools on the server could behave in unwanted way (this is not factual at all, I have no idea what tools exist on Ubuntu different than Debian, I'm not even the tech guy for servers within my organization).

---

### Post by samacaster on 2011-04-24
First: Ubuntu does offer the option of choosing your own partition layout. 

Install side-by-side
Erase and use the whole disk
Create your own partition

The third option would have allowed you to see the current partition scheme and adjust accordingly. Don't come in here screaming a bunch of rubbish because you couldn't take the time to read every option.

As for the hostility aspect its a bit deserved in this case. You came in here slamming Ubuntu and blaming it for everything. It did what you asked it to. Installed side by side. You didn't tell the installer specifically what partition to use. You obviously didn't see that option.

---

### Post by drewsus on 2011-04-24
Here is an idea: Ignore the ONE person that suspects you of being a troll and try not to dramatise it to seem like everyone and their grandmother is doing so. 
Everyone every time should backup their stuff before doing major updates/tinkering with partition tables. Most people learn this in a very similar fashion as you just have.

---

### Post by Timmer1240 on 2011-04-24
If it makes you feel any better I wiped out my win 7 and ubuntu install a couple months ago trying to triple boot with Linux mint debian OH WELL my bad!luckily all my files are backed up so no big deal but these things happen!

---

