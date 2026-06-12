---
title: "Windows/Ubuntu switcharoo"
date: 2006-01-31
forum: General Help
---

### Post by ncappel1 on 2006-01-31
Hi everybody, I'm a newcomer to the whole Ubuntu/Linux scene. The many trials and tribulations between windows xp escalated one day to punches, kicking, and biting. sadly, windows won, and as I was lying face-up in the sunken ditch of despair and frustration, I thought to myself, "there must be another way." (cue insprational music) It was then that I saw the light. I came to and saw that a search and rescue man was pointing a flash light in my face, yelling that he found me. He handed me a bright, shiny, new cd--then left me in my ditch to figure it out for myself.

Is there a way to switch two operating systems with out 2 installation cds?

My computer has two hard drives, one old and one newer. The old one only has 6 gigs of space, and the new one 20. When I installed ubuntu I just put it on the smaller one and dual boot, I wasn't sure if I would want to keep it. I like it a lot, the only things that keep me from completely switching to Ubuntu are some minor issues that I havn't completely resolved yet (minidisc support and java support... these are other problems in themselves)

My real question is, is there anyway to switch the operating systems, so that Ubuntu gets put on the 20 gig drive and windows on the 5 gig drive? The five gig drive is almost full, and being older, runs a little slower than I would like.
My plan would be to just backup all the files I want on both systems and just reinstall windows on the 5 gig drive and put ubuntu on the 20gig drive, using ubuntu for my main computer needs, and the windows for the one or two operations that I can't (yet) accomplish with linux. The problem is that I have an ubuntu cd, but don't have a windows installation cd ; I'm away at school.

Is there a way to switch the two operating systems with out 2 installation cds?


I guess the dramatic story in the beginning wasn't really necessary. :-({|=

---

### Post by carlosqueso on 2006-01-31
I don't think it's possible...but as an alternative, you can partition the 20 gig drive, and use it as your home directory or a general place.  I'd use the live CD with gparted, or if you prefer QTparted in Knoppix.  Just fire one of those up, shrink the winders partition on the 20gig drive, and format the one as ext3.  If you need help mounting it if you decide to to it, let me know.

---

### Post by stuporglue on 2006-01-31
You could use a Ubuntu live CD to resize the Windows partition, then create a new partition on the Windows disk, then use that partition (or partitions) as /home, /etc, /var etc. depending how much space and how many partitions you make. 

Yeah, it's not actually switching the disks, but you could at least reclaim some space from Windows.

---

### Post by bschuteker on 2006-01-31
You could ask around and see if anyone has Norton systemworks with Norton Ghost. You can wipe the 6 Gigger and then use Ghost to copy the Winders drive to it. Then you would have the whole 20 Gig drive to soak up Ubuntu. ;)

---

### Post by lha on 2006-01-31
[QUOTE=bschuteker]You could ask around and see if anyone has Norton systemworks with Norton Ghost. You can wipe the 6 Gigger and then use Ghost to copy the Winders drive to it. Then you would have the whole 20 Gig drive to soak up Ubuntu. ;)[/QUOTE]

If the other drive is Maxtor's, you can use MaxBlast to copy Windows partition from 20 GB drive to 6GB drive. You'll need to resize your Windows partition first. (Or borrow someones Maxtor drive for a moment. I remember MaxBlast checks if you have Maxtor's drive and wont do anything if you don't have.) Maybe your hd manufactorer offers similar program. Try search their website.

