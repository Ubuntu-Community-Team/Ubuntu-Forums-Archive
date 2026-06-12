---
title: "GParted-- cannot resize Windows XP Partition"
date: 2009-12-28
forum: General Help
---

### Post by eveningsky339 on 2009-12-28
Title is pretty self-explanatory... I have a dual-boot configuration with Windows XP and Karmic.  I would like my Windows partition to be about 50 GB in size, since I only use it for my flight simulator.  However, the two are split evenly, with 150 GB each.

So, no problem, right?  I go to GParted... and that Windows Partition isn't moving.  The "Resize" option is simply not available.  Here's a screenie.

[IMG]http://i21.photobucket.com/albums/b282/eveningsky339/gparted.png[/IMG]

Any assistance would be appreciated.

---

### Post by adam814 on 2009-12-28
I think the orange triangle means it didn't unmount cleanly (maybe Windows locked up on shutdown or got a hard reset?).  If you run chkdsk /r in Windows the orange triangle should be gone and you should be able to resize the partition.

To enlarge your ubuntu partitions you'll need to do it from a LiveCD though since you can't resize a mounted partition and you can't umount your root.

---

### Post by eveningsky339 on 2009-12-28
Ah, ok.  Would I just run chkdsk /r in the XP command prompt or do I have to do anything different during boot up?  (Noob question, I know...)

---

### Post by adam814 on 2009-12-28
If you really *needed* it XP would run it on boot.  But you can also just do it in the XP command prompt, so I'd give that a go.

---

### Post by susanw on 2009-12-28
I'm triple booting XP/9.04 and 9.10 and had issues changing the windows partition when first installing. I ended up cleaning up the windows partition using the defrag options from inside windows. This has to be done several times (for some reason I forget) to compact the files into sensible places before you can use GParted to resize the Patition. It took some perseverance but once it worked it's since been easy to repartition when I needed to (to create a Media partition and larger SWAP partition...)

Perhaps it's obvious but if you right click the windows partition in GParted can you choose unmount?


Susan

---

### Post by sliketymo on 2009-12-28
Another tip ,try booting into windows,and disable volume shadow copy,page file(set it to "Do not use page file").It will gripe a little,lol.Then defrag a couple of times.You can turn them back on when your finished resizing.It might allow you to squeeze a little more space if you need it.

---

