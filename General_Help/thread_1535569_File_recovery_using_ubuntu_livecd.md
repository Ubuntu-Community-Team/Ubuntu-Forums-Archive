---
title: "File recovery using ubuntu livecd"
date: 2010-07-21
forum: General Help
---

### Post by danielslaughter on 2010-07-21
Hi there,
I did a search through the forums but couldn't find another post specific to mine so I hope I'm not repeating something old when I ask this...
I'm currently using ubuntu livecd to recover files from a dead windows machine. And when I say dead I mean windows itself won't boot, after several attempts at troubleshooting. All hardware is tested and passed. BIOS is up to date. Ubuntu itself opens up and operates just fine, accessing all drives and peripherals.

My problem is this, I want to recover my music and photos from the hard drive before I restore and re-install Windows. Easy enough. But the hundreds of gigs of music and photos that were on my HD are missing when I file browse to them in ubuntu.
Every other file on the HD is there, in tact, from windows system files to downloaded movies and tv shows. The "Music" and "Photos" folders on my drive are there, and inside each of them is only a few files from thousands that should be there.

Is there a function I am unaware of in ubuntu to show all contents of the drive? Surely a windows boot error wouldn't selectively delete only my music and photos...?

Any help would be greatly appreciated and although I'm new to this forum I actively respond to all offered solutions.

Thanks very much.

---

### Post by dcstar on 2010-07-21
> **danielslaughter said:**
> 
...........
Is there a function I am unaware of in ubuntu to show all contents of the drive? Surely a windows boot error wouldn't selectively delete only my music and photos...?

Any help would be greatly appreciated and although I'm new to this forum I actively respond to all offered solutions.

A corrupted drive is a corrupted drive, no matter what accesses it.

On the Live CD install the ntfsprogs package and then do a ntfsfix on the (unmounted) Windows partition.

If you can't access data after than, then you need to find one of the various emergency recovery CDs and try that option.

---

### Post by Zimmer on 2010-07-21
There is a program called photorec that might be useful to do this... a live cd and download it from the repos... Ubuntucat mentions it in one of his blog posts.....

---

### Post by danielslaughter on 2010-07-21
Problem solved, by happenstance really.
I got frustrated trying to access my files and decided to try a different linux distro. I could view all my files that weren't visible in ubuntu with this new live cd but the transfer rate to my external hdd was astonishingly slow. So as a last resort I went back to ubuntu for one last try, and everything magically appeared.
Like I said my pc hard drive is totally operational and fine it was just windows vista dying after a dodgy microsoft update causing aaaaaaaaaall these problems.
Anyway, problem solved, thanks to ubuntu. Today was my first venture into the complicated world of linux and I'm seriously considering a dual boot when I restore. It's just so.... pretty.

Thanks again for your suggestions.

---

### Post by Zimmer on 2010-07-21
Glad you have recovered your files... please mark the thread as SOLVED using the 'thread tools'  

Regards
Zimmer

---

