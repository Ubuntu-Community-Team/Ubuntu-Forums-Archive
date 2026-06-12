---
title: "Looking to Build an Anti-Virus Linux (for Use With Other Computers)"
date: 2011-08-13
forum: General Help
---

### Post by dniMretsaM on 2011-08-13
Ok, so I want to make a anti-virus Linux to put on a USB drive for use with other computers that have viruses. The only problem is I have no idea how to do this. CLI-only should be fine (if there are any CLI anti-virus programs). So is there something I can get that's already made for this or should I get a regular distro and remove everything I don't want and install what I do? What tools should I get.? Any help would be greatly appreciated! Also, a link to instructions on installing on a USB drive would be helpful (I also plan on putting some LiveUSB's on the same drive, so if the guide included setting up multi-boot that would help a lot).

---

### Post by Primefalcon on 2011-08-13
install ubuntu to a usb stick and keep extra space aside for install stuff...

then simply install clamav and clamtk (the gui for clamav)

for making liveusb's and the such a program called unetbootin rocks!

---

### Post by haqking on 2011-08-13
> **dniMretsaM said:**
> Ok, so I want to make a anti-virus Linux to put on a USB drive for use with other computers that have viruses. The only problem is I have no idea how to do this. CLI-only should be fine (if there are any CLI anti-virus programs). So is there something I can get that's already made for this or should I get a regular distro and remove everything I don't want and install what I do? What tools should I get.? Any help would be greatly appreciated! Also, a link to instructions on installing on a USB drive would be helpful.


any particular reason you want to use Linux with it ?

Why not just take a AV boot disk of which there are many ?

[http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/](http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/)

But you could download and install Ubuntu onto a USB key and install AVG or Avast or Clam AV if you wanted to

---

### Post by Primefalcon on 2011-08-13
> **haqking said:**
> any particular reason you want to use Linux with it ?

Why not just take a AV boot disk of which there are many ?

[http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/](http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/)

But you could download and install Ubuntu onto a USB key and install AVG or Avast or Clam AV if you wanted to
well with linux you could install gparted as well as other aps and have a complete tools disk...

though systemrescuecd kind of already does this

---

### Post by snip3r8 on 2011-08-13
As far as i know clamav can run a command line scanner:
[http://www.clamav.net/lang/en/](http://www.clamav.net/lang/en/)

I think it will be easier though to just use an ubuntu distro and remove what you dont need because ubuntu is really easy to get working on a flash-drive

---

### Post by haqking on 2011-08-13
> **Primefalcon said:**
> well with linux you could install gparted as well as other aps and have a complete tools disk...

though systemrescuecd kind of already does this


Of course.  I just wandered why a AV rescue CD which already exists wont do what he wants

---

### Post by dniMretsaM on 2011-08-13
Thanks for all the replies, I'll look into them. Also, I want it to be as small as possible (that's why I want CLI only if possible), so what are the smallest of the AV programs mentioned?

> **haqking said:**
> any particular reason you want to use Linux with it ?

Why not just take a AV boot disk of which there are many ?

[http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/](http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/)

But you could download and install Ubuntu onto a USB key and install AVG or Avast or Clam AV if you wanted to

Well, a few reasons. One has already been mentioned by Primefalcon.  Another reason is because if I help somebody with their computer using  it, it will put Linux in a good light and may encourage them to try  it out. Also, I want it to be small and Linux can be very small (Slitaz  is 30mb, that's pretty darn small).

---

### Post by Primefalcon on 2011-08-13
> **snip3r8 said:**
> As far as i know clamav can run a command line scanner:
[http://www.clamav.net/lang/en/](http://www.clamav.net/lang/en/)

I think it will be easier though to just use an ubuntu distro and remove what you dont need because ubuntu is really easy to get working on a flash-drive
Sure it can.... actually clamav is fully command line.... clamtk nothing but a front end for it....

freshclam via root to update and clamscan to scan.... but a lot of people aren't comfortable with the CLI ;-) so I prefer to give GUI front-ends as well if available....

---

### Post by dniMretsaM on 2011-08-13
> **Primefalcon said:**
> Sure it can.... actually clamav is fully command line.... clamtk nothing but a front end for it....

freshclam via root to update and clamscan to scan.... but a lot of people aren't comfortable with the CLI ;-) so I prefer to give GUI front-ends as well if available....

I'm pretty geeky so I don't mind the CLI too much. Plus I want to get more comfortable with it, so I try to use CLI apps if I can. Anyway, looking into the various AV programs that have been mentioned. So any ideas on how to keep this as small as possible?

---

### Post by Primefalcon on 2011-08-13
I heard about a ?core installer? for Ubuntu that installs the absolutely bare minimum. Let me do a quick search before I hit reply on here......

ahh here. I think this is it... [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

and install what you need from there... thats of course shot of doing it on top of something like Arch Linux, tiny core, dsl, puppy or some such. but hell Ubuntu with 19mb isn't too bad....

for minimal space as well as a decent UI I'd probably say go puppy, it even supports Ubuntu's deb packages

---

### Post by Primefalcon on 2011-08-13
sorry wrong link... [https://wiki.ubuntu.com/Core](https://wiki.ubuntu.com/Core) doesn't seem to be out yet.... so just try the other suggestions for now such as puppy or such, lubuntu be a decent go too

---

### Post by bodhi.zazen on 2011-08-13
> **haqking said:**
> any particular reason you want to use Linux with it ?

Why not just take a AV boot disk of which there are many ?

[http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/](http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/)

I agree with this. Linux does not really have the tools to do what you are wanting.

Many of the antivirus apps on Linux are going to give you false positives, and your only option of managing anything you find will be do delete it. You can not edit the windows registry or easily re-install bhe bios from Linux.

Most linux antivirus is designed to be run on file or mail servers and watch of incoming infected files, not clean an infected system.

I do not think a linux live CD is the best tool for cleaning windows of viruses, keyloggers, or other malware.

---

### Post by dniMretsaM on 2011-08-13
> **bodhi.zazen said:**
> I agree with this. Linux does not really have the tools to do what you are wanting.

Many of the antivirus apps on Linux are going to give you false positives, and your only option of managing anything you find will be do delete it. You can not edit the windows registry or easily re-install bhe bios from Linux.

Most linux antivirus is designed to be run on file or mail servers and watch of incoming infected files, not clean an infected system.

I do not think a linux live CD is the best tool for cleaning windows of viruses, keyloggers, or other malware.

Ok, what would you recommend for a small rescue CD? And what are rescue CD's running(Linux, BSD, or whatever)? I know they have to run something.

---

### Post by bodhi.zazen on 2011-08-13
> **dniMretsaM said:**
> Ok, what would you recommend for a small rescue CD? And what are rescue CDs' running(Linux, BSD, or whatever)? I know they have to run something.

Depends on the rescue CD I suppose, I know some people who feel the Fedora 15 DVD is a "rescue CD".

Other then that I do not really know as I do not run windows, perhaps someone else might know.

You could always download the CD, mount the iso, and look at the kernel.

---

### Post by Primefalcon on 2011-08-13
I don't know about the virus part since you can install avg, avast and whatever on Linux, even nod32 has a Linux one.

Honestly though I just use clamav myself (it really does work well) for checking for viruses whenever  I pass files to windows users...

You can actually edit the registry: [http://lifehacker.com/5584762/edit-the-windows-registry-from-a-linux-thumb-drive](http://lifehacker.com/5584762/edit-the-windows-registry-from-a-linux-thumb-drive)

As for the bios there's quite a few ways to do it... [http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

The reason though I like linux its a full gui (if you want it) for copying and saving files (if your main os wont boot), you can scan, repartition using gparted, or whatever else...

It does make for a pretty full featured tool not to mention it can read pretty much any filesystem out there....

---

### Post by dniMretsaM on 2011-08-13
I'm thinking Puppy might be the way to go. It's only 100 MB when installed on a USB drive and I'm sure I can trim that down some more by removing various things that won't be necessary (like media stuff). And I'll probably be using Clam AV as it is open source (software freedom is pretty important to me) and is CLI. I'll probably start putting it together tomorrow (along with my other LiveUSBs). Thanks for all the help guys! I really appreciate it. One thing about this forum, there is always somebody ready to help.

---

### Post by Primefalcon on 2011-08-13
Yeah a modified puppy is the way I go myself, plus its easy to make your own repins of it.

btw it runs entirely in ram so it's fast as hell....

---

### Post by haqking on 2011-08-13
> **dniMretsaM said:**
> Ok, what would you recommend for a small rescue CD? And what are rescue CD's running(Linux, BSD, or whatever)? I know they have to run something.

When you say rescue CD are you referring to what i originally said which was a AV scanner boot disk ?

If so see the link i orginally provided, it is far better IMO if you just boot the infected machine to a AV scanner such as Kaspersky Live CD or any others from the link i provided, scan, repair, reboot.

Thats why they make them, most scanners offer a bootable disc version

---

### Post by bodhi.zazen on 2011-08-13
> **Primefalcon said:**
> You can actually edit the registry: [http://lifehacker.com/5584762/edit-the-windows-registry-from-a-linux-thumb-drive](http://lifehacker.com/5584762/edit-the-windows-registry-from-a-linux-thumb-drive)

Just curious, have you ever booted any linux live CD and actually cleaned the windows registry of malware?

Possible to edit the registry is not the same thing.

It is not so easy.

> **haqking said:**
> If so see the link i orginally provided, it is far better IMO if you just boot the infected machine to a AV scanner such as Kaspersky Live CD or any others from the link i provided, scan, repair, reboot.

Thats why they make them, most scanners offer a bootable disc version

+1 , best advice on this thread.

---

### Post by Primefalcon on 2011-08-13
> **bodhi.zazen said:**
> Just curious, have you ever booted any linux live CD and actually cleaned the windows registry of malware?

Possible to edit the registry is not the same thing.

It is not so easy.



+1 , best advice on this thread.
Frankly IMO if you have a virus that's gotten into the registry, fact is that getting it out of dll's as well as registry entries is probably a lost battle anyhow without ruining the system (not to mention that the system couldn't be completely trusted to be virus free anyhow)...

Not to mention the fact that if it's trying to hide itself in places there's probably rootkits and whatever else involved... best solution at that stage is a format and reinstall of windows, and hope to heck that the virus hasn't infected your graphics cards firmware at which staged your screwed without replacing hardware or doing a direct connection which involves soldering a cable to your circuit board...

---

