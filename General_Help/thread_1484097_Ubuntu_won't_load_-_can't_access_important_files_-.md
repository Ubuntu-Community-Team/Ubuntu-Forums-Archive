---
title: "Ubuntu won't load - can't access important files - DESPERATE help needed"
date: 2010-05-15
forum: General Help
---

### Post by AussieDave on 2010-05-15
Please, I'm calling for desperate help here.

On my laptop I have a dual boot of Vista and Ubuntu (Karmic Koala). I have 3 Vista partitions and 1 Ubuntu partition (well, two if you include the swap disk).

Recently I had started to notice that when trying to boot into Ubuntu, it simply wouldn't. It would have a screen with lots of text which would every few seconds refresh yet it never really looked any different, although I'd be unable to tell. I'd leave it there for several minutes and nothing would happen.

I wasn't worried for a while because I only used Ubuntu for some scientific work over the summer and I haven't needed it for a while but now I desperately need those files. I've tried three programs that apparently make Linux partitions accessible in windows but I've been succesful with none of them. I'm now seriously worrying that there has been a harddrive error of sorts...but then I only have one physical harddrive on my laptop and my windows partitions are working okay.

I found my Karmic DVD and I tried to run "run Ubuntu without changing your system" but that wouldn't load after ages.

I haven't tried to reinstall Ubuntu because I've read that doing so would wipe the existing files.

PLEASE help me here. I've been almost in tears fearing that these important files are lost. I'll do anything to retrieve them!

Kindest regards,

David

---

### Post by howefield on 2010-05-15
Try another Live CD, perhaps something lighter like Puppy, about 100meg download, burn to CD, see if that boots on your computer giving you access to your hard drive.

An alternative would be Slitaz, only a 30 meg download.

---

### Post by AussieDave on 2010-05-15
Sorry but I don't know what puppy or slitaz are. I'm really not with the Linux lingo. When you mean see if that boots, you mean try it in that "try linux without affecting your system" mode? That will automatically know which partition on my harddrive has (well I deeply hope it has) the linux files?

---

### Post by howefield on 2010-05-15
> **AussieDave said:**
> Sorry but I don't know what puppy or slitaz are.

Ubuntu is a linux distribution, Puppy and Slitaz are two others.

> When you mean see if that boots, you mean try it in that "try linux without affecting your system" mode?

Yes, you said that Karmic for whatever reason isn't booting, the state of your hard disk shouldn't make any difference to that, as the Live CD does not touch your disk, although it may try to use the swap partition.

I'm just suggesting a couple of other live cds for you to try, as they are small(ish) downloads, it won't take too much time. 

Once loaded, hopefully you will be able to mount your hard drive and copy off the files that you need.

---

### Post by AussieDave on 2010-05-15
In Grub, I have several options.

They are "Ubuntu, linux, 2.6.31-19" and the same but with (recovery mode). There is also "Ubuntu, linux, 2.6.31-17", 16 and 14, each also with recovery modes.

"Ubuntu, linux, 2.6.31-17" is what I used for my work and "Ubuntu, linux, 2.6.31-19" just seemed to appear at one point automatically. I don't recall doing anything to get it.

When running "Ubuntu, linux, 2.6.31-17", the thing just freezes for about 20 seconds and then Grub reloads. All of the others load up this screen where lots of text happens. It does change actually and there is a number that cycles through on the left. it's up to about 350 now. I'm not sure what it means. (I'm on my desktop at the moment by the way). Oh and I've tried the recovery modes and nothing seems to happen.

I've seen things such asL

"[  120.435345] ata1: EH Complete" and "Unrecovered read error - autorecall failed" pop up.

---

### Post by AussieDave on 2010-05-15
> **howefield said:**
> Ubuntu is a linux distribution, Puppy and Slitaz are two others.



Yes, you said that Karmic for whatever reason isn't booting, the state of your hard disk shouldn't make any difference to that, as the Live CD does not touch your disk, although it may try to use the swap partition.

I'm just suggesting a couple of other live cds for you to try, as they are small(ish) downloads, it won't take too much time. 

Once loaded, hopefully you will be able to mount your hard drive and copy off the files that you need.
Okay. I'll make myself a Puppy or Slitaz cd and then hopefully that can access my disk.

I am a bit worried because I downloaded a program that let's you access linux partitions in windows and it recognised the 2 linux partitions (1 is the swap drive) and I assigned them letters but when I went to access them, they were treated like unused partitions of my harddrive which I first had to format (which of course I didn't).

---

### Post by AussieDave on 2010-05-15
FARK why can't I find a blank cd when I need one so desperately? :(

---

### Post by AussieDave on 2010-05-15
Not getting much else help here guys :(

Puppy won't load. Gives me some ****ing error. I'm going to try Slitaz. Man I'm tired. Had to drive to the 24 hour K-Mart just to get some blank DVDs. I just want to get these files.

If Slitaz doesn't work then I'm running out of options. I'm desperate for further help here.

---

### Post by AussieDave on 2010-05-15
Okay, so I got Slitaz to work. It shows the Linux partition but it says that it can't mount it for an unknown reason :(

****! ****! ****!

What do I do now? I really need help. It seems that somehow this HD partiton has stuffed up. I really hope that the files are still there. How can I get these files back? PLEASEEEE help!!!

---

### Post by HiImTye on 2010-05-15
windows has been known to mess with linux partitions in the past.. it's possible that the partition is corrupted

try checking the disk

---

### Post by AussieDave on 2010-05-15
Or maybe it was a purely Linux based fault...

How can I check the disk? I'm currently downloading something from ubuntu-rescue-remix.org

Hopefully that gives me some love!

It would have taken some effort for me to format that drive wouldn't it? Surely I couldn't have done it on purpose! I never did anything special. All I ever did was try to load the ****ing thing and I tried the recovery mode options a few times but they dd nothing.

---

### Post by AussieDave on 2010-05-15
Okay well these things seemed to have failed me. There must be something wrong with that harddrive partition. I'm going to take it to the computer technician I normally go to and hope to God that he can do something.

Must say, pretty underwhelmed with the amount of help I've gotten on here but a big thanks to the couple of people who did take the effort to help out someone struggling.

---

