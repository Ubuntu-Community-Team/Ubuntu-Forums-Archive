---
title: "Microsoft ReFS and Linux"
date: 2012-05-12
forum: General Help
---

### Post by HappyLinux on 2012-05-12
It has recently come to my attention that Windows 8 (coughs, splutters and pukes) will be coming out with a new file system to replace NTFS.

This new file system is being called ReFS (Resilient File System). It's being dubbed as a competitor to Linux's BTRFS.

Even though I'll be avoiding Windows 8 for as long as possible, I won't be able to run forever. At some point I'll end up having to replace my Win7 with Win8, or Win9 or 10.

My point is, that eventually stuff like removable media, or just plain USB Hard Drives are bound to come with ReFS. Would Linux be able to handle it almost straight out the box, or will it take time for the programmers to develop the drivers necessary?

Oh yes, does anyone know when BTRFS will become the default in place of Ext4?

---

### Post by rai4shu2 on 2012-05-13
I would stick with NTFS for generic data dumping a good long time, as I doubt anyone in the Windows world is itching to switch away from NTFS.

I think Btrfs will be the default FS when pigs fly. Ext4 is still the best FS, and I dare you to find a benchmark that proves otherwise.

---

### Post by HappyLinux on 2012-05-13
I'm not itching to switch from NTFS any time soon, but no doubt Microsoft will try forcing companies into using ReFS. When they brought out NTFS into general use, hard drive companies like Western Digital etc quickly switched to pre-formatting their HDDs as NTFS.

I know that if I bought a HDD which came pre-formatted with ReFS, I could reformat as NTFS, but what about reading a Win8 partition from within a linux distro?

Also, how long will it be before Microsoft removes the formatting option for NTFS?? Oops, dumb question. They won't remove the option for a long time, just like it took them a long time to remove the FAT32 option and replaced it with exFAT.

As for Ext4 and Btrfs, I have also seen a benchmark review between them, and for the most part, Ext4 wins hands down.

There's a thought; Microsoft calls the new file system as Resilient File System (ReFS), but I wouldn't be surprised if it's not as resilient as they make it out to be. It would probably be more resilient if Linux used it. However, would Windows be more stable if it was running on Ext4?

---

### Post by uRock on 2012-05-13
> **HappyLinux said:**
> I'm not itching to switch from NTFS any time soon, but no doubt Microsoft will try forcing companies into using ReFS. When they brought out NTFS into general use, hard drive companies like Western Digital etc quickly switched to pre-formatting their HDDs as NTFS.

I know that if I bought a HDD which came pre-formatted with ReFS, I could reformat as NTFS, but what about reading a Win8 partition from within a linux distro?

Also, how long will it be before Microsoft removes the formatting option for NTFS?? Oops, dumb question. They won't remove the option for a long time, just like it took them a long time to remove the FAT32 option and replaced it with exFAT.

As for Ext4 and Btrfs, I have also seen a benchmark review between them, and for the most part, Ext4 wins hands down.

There's a thought; Microsoft calls the new file system as Resilient File System (ReFS), but I wouldn't be surprised if it's not as resilient as they make it out to be. It would probably be more resilient if Linux used it. However, would Windows be more stable if it was running on Ext4?
Since there are so many servers out there running NTFS, I highly doubt MS will default to a new FS any time soon. 

When you ask if Windows would be more stable, what do you mean?

     1) Windows 7 is like depleted uranium armor, it is solid, yet flexible. I have had zero problems with it or any other version of Windows I have run in the past.

     2) Ubuntu Forums is not the place to bash other operating system, so please do not do so here.

---

### Post by WorMzy on 2012-05-13
I doubt there will be support for ReFS on Linux for a while, unless Microsoft make it open source and/or assist in the development of non-Microsoft OS drivers. Like NTFS support, I expect it'll take a good few years before a reliable driver+fsutils are developed.

Regarding btrfs, it may be the default filesystem in Fedora 17, if that's any use to you. There's nothing stopping you using it now if you want to though.

---

### Post by HappyLinux on 2012-05-14
> **uRock said:**
> Since there are so many servers out there running NTFS, I highly doubt MS will default to a new FS any time soon. 

When you ask if Windows would be more stable, what do you mean?

     1) Windows 7 is like depleted uranium armor, it is solid, yet flexible. I have had zero problems with it or any other version of Windows I have run in the past.

     2) Ubuntu Forums is not the place to bash other operating system, so please do not do so here.

I apologise if it seems like I'm bashing Windows or other OSes. In fact, I'm quite fond of Win7. I quite liked Win2000 as well. In addition, I also like Mac OSX. Although I can't afford to buy a Mac.

What I mean by windows being stable is how easy it is to break. For years now, I've seen several different windows breaking under the strain of repeated install, uninstall, upgrade, update of programs from MS Office, to JavaRE. No matter how many much you clean up windows registry, running programs like CCleaner to clear out junk, etc, eventually Windows starts to collapse in on itself. Sort of like the foundations of a building being damaged.

However, Windows isn't alone. This sort of problem is within Linux and Mac, although it takes longer to happen.

So far I haven't had any problems with Win7 either. I find it to be a sturdy version of windows. Heck, I'm dual-booting my machine. Win7 and Mint 12. I use Win7 for gaming so it takes a beating with me installing a game, then uninstall that and install another game. I stick to Mint for general desktop work.

I would love to own a Macbook Pro.

Win7 is great, Linux is an addiction, and Mac just seems fun in its own way.

---

### Post by HappyLinux on 2012-05-14
> **WorMzy said:**
> I doubt there will be support for ReFS on Linux for a while, unless Microsoft make it open source and/or assist in the development of non-Microsoft OS drivers. Like NTFS support, I expect it'll take a good few years before a reliable driver+fsutils are developed.

Regarding btrfs, it may be the default filesystem in Fedora 17, if that's any use to you. There's nothing stopping you using it now if you want to though.

If and when Mint sets Btrfs as default, then I'll just go with the flow. For now, I'll stick with Ext4.

As for the means for Linux to handle ReFS, I can wait. I can at least stick with Win7 which no doubt MS will bring out the update to handle ReFS in a Service Pack or something.

---

