---
title: "Remove Win XP Without losing files"
date: 2009-11-01
forum: General Help
---

### Post by greenco on 2009-11-01
My son has been running Win XP and Ubuntu 9.04, with a dual boot setup. He is ready to remove Win XP and make the switch to Ubuntu. As far as I know he used the Win XP's "Add and Remove Programs" feature to install Ubuntu from the "Live CD". He has a lot of music files (iTunes) stored on his C drive, that he has downloaded for his I-Pod. He has been moving them into a Ubuntu folder, to back them up. He lives in Arizona and I am in Maryland and I plan on talking him through the installation process, via telephone. I have installed Ubuntu several times on my computer and I am able to do the partitioning and etc. that is needed for a full Ubuntu install.  I have some questions about how to do it, so that he does not lose his music files. He has over 1100 songs and it would take a lot of blank CDs, to back them all up. I never had Windows and Ubuntu installed, at the same time, so I am not sure of how to accomplish this.

1. When he boots the computer, with the Live CD, and selects to "Install Ubuntu", will the Win XP and the current Ubuntu partitions show up in the partitioner window or will they be on a single NTFS partition?

2. Can I use some of  the hard disk's free space to make a ' / ' and a "Home" and a "Swap" partition, without messing with the current Win XP & Ubuntu files?

3. If I use step 2 and he moves the files to the new "Home" partition, would he not lose them when we resize that "Home" partition to reclaim the Win XP disk space?

4. Is there a "SAFE" method that I can use to do this?
Thanks

---

### Post by howefield on 2009-11-01
I think the first thing you need to do is clarify whether the Ubuntu part of the dual boot was done via a Wubi install, or is it a real install ?

---

### Post by greenco on 2009-11-01
I just called him and he said he booted off of the "Live CD" and elected the option to installed a dual boot setup.

---

### Post by Monotoko on 2009-11-01
1. When he boots the computer, with the Live CD, and selects to "Install Ubuntu", will the Win XP and the current Ubuntu partitions show up in the partitioner window or will they be on a single NTFS partition?

[COLOR="Green"]They will show up in the partitioner Window if he has done a liveCD boot and installed via that (rather than inside windows through WUBI)[/COLOR]

2. Can I use some of the hard disk's free space to make a ' / ' and a "Home" and a "Swap" partition, without messing with the current Win XP & Ubuntu files?

[COLOR="Green"]I would not mess with /, leave that where it is, but for a seperate home partition, take a look here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)[/COLOR]

3. If I use step 2 and he moves the files to the new "Home" partition, would he not lose them when we resize that "Home" partition to reclaim the Win XP disk space?
[COLOR="Green"]You will need to have Windows XP deleted to create that new /home partition in the first place, back everything you do not want to lose onto EXTERNAL media[/COLOR]

4. Is there a "SAFE" method that I can use to do this?
[COLOR="Green"]No method is completly safe, but the best way would simply be to get the needed files off the Windows XP and Ubuntu partitions onto external media, wipe the Windows XP parition using GParted, create a new partition in Windows XP's place using GParted, then use the insructions here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) Do NOT forget to backup, then if something does go wrong, it is not the end of the world[/COLOR]

Thanks
[COLOR="Green"]Thank you :)[/COLOR]

---

### Post by howefield on 2009-11-01
Hmm.. you'd need to be very confident of both you and your sons ability to do this successfully over the telephone :) Good Luck.

Presumably your son can't do this on his own and you can't physically see what is being done, the potential for exasperation is huge. Enough of the downside. ;)

1100 songs isn't that many, it is only a couple(ish) of dvds depending on file size. Are a few dvds out of the question ? I wouldn't be happy doing this without knowing the required data was off the disk being worked on.

With the data off the hard disk safely, then the Ubuntu install becomes a piece of cake.

---

### Post by greenco on 2009-11-01
Thanks, I just called him again and explained the danger of losing the files, unless he backs them up on CDs or DVDs. He said he would go buy some tomorrow and copy the files onto them. When that is done, I can have him boot from the "Live CD" and do a manual install. This will let us use the whole hard drive for Ubuntu.

---

