---
title: "possible kernel bug - multiple mail clients crashing ubuntu 10.04"
date: 2010-08-18
forum: General Help
---

### Post by dewdrop_world on 2010-08-18
Over the past week or so, I've posted a few message about what looked like general stability problems in lucid, then problems specifically with Thunderbird.

Today I found it isn't just Thunderbird. I tried Claws Mail and Kmail, and all of them exhibit the same symptoms as Thunderbird:

- The app randomly hangs, crashes or stops connecting to the mail server.

- Quitting the app randomly takes down other applications. (Uh-oh -- modern OSs are supposed to prevent one application from corrupting another.)

- Once the problems start, any application is likely to have stability problems -- e.g., this morning, when Kmail started buggering up, I launched the software center to uninstall it and the window never appeared. A box showed up in the window panel at the bottom of the screen at first, but when it was time to draw the window, kaboom.

(I'm currently not using Evolution because of issues with syncing message deletion back to the server. Plus, at least once, Evolution lost its connection to the mail server. I don't remember serious instability with it, but I wasn't looking for the instability either. It might well be just as bad as the others.)

So, we have an issue triggered by multiple applications, and the issue is not limited to one unstable process on the machine (one unstable process makes other processes unstable). *That smells like a kernel bug.*

I'm wondering if anyone else has seen anything like this? I'm using the amd64 version on a MSI A6200, Intel Core i3 processor. I'll have to doublecheck the kernel version. When I installed the OS, it was (something-something).21 and now (after the first round of automatic system updates) it's .24 - "something-something" is whatever the standard kernel is when you download the amd64 CDROM image.

As long as I'm not running a mail client (apparently, any mail client), the system is stable. So it looks very much like there is something that mail clients do, which other applications tend not to do, which is broken.

I'll file a bug report if need be, but it would help to have some advice on how to make the report more specific.

James

---

### Post by oaxacamatt1 on 2010-08-18
Hmmm... 
It almost sounds like a hardware issue to me.  Have you tried getting the liveCD and running an FSCK on you hd?  It almost sounds like an intermittant hardware related bug.  I might try to follow up that issue too.
Cheers,
Matt

---

### Post by dewdrop_world on 2010-08-18
If it's an intermittent hardware problem, I don't understand why *it never happens* when I'm not using a mail client. If I don't launch a mail client, I have NO crashes, NO apps vanishing, NO kernel panics, everything is good.

Hardware issues would affect all apps, right?

Maybe it's not the kernel - maybe it's some daemon that mail clients use, but other software doesn't.

James

---

### Post by dewdrop_world on 2010-08-19
> **oaxacamatt1 said:**
> Have you tried getting the liveCD and running an FSCK on you hd?

fsck reports /dev/sda7 (my linux boot partition) is clean (running from liveCD).
James

---

### Post by dcstar on 2010-08-19
> **dewdrop_world said:**
> If it's an intermittent hardware problem, I don't understand why *it never happens* when I'm not using a mail client. If I don't launch a mail client, I have NO crashes, NO apps vanishing, NO kernel panics, everything is good.
........

And what do **all** mail clients use?.... oh yeah, the network.....

---

### Post by dewdrop_world on 2010-08-19
> **dcstar said:**
> And what do **all** mail clients use?.... oh yeah, the network.....

Firefox also uses the network, but it doesn't make my system unstable. I can leave gmail open for hours while doing other stuff, no problems.

So far, it's ONLY mail clients. I haven't tried IM clients yet, though.

James

---

### Post by dewdrop_world on 2010-08-24
>bump<

Since the latest, I've turned on keyboard shortcuts in gmail's web interface. That's fairly usable, actually (except that I had to disable the Firefox Ubuntu modifications plug-in, which appears in other online discussions to cause more problems than it solves). Close enough for now -- I hated having to use the mouse to navigate through my mail, but now I don't have to. I can live with it.

So, quick summary --

Network apps that make my machine unstable:

Thunderbird
Claws Mail
kmail

Network apps that don't cause stability problems:

Firefox
Skype
Empathy (not used much, but seems at first to be OK)

I don't know... maybe I should just submit a bug report. I've posted a few questions on these forums but this is the only thread where I've ever received a reply. And, the replies here have been good "rule out the basics" thoughts but have stopped short of a solution.

I'd really appreciate some help. I prefer using a proper mail client but so far I can't.

Thanks,
James

---

### Post by dewdrop_world on 2010-09-05
Bump... I've recently found, Firefox makes it unstable too, but only when downloading big files.

(But, Skype also brings in a ton of packets and I've yet to see it make other apps crash.)

I still would very much like to have a solution to this. Ultimately this bug will drive me to a different linux distro. Totally unacceptable for long term use.

Anybody reading?

James

---

### Post by davidmohammed on 2010-09-05
sure - try another distro.  But what you have described indicates a network issue.  Maybe a hardware issue.

Two ways to resolve this - try a different kernel.  Either an older kernel, or obviously a newer kernel.

Second - connect using a different network port e.g. wireless if you are using wired, or wired if using wireless.

Give the "newer" kernel idea a try.  Download the latest 2.6.35 kernel from [here]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds") (you need to download 3 deb files and install them).  If this doesnt work, the strong indication is that your issue is a hardware problem.

---

### Post by dewdrop_world on 2010-09-05
Before I do something to the install - these debs, right? Just want to avoid messing something else up :)

linux-headers-2.6.35-02063504-generic_2.6.35-02063504.201008271919_amd64.deb
linux-headers-2.6.35-02063504_2.6.35-02063504.201008271919_all.deb
linux-image-2.6.35-02063504-generic_2.6.35-02063504.201008271919_amd64.deb

(Intel core i3, I installed ubuntu amd64 initially)

It's a dual boot system with win7, no problems with large downloads in that other OS, which makes me think maybe not hardware.

James

---

### Post by davidmohammed on 2010-09-06
Yes those look fine.  After installing - reboot.  You'll notice the new kernel appearing in your grub list of kernels.  Boot with this new kernel.  If you have any issues, just boot with your old lucid kernel.

---

### Post by dewdrop_world on 2010-09-07
Well, I've never been to Egypt, but it seems I know a thing or two about De Nile.

I said Windows was working okay based on an attempt to download a large file where Firefox was not croaking. Lately I've had to use some Windows-specific software more often, and it became clear real fast that the system is only stable... wait for it... *when the network is not plugged in*.

So, lots of different software and *two* operating systems that go terribly unstable when the network is in use... it sounds more and more like a hardware problem all the time.

That should be an adventure -- I'm sure the machine is under warranty, but I bought it in the US and relocated to China for work. I really hope it can be done without overseas $$$$hipping charge$$$... well, one step at a time.

Sorry for being a bit dense about the hardware angle -- the full scale of the problem revealed itself only gradually -- in the meantime, I still have a working Mac system and I can use this machine productively by limiting its online time (and rebooting early and often).

Thanks,
James

---

### Post by dewdrop_world on 2010-09-26
Closing the loop -- I haven't done any kernel updates (no time), but based on a suggestion from another forum, I ran memtest from the GRUB menu this morning and found that at least one of the memory chips in my machine is defective. As I think about it, that would explain all the symptoms.

Why mail clients? They often have bigger memory footprints, more likelihood of hitting bad memory areas.

Why large file downloads (including packages and system updates)? They cause the file system cache to grow.

Why more often in Windows than Linux? Redmond bloatware, of course!

I'll have to limp along for a few more weeks until a major project is finished. Then it's off for warranty service to get the memory replaced.

Thanks again to everyone who answered.
James

---

