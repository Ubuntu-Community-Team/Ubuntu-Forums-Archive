---
title: "Dual Booting Win 7/10.04."
date: 2010-09-22
forum: General Help
---

### Post by Roasted on 2010-09-22
I think this is a Windows problem, but I'm curious if any users can fill me in on what happened. I got new hard drives in so I began my transformation of Vista/10.04/500gb drive to Win 7/10.04/1TB drive. I installed Win 7, got all the updates, and 5 hours later was able to reboot. Okay fine. I install Ubuntu, do my thing, okay fine. I go to boot back to Win 7 and it errors out with 0xc000000e. It's non bootable. Even the super grub boot cd wouldn't boot it.

Does Win 7 hate 10.04 or something?

---

### Post by bryanfblareunion on 2010-09-22
I use Windows 7/10.04 boot on my laptop and it works fine. That sounds like it may be a hard drive problem? Not sure what that error code is. Might want to search Microsoft.

---

### Post by Roasted on 2010-09-23
Well here's what happened tonight, so if anybody can clue me in on what the potential issues were, I'd like to hear it.

I was running a single drive with Windows 7. I then installed Ubuntu. Afterwards I plugged in my backup drive, a 500gb internal SATA drive to SATA port B, and pulled my data off of it to the main drive I just installed. Then I rebooted and Windows 7 bombed out. Did Win 7 bomb because of the hard drive? I find it extremely doubtful.

I ended up doing a repair of Windows 7, bringing back boot functionality but removing Ubuntu's boot functionality. I then went to Ubuntu on a LiveCD and restored Grub2. Things worked great after that. Windows and Linux both boot without issue now.

I have to wonder, what in the world happened? Could the hard drive I added have been the breaking point? I don't understand how adding other hard drives would make something like Windows 7 act up. Windows 98 maybe, but why 7? 

Anyway, if anybody has anything else to add, I'd love to hear it. but my actual boot issue between 7 and Ubuntu is fine. Has anybody else had flawless (or problematic) Win 7/Ubuntu dual boot setups?

---

### Post by Mark Phelps on 2010-09-23
What happened to you is a typical experience when folks use Gparted to shrink the Win7 OS partition and/or allow the Ubuntu installer to do the same with a side-by-side installation. All to often, this renders the Win7 OS unbootable -- and it takes running Startup Repair to reinitialize the Win7 boot loader to get it working again.

That's the more typical problem...

If you used the Win7 Disk Management utility to shrink the Win7 OS partition (the RIGHT way to do this), and you STILL had the same problem ... sorry ... don't have any explanation for that situation.

---

### Post by Roasted on 2010-09-23
> **Mark Phelps said:**
> What happened to you is a typical experience when folks use Gparted to shrink the Win7 OS partition and/or allow the Ubuntu installer to do the same with a side-by-side installation. All to often, this renders the Win7 OS unbootable -- and it takes running Startup Repair to reinitialize the Win7 boot loader to get it working again.

That's the more typical problem...

If you used the Win7 Disk Management utility to shrink the Win7 OS partition (the RIGHT way to do this), and you STILL had the same problem ... sorry ... don't have any explanation for that situation.

I didn't use GParted. It was a brand new disk, straight out of the box unformatted. Put in PC, booted to Win 7 CD, added 120gb partition, left the rest untouched. Installed. Etc.

Fricken Winders... it just had to be a brat.

---

