---
title: "partitioning help"
date: 2009-08-21
forum: General Help
---

### Post by evanm457 on 2009-08-21
I am trying to partition my drive but it says that I only have 37mb shrink volume. No matter how much stuff I delete off the c drive the shrink volume stays at 37mb. whats going on?
BTW iv a vista and im trying to partition it to run ubuntu along vista.help appriciated

---

### Post by kestrel1 on 2009-08-21
> **evanm457 said:**
> I am trying to partition my drive but it says that I only have 37mb shrink volume. No matter how much stuff I delete off the c drive the shrink volume stays at 37mb. whats going on?
BTW iv a vista and im trying to partition it to run ubuntu along vista.help appriciated
How are you trying to partition the drive? are you using the Ubuntu live CD with Gparted?

---

### Post by bumanie on 2009-08-21
Deleting things from the filesystem will not alter the space the filesystem takes up on the hard drive. The 37gb is the amount of space taken up by the filesystem and it will stay the same whether you have 1gb of files stored within the filesystem or 30gb of files within it. To reduce the 37gb, you need to reduce the partition, not the amount of information the partition is holding. Before partioning vista, you need to defrag it a couple of times and it is best to use vista's own partitioning tool, which can shrink or expand partitions.

---

### Post by evanm457 on 2009-08-21
i am partitioning by going into vista control panel hard drive

---

### Post by evanm457 on 2009-08-21
thank you bumanie so how do I shrink the windows vista part of the c drive and roughly how much? At the moment it is taking up 175gb of space alot more than i think it should need but of course the drive also contains different applications and stuff.

---

### Post by evanm457 on 2009-08-21
oh it actually says that it has roughly 18gb free space in the c drive which would be enough to allocate to ubuntu cause it only needs 8gigs free space. i put an attachment of the hard disk app, i hope it loads up for ye>>>

---

### Post by kestrel1 on 2009-08-21
> **evanm457 said:**
> oh it actually says that it has roughly 18gb free space in the c drive which would be enough to allocate to ubuntu cause it only needs 8gigs free space. i put an attachment of the hard disk app, i hope it loads up for ye>>>
Only 18gb free? what do you have stored on there. I would suggest that you get an external drive & transfer some of your document's, photo's etc to it. You need some free space on your C:/ partition for Windows virtual memory. You may get away with using 10gb of the space that is left, but I personally wouldn't risk it.
Anyway, to partition the drive I would suggest that you boot up with the Ubuntu live CD & use gparted, but before doing that make sure that you have de-fragmented your drive.

---

### Post by evanm457 on 2009-08-21
yea i know my computer can be slow at times but I need the space cause I make music and have a lot of songs like 50gb of CDs. I also have lots of high preformance apps which take up another 50 gigs roughly. I might just get another hard drive to transfer everything onto or I might get a blue ray disk and put aload of songs onto that.

---

### Post by P4man on 2009-08-21
just so you know, afaik, you can't burn bluray discs under linux yet without Nero. Buying another hdd (or 2)  is also probably both cheaper and faster, and I don't much trust optical storage, but ymmv.

---

### Post by kestrel1 on 2009-08-21
> **P4man said:**
> just so you know, afaik, you can't burn bluray discs under linux yet without Nero. Buying another hdd (or 2)  is also probably both cheaper and faster, and I don't much trust optical storage, but ymmv.
I would agree with this. another HDD would be loads cheaper at present. You can pick up a terabyte HDD for next to nothing these days (relatively speaking)
You can either go internal or external, you could even do both. An external for backups & an internal for everything else.

---

### Post by evanm457 on 2009-08-21
ah yea ino ill be burning the BR disks in vista which will be running alongside ubuntu

well I've a laptop so i cant use an internal hdd so ill probably get a 320gb external one. But in saying that over in Ireland anyway a 320gb hdd is 50 euro and a br cd is a fiver blu-ray cds hold a little below 50gb so buying six would cost 30 euro and just short of 300gb anyway all I need is 50gb to hold my music and that will free up my laptops internal drive.

---

