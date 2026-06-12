---
title: "Software Raid"
date: 2009-08-11
forum: General Help
---

### Post by whaase on 2009-08-11
I want to set up a software raid 5 using mdadm and with 4 - 1 tb sata drives. My primary boot drive is a 80 gig sata.

My question is, if I have the main os on the 80 gig and a raid 5 with the 4 - 1 tb drives, if the main os failed. Would a new install find the existing software raid?

---

### Post by jocampo on 2009-08-11
> **whaase said:**
> I want to set up a software raid 5 using mdadm and with 4 - 1 tb sata drives. My primary boot drive is a 80 gig sata.

My question is, if I have the main os on the 80 gig and a raid 5 with the 4 - 1 tb drives, if the main os failed. Would a new install find the existing software raid?

Not 100% sure, but I think so. Because information is written at partition table level. If those who are part of the RAID5 had no failure, your Os (after re configure mdadm again) should see those drives. Please take a look on the following link: [http://ubuntuforums.org/showthread.php?t=408461]("http://ubuntuforums.org/showthread.php?t=408461")
and
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html]("http://tldp.org/HOWTO/Software-RAID-HOWTO.html")

That said, I am not a big fan or software RAID. Because performance and with current disk and server prices, I would not "play" with my data that way ...I would use a read hardware RAID instead. But...is your data and your information ... ;-)

---

### Post by whaase on 2009-08-11
> **jocampo said:**
> Not 100% sure, but I think so. Because information is written at partition table level. If those who are part of the RAID5 had no failure, your Os (after re configure mdadm again) should see those drives. Please take a look on the following link: [http://ubuntuforums.org/showthread.php?t=408461]("http://ubuntuforums.org/showthread.php?t=408461")
and
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html]("http://tldp.org/HOWTO/Software-RAID-HOWTO.html")

That said, I am not a big fan or software RAID. Because performance and with current disk and server prices, I would not "play" with my data that way ...I would use a read hardware RAID instead. But...is your data and your information ... ;-)

Ill read through those, thanks!

I've been really tossed over this. I built a freenas server with software raid. I was getting about 18 MB upload and about 30 MB down. I wasn't happy, so I installed ubuntu and did a soft raid. I got 50 up and 50 down. Then I was told hardware raid was the way to go. So I bought a 4 port pci-e raid card. I got 30 down and maxed out at 2 MB up! I tried everything. After lots of googling I've read that cheaper raid cards are basically the same as software. And in order to get a true hardware raid you have to spend the $$$$. This is for my media center, so dumping that much just isn't going to happen lol

I remember at the last company I worked for our Dell 2650 AD controller was set up raid 5 w/5 drives. The raid controller bit the dust and we lost it all. Server was toast basically. Thank god for backups lol. But it makes me real gun shy with these things now.

---

### Post by jocampo on 2009-08-12
Well... please remember that nothing replace backups. RAID are for data redundancy only. Also, RAID5 does not provide the best read/write peformance because the parity bit. 

If you do not have critical data on it and you can tolerate some downtime, go for it and use software raid. But please be sure you are running regular backups, you won't regret that when your server does not boot in the moorning or your data drives just start to complain ...

---

