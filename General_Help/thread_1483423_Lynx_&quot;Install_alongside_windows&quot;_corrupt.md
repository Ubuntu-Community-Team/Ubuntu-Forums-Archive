---
title: "Lynx: &quot;Install alongside windows&quot; corrupted both partitions"
date: 2010-05-14
forum: General Help
---

### Post by _Rade on 2010-05-14
Hi all, and thanks in advance for any replies!

I was using Windows 7 (I know...) and decided to Give Lucid Lynx a try. Popped in the CD, and was pleasantly surprised to find an option to "install alongside windows". Awesome.

So I followed the installer instructions, and the system rebooted as expected. Brilliant, or so I thought. Machine POSTed and I could feel a tinge of excitement up my spine as the thought of an open source OS was about to become a reality.

Except that in reality, I got a BIOS error stating that no bootable drive had been found (I didn't even change any boot settings, but checked that they were as they should be and that the CD was removed.

I used to work as a PC technician so I knew instantly that something had gone wrong - although spent some considerable time trying to prove otherwise!

OK, worst case scenario has happened, a corrupted boot sector/MBR - no worries, I thought, I've got a SATA -> USB connector, I'll use that and my laptop to recover my data (freelance work). But my HDD was not recognised (even though the same method successfully showed me data from an old drive I had around). So I open up the windows MMC and head to disk drives section and to my display I see that the drive's filesystem is "RAW".

OK, so maybe windows isn't playing fair with the linux partition? Time for a clean install of Lynx on another HDD,

Boot  lynx, plug in the USB > STA connector with a test drive, works perfectly, so next (praying) I plugged in the corrupted drive. Nothing.

Disk utility shows my corrupted drive (partition type: HPFS/NTFS) but will not allow me to do anything other than format. Definite no-no there.

I have browsed the forums extensively and could not find a useful thread, so please, community, I emplore you - help me. The linux dream has turned into a nightmare; I love my new desktop OS (awesome work since Hardy btw), but without my data it might as well be a netbook!

Again, thanks in advance for any replies I will be sincerely grateful for any suggestions.


_Rade

---

### Post by _Rade on 2010-05-20
OK so I wasn't expecting much...

For the 60 peopel that have read this possibly with a similar problem, here's what I did: (no fix btw)

Downloaded and tried about a dozen of the most popular data recovery utilities (file scanvenger etc), many of which proclaimed to be able to recover "RAW" data, but none of them worked. Just as i was about to curl up in a ball and cry I tried one last app that managed to get all my data back!

- Easus recovery I think it''s called.

Anyway, long story short: managed to find an app to recover my data: reinstalled windows on it's own drive with Lynx on another. No magical cure but at least I got my data back.

For the record the only other similar posts I could find just ended up with a Lynx bug report being filed, so for those of you looking for something more useful: this is the best you're gonna get.

Question - do you think you're "average user" would have gone to this trouble? Of course not, they would have dismissed "this linux thing" as amateur and buggy. Some great (and by great I mean AWESOME) work, but still a long way to go...

All the best :)

---

