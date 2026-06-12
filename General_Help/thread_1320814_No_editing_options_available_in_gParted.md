---
title: "No editing options available in gParted"
date: 2009-11-09
forum: General Help
---

### Post by OldGrantonian on 2009-11-09
I have dual-boot Vista and Ubuntu karmic. I want to reduce my Vista partition in order to increase my Ubuntu partition.

I unmount the Vista partitions and launch gParted. 

If I select a Vista partition to reduce, there are no editing options available. Only "Delete" is available.

Should I be doing this from a live CD?
.

---

### Post by tubbygweilo on 2009-11-09
I expect the partition should be resized from within Vista, I say this because I wrecked a Vista file system by resizing from an Ubuntu alt-installdisk. Do your self a favour and use the forum search function to further research this topic.

---

### Post by shaggy999 on 2009-11-09
First of all, I would *highly* recommend that before you resize your Vista partition that you defragment it first from within Vista. It makes the process much easier and faster. The second thing is that I wonder if you have ntfs write support enabled in gparted. You can find out by clicking on "File System Support" under one of the menu options. Adding in support for ntfs writes (don't confuse this with ntfs-3g file system driver) I believe is done by installing the "ntfsprogs" package.

---

### Post by coffeecat on 2009-11-09
Do **not** resize a Vista partition with Gparted. [This link]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") tells you how to resize a Vista partition with Gparted, but also tells you what will happen if you do. Scroll down the page - have a look at the "Windows failed to start" screenshot. The link cheerfully goes on to tell you how to fix this. Which is fine for the small minority of Vista users in the world who have a Microsoft Vista install DVD. If you have (as most Vista users do) only a manufacturer's restore image DVD, or even only some sort of restore partition, then you are out of luck: it will be a matter of 'bye, bye, Vista'.

Shrink Vista using Vista's own utility for this - it's an easy enough task. If Vista won't let you shrink it as much as you want, then have a look at [this link]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/").

---

