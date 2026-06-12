---
title: "Linux Swap?"
date: 2010-01-25
forum: General Help
---

### Post by ManyBeers on 2010-01-25
Can Ubuntu swap partition go in an Extended partition
(a logical partition within the extended)while Ubuntu is on a Primary partition?

---

### Post by cascade9 on 2010-01-25
Yes. ;)

---

### Post by ManyBeers on 2010-01-25
> **cascade9 said:**
> Yes. ;)
Thanks. What about a seperate Home partition.

---

### Post by cascade9 on 2010-01-25
Should be fine as well. 

Linux is far less picky about primary/extended partitions than windows is ;)

---

### Post by t4thfavor on 2010-01-25
As a side note, I'm not sure I have ever seen my Linux machines get into their swap more than a few KB :) gotta love it.

I even have old machines that rarely use it.

---

### Post by ManyBeers on 2010-01-25
> **cascade9 said:**
> Should be fine as well. 

Linux is far less picky about primary/extended partitions than windows is ;)

Thanks again fellas one last thing ...how can i make sure Swap is turned on? In System Monitor Swap is 0 bytes. Since i just deleted the old Partition and made a new larger one on an extended partition i would like to make sure it is being used.

---

### Post by t4thfavor on 2010-01-25
sudo swapon -a
there will also be a relevant entry in /etc/fstab that is mounted as type swap I believe. you will need to change it to the new partition, and your off.

---

### Post by ManyBeers on 2010-01-26
> **t4thfavor said:**
> sudo swapon -a
there will also be a relevant entry in /etc/fstab that is mounted as type swap I believe. you will need to change it to the new partition, and your off.

The entry in my current fstab is the old partition 
sda 3  UUID=78202c82-2142-4f98-889d-8b0444f88194
The new partition is 
sda 5 
How do I get Ubuntu to see and use it? I guess I need the UUID correct?

---

### Post by t4thfavor on 2010-01-26
Those values are stored in /dev/disk/by-^ so you can match them up with the correct device do an 

you don't have to use UUID in case there isn't one in the below directory, you can replace the UUID part with the dev node "/dev/sda3" or whatever it is.

ls -la /dev/disk/by-uuid and look for the new partition. 

Give it a try and see what you come up with.

---

### Post by ManyBeers on 2010-01-26
> **t4thfavor said:**
> Those values are stored in /dev/disk/by-^ so you can match them up with the correct device do an 

you don't have to use UUID in case there isn't one in the below directory, you can replace the UUID part with the dev node "/dev/sda3" or whatever it is.

ls -la /dev/disk/by-uuid and look for the new partition. 

Give it a try and see what you come up with.

Using that code you gave me I was able to determine the UUID of the sda 5 partition and have edited my fstab accordingly. I think everything is fine but I will reboot to make sure. Give me a few minutes to report bavk.

---

### Post by ManyBeers on 2010-01-26
Thanks t4thfavor I just rebooted and opened up System Monitor and though no swap is being used it shows the correct size of my new swap partition so it definitely sees it and i assume swap is on. Thanks a bunch.

---

### Post by t4thfavor on 2010-01-26
Youll be lucky if you ever do see it in use, like I said I have only seen it a few times during heavy video editing and whatnot. NP thats what were here for.

---

### Post by ManyBeers on 2010-01-26
> **t4thfavor said:**
> Youll be lucky if you ever do see it in use, like I said I have only seen it a few times during heavy video editing and whatnot. NP thats what were here for.
Just after i posted my previous post I went ahead and installed some updates and System Monitor showe 36 mbs of swap being used. Probably the updates triggered it's use. So it is now working.

---

### Post by t4thfavor on 2010-01-26
A stunning discovery! Well I guess I have been wrong a few times.

---

### Post by amaroKer on 2010-01-26
Everything gets put in swap for hibernation too.

---

