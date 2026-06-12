---
title: "Use other partition as home + backup"
date: 2010-06-19
forum: General Help
---

### Post by jesuisbenjamin on 2010-06-19
Dear forum,

I have a Dell laptop with dual-boot Vista-Ubuntu. I never ever used Vista and am not planning to.
I'd like to move from 9.04 to 10.04. I know how to backup and run an update already. But for the sake of simplicity, i'd prefer to erase the data of the current Vista-partition and use it as my /home content.
It makes more sense to me, so i don't have to make a backup of everything for ever again and again when installing or updating my OS. Does it make sense to do that? Is it possible? If so what is the neatest way of doing this?

Thanks for your advice.
B.

---

### Post by jms1989 on 2010-06-19
well you can format and copy your home folder to the old vista partition then do the install, just remember to set the vista partition as /home and whatever filesystem you chose to use.

---

### Post by jesuisbenjamin on 2010-06-19
> **jms1989 said:**
> well you can format and copy your home folder to the old vista partition then do the install
OK, if i do that will it affect the dual boot at start up? (grub)

> **jms1989 said:**
> just remember to set the vista partition as /home and whatever filesystem you chose to use.

How do i set the partition as /home?

Thanks.

---

### Post by Rabbut on 2010-06-19
Setting a different directory as your home one should make no difference to the way the system boots AFAIK. :-k I'd await confirmation however from someone that knows for sure...

To set a different directory as your home, when installing 10.0, you'd select that directory as home during the install process if I recall correctly. I only know how to point to a different partition though, not a directory on an existing file system. Mind you, you can't use a Windows NTFS file system for a pure-Linux boot partition AFAIK.

The simplist way to do what your asking from where I'm sat would be to shrink the existing Windows partition on the install. You'd then create a Linux EXT2/3/4 partition beside it and install Ubuntu onto that. You'd then set the old Windows partition as your home directory in the advanced disk set-up window.:wink:

Just remember to un-check the option of having GRUB set-up Vista as an alternative OS when you install, so you don't get the options screen on boot. It's tidier that way, and also stops you having a null pointer to a none-existant OS after you wipe Windows files from that partition after getting 10.04 off the ground:lolflag:

---

### Post by jesuisbenjamin on 2010-06-20
Ha thanks...


@Rabbut: the process you are describing to me is confusing. It seems i'll end up with 3 partitions.

I thought i'd have to format the Vista partition so Ubuntu can use it, then move my /home there. Then i would install 10.04 from scratch on the main partition (since i understand a clean install is better than an upgrade(?))

(if i choose to upgrade instead, can i still point at the other partition?)

But when installing or after installing can i point at the other partition as my /home and how?

Thanks.
B.

---

### Post by jesuisbenjamin on 2010-06-21
Hi there,

is there anyone who wishes to share his/her expertise on the above?
Thanks.
B.

---

### Post by jms1989 on 2010-06-22
ok, during the installer once you get to the partition menu select advanced menu or custom of something like that, once there, you'll want to make a partition as / (root) and one as /home. Since you're wanting to make the vista partition as /home, right click on it and click edit or select it and click the edit button, choose the file system as ext4 (the best one available now) tick the box to format and if everything looks right, click ok. For the root partition, pick the one you want to use and repeat the steps for the /home partition.

If want, you could just go with a new layout and you can create your own partition sizes, order than like this, swap, root partition, and /home. By making a new layout, you destroy whatever is on there already and starting anew.

Does this make any sense?

---

### Post by jesuisbenjamin on 2010-06-22
It kind of does make sense.
Yet i believe what you suggest would simply erase all the current data from my disk. 
I would like to format the Vista partition, paste there my current /home and then install Lucid on the main partition and tell it to look into the other partition for /home.
Is it possible to do so?

Thanks.

---

### Post by sf-it-services on 2010-06-22
mount NTFS partition as /storage just use it as space for  downloads etc..... my /home directory has links to various drives for storage, documents, etc none of them are on my / partition

if you are reinstalling, its simple just mount /home on the partition you want during install

---

### Post by jesuisbenjamin on 2010-06-22
Ok thanks,

so basically once i created /storage and put there all my docs, mp3s etc, i can install.
During install i can add /home on /storage without erasing the already existing /storage data?
And alternatively, i can keep /home on the main partition and link it to /storage.

Am i understanding correctly? (i need to make sure i am not going to erase all my data of my study)

Now with regard to formating the Vista partition:
I have sda1, 2 and 3 which seem to be allocated to Vista and recovery. Can i just erase all three and make one ext4 partition of them? cf. screenshot.

Thanks.
B.

PS: in view of my partition size, can i install Lucid on currently sda1+2+3 and allocate /home to the current /home on sda4 which is used by 9.04?

---

