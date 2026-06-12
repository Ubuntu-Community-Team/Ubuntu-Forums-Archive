---
title: "Advice using GParted to create seperate partitions for 9.04 and 9.10"
date: 2009-12-01
forum: General Help
---

### Post by isee on 2009-12-01
Hi All!

Bear in mind I'm pretty noob, and also I can try try again, as long as I don't f\u my HD itself.  Can that happen?

Im going to reformat my laptop again for the umpteenth time, after various Distro and Ubuntu installations.  However, this time I want to format my HD and use GParted on CD to create partitions first, and then install.  I've perused various guides, but would appreciate advice on what's the best way for me to proceed.

This is what I think I want.  3 partitions, one for 9.04, one for 9.10, and one for /home.

I'm unsure, but think it would be easier for me to have 9.04 and its swap in one partition, 9.10 and its swap in another, and then /home in another.  I think I want the separate swap partitions for Jaunty and Karmic, I just want them to be independent of one another.  Does this sound reasonable?

I'm hoping it works this way, that when I go to install 9.04 on the first partition, that the swap will be made within that partition, and installing 9.10 on the second partition will put it's swap in that partition.  This sounds like I would have to create extended partitions within the partitions.  Preferably my installs will do this themselves.  Is that correct?  Can I accomplish this without being a wizard?

Quite a bit I know, but THANKS for any advice.

---

### Post by JBAlaska on 2009-12-01
Your distro's will share a common swap partition, so you need 1-/ for 9.04 1-/ for 9.10 1-/home and one swap. So if your only going to use the 4 partitions you can make them all primary. But if you decide later to resize and add another partition you should think about using 1-primary 1-swap 1-extended and 2 logical inside the extended.

Both methods are really quite simple with the LiveCD and Gparted.

One note 9.04 uses legacy grub and 9.10 uses grub2, so you might want to either use legacy on both versions or install 9.10 first and use os-prober and update-grub to setup your 9.04 boot.

---

### Post by dcstar on 2009-12-01
> **isee said:**
> 
.......
I'm hoping it works this way, that when I go to install 9.04 on the first partition, that the swap will be made within that partition, and installing 9.10 on the second partition will put it's swap in that partition.  This sounds like I would have to create extended partitions within the partitions.  Preferably my installs will do this themselves.  Is that correct?  Can I accomplish this without being a wizard?


Just use the manual partition option in the install process.

Set aside 10GB of space for each version's root partition, and whatever you need for /home and swap (put them in the Extended partition with lots of space disk space for any future partitions)

After you install the first version (do 9.04 first), just repeat the process with the 9.10 install giving it 10GB of space for the root partition and set it to use the existing /home and swap.

---

### Post by isee on 2009-12-01
Thanks Much!

> **JBAlaska said:**
> Your distro's will share a common swap partition.

This wasn't what happened when I installed 9.04 and then 9.10 for dual boot.  9.10 created an extended partition, /dev/sda2, and it has in it /dev/sda5 and /dev/sda7, both are swap.  /dev/sda6 is the ext4 it created for itself, within the extended partition.

I think 9.10 just expanded the original extended partition that 9.04's swap was in, and created it's own swap also.  Kinda frustrating, as I'd read about shared swaps.

So I just want to reformat.  Creating 4 partitions sounds like a way I'd like to go then, but when I then first install 9.04, how do I instruct it to make it's swap in partition 4?

Really, I'd like 9.04 and its swap in one partition , to be left alone so I don't have to be doing complete reinstalls.  I have issues with 9.10, so I would like it on its own partition, with its own swap.

As 9.04 will be the first install, I plan on keeping the Legacy Grub.

---

### Post by isee on 2009-12-01
So 2 primary partitions and 1 extended partition for \home and swap?

Can I not just have 9.04 with swap on the first 10 or 15 gigs of my HD in one partition (extended or not), leaving the rest of my HD at my disposal for other partitions and installations?

---

### Post by oldfred on 2009-12-01
Swap is always a separate partition as normally installed. There is some way to create a swap file but I do not know how. If you create partitions in advance you need to use the manual/advanced install and just tell the installer what partition to use. You have to keep track of your partitions if you have a lot.

I also created /data and a /test for alternate installs and when I installed I mixed them up, fortunately I had no data yet in the data partition so I did not lose anything.

---

### Post by dcstar on 2009-12-02
> **isee said:**
> 
.......
As 9.04 will be the first install, I plan on keeping the Legacy Grub.

The last installation will install it's version of Grub.

It is fairly easy to change 9.10 to use legacy Grub - just search out the instructions.

---

