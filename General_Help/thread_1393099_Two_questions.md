---
title: "Two questions"
date: 2010-01-28
forum: General Help
---

### Post by nishant.singh28 on 2010-01-28
I have two things to ask.
1) I have set a large image as nautilus background. How can i prevent it from scrolling down when the filelist is long?
2) I have two drives, one a 200GB partition on my notebook drive and a 250GB portable drive where I store Data. Both are NTFS filesystems. I want to defrag them. Please keep three suggestions to yourself: using Wine, changing them to ext and defragging over the network. If there are any programs that can run on my system and defrag, please let me know.

---

### Post by howefield on 2010-01-29
> **nishant.singh28 said:**
> Both are NTFS filesystems. I want to defrag them.

Hiren's BootCD 10.1

---

### Post by nishant.singh28 on 2010-01-29
> **howefield said:**
> Hiren's BootCD 10.1
Anything that doesn't require me to power down my system?

---

### Post by howefield on 2010-01-29
> **nishant.singh28 said:**
> Anything that doesn't require me to power down my system?

Not sure that I know of an application that suits your ever growing list of criteria.

To be honest, I wouldn't trust Windows disk management tools with my Linux drives, and vice versa, if I wanted to defragment ntfs, I'd use windows compatible applications.

A "crude" way might be to copy the files off and reformat your disk/partition, then copy them back.

---

### Post by nishant.singh28 on 2010-01-29
> **howefield said:**
> Not sure that I know of an application that suits your ever growing list of criteria.

To be honest, I wouldn't trust Windows disk management tools with my Linux drives, and vice versa, if I wanted to defragment ntfs, I'd use windows compatible applications.

A "crude" way might be to copy the files off and reformat your disk/partition, then copy them back.
The criteria is not growing. Given the size 200 + 250 GB, I don't think anyone can afford so much downtime, considering that half of my study work is online. It is an understood criterion that defragging should not necessitate powering the system down. 
OK, what windows compatible tool would run on Ubuntu because I don't tust Wine at all to do stuff like that.
I can't switch to ext4 as I might need Windows some day( may God prevent this day from coming!!! ) and I sometimes need to connect my external drive to my friend's Windows 7 notebook.

---

### Post by chewearn on 2010-01-29
[http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)
[http://www.webupd8.org/2009/10/defragmenting-linux-ext3-filesystems.html](http://www.webupd8.org/2009/10/defragmenting-linux-ext3-filesystems.html)

I have never used any of the software in these links, so it's your own risk.

---

### Post by Simian Man on 2010-01-29
> **nishant.singh28 said:**
> The criteria is not growing. Given the size 200 + 250 GB, I don't think anyone can afford so much downtime, considering that half of my study work is online. It is an understood criterion that defragging should not necessitate powering the system down.

First off very few people would want to use NTFS without windows, so barely anybody would need a native Linux tool to defrag NTFS.  Secondly don't you sleep?  Boot the CD howefield mentioned when you go to bed and wake up to a defragged filesystem.

---

### Post by nishant.singh28 on 2010-01-29
I sleep. My system doesn't. It hasn't been shutdown for two days. The problem is there are many noisy people in adjacent rooms so I usually leave my system playing some light music to drown out the noise.
 THE MOST IMPORTANT THING:
The 2nd point isn't very important so I don't have a problem if I can't defrag. The most important question is the nautilus one. What about that?

---

### Post by howefield on 2010-01-29
> **nishant.singh28 said:**
> The criteria is not growing.

You started off with

> Please keep three suggestions to yourself: using Wine, changing them to ext and defragging over the network.

Then added

> Anything that doesn't require me to power down my system?

Therefore, the criteria by which you will accept a suggestion is growing. ;) 

Most people who have ntfs drives, also have windows or at least access to windows, which in fact you have through the friend you mention.

If the only reason I had for keeping ntfs partitions was "I might need Windows some day" which is extremely unlikely because of "( may God prevent this day from coming!!! ) I'd be looking at using a non fragmenting file system such as ext3 or 4.

And for friends who need access to the disk, I'd find another solution.

---

### Post by nishant.singh28 on 2010-01-29
Can we please look at the problem at hand instead of poking each other? I'm really sorry if my words offended anyone. I never meant any insult. But if anyone suggests that I'm being picky just consider this.
1) I tried using Wine for it, no avail.
2) My system isn't permanently mine. I may make a switch when I want to, and when this notebook goes home, I WILL have to install Windows *sigh*. SO I said no switching to ext.
3) One drive is an internal partition, so it can't be defragged by my friend.
4) Over the network? I'm not so experienced and have 0 experience of doing things over a network. I f anyone can give me full details, please come forward.
5) I'm a student and need to have access to my mails, online assignments and ebooks 24 hours a day. I can't afford a downtime of over 10 hours(5 hours per disk of that size from my extensive Windows experience).

---

