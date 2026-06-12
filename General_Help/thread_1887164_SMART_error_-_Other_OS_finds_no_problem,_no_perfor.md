---
title: "SMART error - Other OS finds no problem, no performance issues"
date: 2011-11-26
forum: General Help
---

### Post by Paperypip on 2011-11-26
I just installed Ubuntu yesterday and so far it's mostly working great with just one notable exception: The Disk Utility is giving me frequent warnings about my SSD. It tells me "THE DISK IS BEING USED OUTSIDE DESIGN PARAMETERS".

Here are some screenshots I took of Disk Utility:

[[img]http://i.imgur.com/kyADWs.png[/img]](http://i.imgur.com/kyADW.png)

Hovering over these failed test results tells me that the problems are due to age. This is a brand new drive.

[[img]http://i.imgur.com/5FPIWs.png[/img]](http://i.imgur.com/5FPIW.png)

I've noticed no performance issues with this drive whatsoever, and furthermore, the disk utility I use in Windows (booting from a different partition on the same drive) does not find any issues with this drive. What's going on here? Is this error the result of some quirk of how I've set up my system, or is there a genuine hardware issue here I didn't catch in Windows?

---

### Post by Paperypip on 2011-11-26
Hmmmm, scratch the "no performance issues". Throughout the day I've been noticing a lot of suspicious things like inexplicably corrupt downloads, the failure of various programs to open in both Ubuntu and Windows, etc. :???:

So, I'm given the error I posted about in Disk Utility in the first post which I find ambiguous and confusing, and the error isn't present when I use my SMART programs in Windows. There's an HDD installed alongside the SSD- every SMART program I run gives me a (not particularly urgent looking) warning about a few bad sectors (edit: *on the HDD*- only in Ubuntu am I getting any error messages about the SSD; Windows thinks there's some sector issues on the HDD but the SSD is running fine. This is why I'm not confident which drive is actually giving me issues.).

Are there any more detailed scans I should do to try to diagnose exactly what's going wrong? Both the SSD and HDD drive in this desktop are brand new and it shouldn't be a problem to take advantage of my warranty, it's just I don't want to replace both of them (and lose all my data on both of them- not the worst thing in the worst at this point since this is a new set-up but if I can spare myself that annoyance I will...) if there is an actual sever problem with only one of the drives.

If there's no more scans I can do I'm going to try removing one of the drives and seeing if I still see any errors.

---

### Post by LinuxFan999 on 2011-11-26
Solid state drives suck! They are terrible and unreliable. Back up your data and get a 1TB-2TB mechanical hard drive, which will be far more reliable.

---

### Post by Paperypip on 2011-11-27
Not really interested in debating the relative merits of the hardware; fact of the matter is right now I have a brand new HDD and a brand new SSD on this computer and one of them might be failing; how do I tell which one it is?

The inconsistent SMART results are still confusing me. I found a Windows program, HDDScan that can perform verify scans, read scans, erase scans, etc. on a hard drive though I'm not quite sure how useful the information I might get from that will be. Is there any software like this on Ubuntu?

Also a lot of hard-drive monitor software seems to prefer to scan the partition rather than the whole drive. Can I get around this?

My current plan is to make a catalogue of tasks this computer has had issues with and try em out with only the SSD installed, and if they work, I'll try making a bootable partition of some sort on the HDD and see whether that works fine.

---

### Post by Lampi on 2011-11-27
install smartmontools and run a long smart selftest on both drives, that should clear things up for you.

edit: hold that thought: what ubuntu are you using? smartmontools should be a recent enough version like 5.4 to have proper SSD support, it won't matter for the disk

---

### Post by Paperypip on 2011-11-27
I'm on Oneiric so I doubt there'll be an issue there. Thanks for the suggestion. :)

---

### Post by Paperypip on 2011-11-28
Mystery semi-solved; I updated the SSD drive's firmware and now Ubuntu's Disk Utility finds it to be in perfect health just like all the other HDD scanners I've tried on it. Turns out with the old firmware Ubuntu's Disk Utility and however SMART was configured for the SSD just didn't play nice together. Seems to be some genuine bad sectors on the HDD and I'm just testing to see how many of the odd errors I've been seeing have been attributable to those sectors. I've got a few hypotheses now that it could just be Windows being a pain about something else entirely.

So far in my dual-booted system Windows 7 has been by far the huger pain. Linux sure is making a great case for itself right now. :)

---