I matter of fact, I might have read of some Linux tools that are able to ghost partitions. (Maybe even dd can do it, don't know.)

---

### Post by ncappel1 on 2006-02-02
Thanks for the good info, i'll try some things and let you know how it works out!

---

### Post by ncappel1 on 2006-02-19
Update: I tried some of the suggestion on this thread. I was going to use max blast. but in the end it wouldn't really do exactly what I wanted to do. I ended up simply backing up all of my files, and physically reinstalling windows first on the small harddrive. After this, there were two separate windows xp operating systems, one on each drive. after this, I reinstalled Ubuntu on the larger drive. Everything installed fine, and I thought I was home free, but now the problem is that the grub menu doesn't show windows as an option to boot. It only has the ubuntu. 

I don't suspect that I accidentally installed ubuntu on one drive and used the smaller one as extra space, because i specifically told it to only install on the 120 gig drive, and ubuntu shows that I have 111 gigs free, all under one drive. 

Anybody have an idea how I can get windows to appear in the grub menu?
thank you

(note: I accidentally said that the larger drive was 20 gigs in the first posts, i meant 120.)

---

### Post by lha on 2006-02-19
Where grub is installed?

---

### Post by JimS on 2006-02-19
...

It seems to me that the Windows drive
should be the master drive and have
grub (or MBR pointing to grub, I don't
know which) on it.  The Ubuntu drive should
be the slave drive.  If I'm right and you are
still having a missing grub, then check
your bios, HD jumpers, and/or cable settings
to make sure your have your ducks in order.

I have 2 HDs of different manufacture, one
5+ years old w/ WinME and the newer one,
now with Ubuntu.  It was a struggle to get their
settings correct when I added the 2nd HD.

BTW do y'all find my short lines easier to read
then other people's long lines??  I have a 20" CRT
monitor ($40 used and hernia heavy) and I tend
to get lost reading long lines, so I may have
missed your point.

J[COLOR="Blue"]imS
Prostate Cancer Aware
[/COLOR]
...

---

### Post by ncappel1 on 2006-02-20
The grub is installed in hd0, the master drive, the 120 gig drive. 

JimS, I am guessing that the pins and everything are in the correct place, because before I tried to switch the to OSs I had a perfectly functional dual boot. As a matter of fact, when Ubuntu and windows were installed in the slave and master drives, respectively, the grub was installed in the slave. This was because when ubuntu asked me during installation to create a grub sequence, i just selected yes, and it did everything automatically.

---

### Post by lha on 2006-02-20
Take a look at [http://www.ubuntuforums.org/showpost.php?p=728667&postcount=3]("http://www.ubuntuforums.org/showpost.php?p=728667&postcount=3")

---

### Post by ncappel1 on 2006-02-26
bah! humbug...

I have been fiddling around for a little bit now, and when I was tryingto edit the grub, I this message when I tried to load Windows xp: "NTLDR missing" I looked in the Maxtor Maxblast manual and it said that if this message came up I would have to put in my windows xp cd and install windows. I tried doing that, but as I have now learned, installing windows as a secondary operating system (that is, after another the computer was only running ubuntu) is a bad bad bad idea.

I didn't even get to installing anything, there was an error. The whole thing just crashed and messed up the grub. I used the live cd to try and repair it after finding some other threads on the forum, but nothing worked. I got so frustrated that I finally decided that keeping a windows dual boot only for my sony minidisc software was not worth the trouble I was going through. 

I made a decision two days later that I would learn from this experience and use it as a stepping stone. I completely reformatted everything and reinstalled ubuntu. I don't intend on using windows on my home computer ever again! I'm sorry windows, it isn't you, it's me....wait, what the heck am I saying!? **of course it's you! I tried so hard to make it work, but you just don't care!** oh...how could I have been led on like this for so long? I was so blind. 

100% Ubuntu as of Feb. 25, 2006. I bought a new bag of espresso coffee to celebrate.

---

### Post by nanotube on 2006-02-27
haha, you go dude! :)

---

### Post by Resurrection on 2006-02-27
Well it would seem I'm a little late to the party, oh well.

I was going to ask you though did you make sure that the smaller drive was the master drive on the primary ide?  Windows has this nasty thing about wanting to be the first partition on the master drive of the primary ide.  If it isn't there, it won't boot (at least thats been my experience).  Ubuntu (since it is superior) doesn't care what partition or drive or ide its on.

Like I said, too late now.  Maybe someone else will see this though.

---

### Post by lha on 2006-02-27
[QUOTE=Resurrection]Windows has this nasty thing about wanting to be the first partition on the master drive of the primary ide.  If it isn't there, it won't boot[/QUOTE]

False. I have two instances of Windows on my secondary master (it'd work even if they were on a slave drive) and they boot fine. Of course, as there are two Windows installations on a hard drive, one of them is not on the first partition.

---

### Post by handy on 2006-02-27
Yes, the more modern motherboards will boot windoze from the primary or secondary IDE channels.

I will continue booting xp from the secondary master (where it of course belongs) until it gets the boot completely! :mrgreen:

---

### Post by Resurrection on 2006-02-27
[QUOTE=handy]Yes, the more modern motherboards will boot windoze from the primary or secondary IDE channels.

I will continue booting xp from the secondary master (where it of course belongs) until it gets the boot completely! :mrgreen:[/QUOTE]
Ah, maybe its because it was on my old machine, more than 4 years old.  I could never get windows to work without being on first partition of master on primary ide.

Learn something new everyday.  Thanks.

---

### Post by ncappel1 on 2006-02-27
that was probably my issue. My computer is about 3 or 4 years old. Maybe that had something to do with it. You are right Resurrection, you learn something new every day!

---

