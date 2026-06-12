---
title: "Luckyback up...now stuck in tty1"
date: 2010-12-09
forum: General Help
---

### Post by AirWreck on 2010-12-09
I just started using Luckybackup as a replacement for the trusty but aging Keep, but not feeling so lucky right now.

I've been using it for about a week to back up my home partition as well as my NTFS partition where I keep the majority of my files.  This morning, I forgot to mount my external drive that is the target for these backups.  Luckybackup backed up my home, there's not much but my email from kmail/kontact in there but still I noticed that it seemed to be taking longer than a quick diff backup of changes since a couple days ago, as in about as long to do a fresh backup.  The backup puked when it got into the real data on my NTFS partition.  I got a few errors with the last one being "no more space on drive" or something to that effect.  Its all kind of fuzzy (pre cup of coffee) but I closed out and then realized I hadn't mounted my external.  The system got clunky so I rebooted and got the tty1 screen...and ever after.

I booted into kubu using my flash drive and found that the 10gb root partition was chockablock.  Its usually nowhere near that so I figured that it dumped my backup into a root directory somewhere.  I did a search for files (including hidden) updated today to see if I could find an easy smoking gun.  Nope.  /usr is 3gb but I haven't been able to find any good candidates deeper in the subdirectories.

I am on a ship at sea and cannot plug my personal laptop into the network so I can't just reinstall the root and start over clean.

Any suggestions out there to help me out?  Many thanks.

FYI...if it helps - I'm dual booting Kubuntu 10.10 64bit with W7 on a Toshiba Satellite T135 but I think my idiot move is more generic in nature!

---

### Post by AirWreck on 2010-12-11
Bump...anyone that can help a sailor out???  Thanks.

---

### Post by QLee on 2010-12-11
[QUOTE=AirWreck]...  This morning, I forgot to mount my external drive that is the target for these backups. ...[/QUOTE]

Well, this is a guess but I believe it is an educated guess. It's a problem that sometimes occurs to forgetful users.

When you forgot to attach your backup external drive, the "unLucky" backup started writing in the directory where the external would usually be mounted, and there wasn't enough unused space, thus filling up your root filesystem tree.

You can boot again without the external, navigate to the location where it is usually mounted and delete the partial backup located there. If you have a live CD, you could do it with whatever GUI you are familiar with.

Good luck, sailor!

---

### Post by AirWreck on 2010-12-11
You, my friend, saved my life...or at least greatly improved the quality of it for the next two weeks of it before we get back to port and I could have done a last ditch reinstall.  The forgetful user thanks you!

---

