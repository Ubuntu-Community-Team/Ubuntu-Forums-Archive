---
title: "Swappiness?"
date: 2010-04-29
forum: General Help
---

### Post by keygiwawah on 2010-04-29
I am planning on upgrading my Linux machine to Lucid as soon as possible.  I only have 1GB of RAM on that machine, and was just curious if anyone had any suggestions about what I should set my swappiness to?  I was just going to try it out with none, but if that does not work out, I was hoping someone had a good amount of space to use.

---

### Post by mcclunyboy on 2010-04-29
depends on what you intend to use it for...i would set it to 2gb (double your physical memory :P)

---

### Post by anaconda on 2010-04-29
I would set the swappiness value to 10

Hmm.. did you mean the swappines value (which determines how easily swap is used) or did you mean how big swap partition you should make...

If you ask the size of the swap partition I would make it 1GB, but that is me..

---

### Post by keygiwawah on 2010-04-29
Do you mean double it as in 1GB RAM and 1GB on HDD, or 2GB on HDD? I'm not too experienced with using this yet so I'm really not sure on how much is needed. I just don't want to put too much on my HDD because it's not the fasted computer to begin with. So just want be sure.

Thanks for the help.

---

### Post by mcclunyboy on 2010-04-29
If you have 1GB of Ram it is normally set to 1-3x that amount.  I generally do double, anaconda does the same...With ubuntu 9 1GB should be fine, older linux versions required a little more.  The Swap file is basically a partition on your hard disk used as  temporary memory.

How big is your hard disk?  Obviously if it is small don't have a big swap file...

---

### Post by Rubi1200 on 2010-04-29
If you plan on a clean install using the LiveCD (which I recommend), Ubuntu will automatically create a swap partition on the HD. It will be double the size of your RAM i.e. 2 GB. If you intend manually partitioning your HD, I still suggest a 2 GB swap. I also have an older computer with 1 GB RAM, and I have found my current configuration to be ideal. As it is, Ubuntu is very light on system resources.
Good luck!
:)

---

### Post by keygiwawah on 2010-04-29
Thanks I'm going to try 1GB and 2 if that isn't enough, but I only have a 40GB HDD on my Linux machine, so that small amount actually means a lot to me.

---

