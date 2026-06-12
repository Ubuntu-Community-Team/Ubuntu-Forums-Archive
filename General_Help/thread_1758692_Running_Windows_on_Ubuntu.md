---
title: "Running Windows on Ubuntu"
date: 2011-05-14
forum: General Help
---

### Post by PsyclonJohn on 2011-05-14
I used to run duel boot and use Ubuntu through Windows, but I eventually got rid of Windows because the file system went corrupt. 

Is there a way to run Windows through Ubuntu?

---

### Post by 3 frags left on 2011-05-14
If you mean by using virtual machines, yes, there is. You can install VirtualBox for that. TO get it, just type in the console *sudo apt-get install virtualbox-ose* or get the package VirtualBox through Ubuntu Software Center. If you need any help on installing a Virtual Machine, PM me so I'll answer you in this thread.

---

### Post by PsyclonJohn on 2011-05-15
Will it perform like a normal Windows installation? I only want to use windows for FL Studio 10 and when I install FL Studio on Ubuntu it goes pretty slow. I'll give VirtualBox a try though, thanks!

---

### Post by pSYcl0Ne on 2011-05-15
VirtualBox is pretty cool, you need to delligate a portion of your ram to it, but guest editions makes it seem like your actually running windows when in seamless mode

---

### Post by Duncan Williams on 2011-05-15
I had the same issue as the op.
I had an extensive constantly updated with lots of tools and software windows XP (sp-3) system.
This was booting and using > Microsoft Security Essential,Immunet Protect (A.V), comodo firewall, network monitor and a few other `necessities'.
It took ages to boot up and shut down and I was still getting trojans and malware issues. Plus XP is getting a bit dated and it was slow due to all the never ending updating software, security patches, service packs, etc.

So, I decided to try Ubuntu a few months back and installed maverick with dual boot.
After a month I found that I hardly ever used windows,but all my mp3's, mp4's, photos.. etc were still on my windows partition as that way I could access them from both ubuntu and windows.

Then, I bought a new video card to update ubuntu (as was having probs with old nvidia card) and in amongst that **lost track of both windows and ubuntu** (no grub).

After using [_supergrub2_]("http://www.bootproblems.com/"), I was able to boot from supergrub CD and access grub.
So I went into windows and backed up all my media and other stuff (50gig) onto a spare hard drive. Luckily most of my data is in the cloud.

After stashing away my spare hard drive for fallback.
I downloaded Ubuntu 11.04 (natty) and copied it to cd.

After formatting my main hard drive, I installed windows XP from original CD.How fast it is from scratch.
I installed **latest** `ati catalyst' for my new (for me) Radeon HD 3650-512mb graphics card, Sound drivers for my 5.1 surround card, drivers for my AOC 24" monitor, VIA drivers for my motherboard chipset and a **few** other things, like direct X 9.c, VLC, flash, ccleaner, chrome, etc.

Ok this is one fast, lean, multimedia/games setup.
I used ati control center to overclock my graphics card and set the refresh to 75hz. 
**It is no use for internet or business stuff.** 
(**no** security/service packs, anti-virus protection, firewall, office software)
Using windows software tools to **[*clean out*]("http://my.opera.com/internetsecurity/blog/2011/02/23/free-anti-malware-and-other-applications")** unused software, backup files, caches, temp files, registry errors, etc. tweak swap-file, temp settings.
> Boots in less than a minute. Can use immediately (no background tasks) with full memory and cpu use.

Then, Installed Ubuntu Natty from cd, as dual boot (40 gig partition).
Installed ati catalyst 11.5 drivers, Updated natty via `update manager' (350mb)to current build.

Ok, after that I had my **new** dual boot setup.
> ubuntu unity
> windows XP

After setting up chrome on both setups. I added all my extensions back (synced bookmarks, lastpass(password manager), etc).
All my documents and web related pictures etc are stored in [_googledocs_]("http://www.google.com/google-d-s/tour1.html")
All my media files and other stuff is available through both setups on my windows partition (which is backed up)

So, 
> If I want to watch movies or play games or access my messagebank on my mobile (samsung pc-studio), I boot into windows. quick and easy. less than a minute.
> If I want to go on the net or do business stuff or anything else, I boot into unity. quick and easy. less than a minute.

All files and apps are available in ubuntu.

I think this is the best way to have direct access to windows software and data.

To do a complete backup you only need to backup the windows partition if you keep all your files, documents, backups, downloads, etc on your windows partition.
If one setup goes down, you can fix it from the other.

---

### Post by PsyclonJohn on 2011-05-15
I've tried reformatting using the LiveCD and had no luck with it (that was my first time dealing with anything like that) so, not entirely sure if I did things correctly. Next best thing, right?

I'm not looking to use Windows as a backup or anything, I just miss producing audio with FL Studio. I installed FL Studio with WINE and it's a bit slow and lacks some features that work well in Windows. I just hope it works well in VirtualBox. That's about it, I don't use Windows for anything else, that's Ubuntu job! :)

Just one day I got a Windows update and ... that was the end of Vista.

---

### Post by PsyclonJohn on 2011-05-15
Okay, I gave VirtualBox a try and so far it's not looking pretty.

Ubuntu freezes up when the Windows Boot screen appears, my mouse stops and no commands work. When I boot up Ubuntu my CPU monitor goes at a constant 100%

I'll delete the Vista file I created in VirtualBox and allow it to access less RAM (yet FL Studio requires a lot of RAM) and see it it all works.

---

### Post by PsyclonJohn on 2011-05-15
Alright, that attempt I really thought I was going to have it working. I gave it 512 MB of RAM and as soon as it go to "Expanding Files: 12%" it froze up. So, looks like I'm going to have to go to my 3rd option and get a new PC. One with at least 8 GB of RAM because giving Windows less than 512 MB of RAM to work on just doesn't cut it. 

This is my personal Dell Desktop, and my family shares a Dell Laptop and the Windows 7 on there died... so, I'll see if I can run VirtualBox on there, since it has 4 GB of RAM and a 64 Bit Processor. 

Why does it have to have fixed amount of RAM?

---

### Post by VOT Productions on 2011-05-15
Can you try XP or something? 7 and Vista use quite a lot of RAM.

---

### Post by PsyclonJohn on 2011-05-15
I only have Vista 32bit and 7 64bit disks.

---

### Post by Mark Phelps on 2011-05-16
> **PsyclonJohn said:**
> I only have Vista 32bit and 7 64bit disks.

Then you're going to need a MINIMUM of 1GB of memory to run either one.  And yeah, you CAN run in less, but my experience, when I upgraded a PC from XP to Vista, that was even with 1GB of memory, Vista ran so slow as to be painful.

I had to upgrade to 2GB to get decent performance.

So, you're right in that you're going to need a LOT of memory to run Vista in a VM and get decent performance.

---

