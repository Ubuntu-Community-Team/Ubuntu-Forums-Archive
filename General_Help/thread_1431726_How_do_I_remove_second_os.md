---
title: "How do I remove second o/s?"
date: 2010-03-16
forum: General Help
---

### Post by anthony2010 on 2010-03-16
Hi. Im running Ubuntu Studio and to be honest, Ive tried other O/s's and have decided I just want Ubuntu studio.It rocks.

So.. How do I get rid of the other O/s on my system so that my hard drive is freed up for just studio? If at all possible, i would prefer not to do a fresh install as I have it just nice now.

G Parted just gives me a load of partitions that are numbered and doesnt tell me which is the one I want to get rid of. I dont want to accidentally delete studio.

Any and all advice appreciated!

ant.

---

### Post by cchhrriiss121212 on 2010-03-17
Go to places and open up computer. You can tell which partition is which by the volume size, if you are using studio it will be mounted and the others will not. You could then resize your studio partition and update grub.

---

### Post by anthony2010 on 2010-03-18
Hi Chris.

ok I managed to delete the partition... I'm not sure about this..

Anyway, instead of showing a 500gb hard drive, 'computer' now just shows 'filesystem'. I have a load of unallocated space (according to G parted) but I really dont know how to allocate this space to studio or how to extend studio's space to include that unallocated space. I couldnt ask you to be a tad more specific on how to do this could I?
 I did manage to delete the irrelevant swap partition ( of which there were 2 Now just 1) I dont know if it helps but I took a screenshot of gparted..

[ATTACH]150474[/ATTACH]

cheers.

ant

---

### Post by john newbuntu on 2010-03-18
Well, looks like you removed a whole OS on the first partition.  One of the things you could do is to format that 232GB into an ext4 filesystem and relocate your /home directory to there.  This way, in the event of future upgrades, only the root file system (/dev/sda6) gets disturbed and not your /home directory.
You could also split this into smaller chunks just in case you want to try out another OS.

The unallocated 9.14GB can be merged with /dev/sda6.  Also, the swap space appears a tad bit bigger.  In general, you need it to be twice that of the RAM, although if you have a 4GB RAM you only need about say 5GB swap.

The following document from gparted tells you on how to resize partitions.
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
Hope these help.  Good luck.

---

### Post by anthony2010 on 2010-03-30
Hi.

I didn't find a way of doing this so I went for the option of a clean install. Good ol Michael Finnagen!

Thanks for your efforts all.

ant.

---

