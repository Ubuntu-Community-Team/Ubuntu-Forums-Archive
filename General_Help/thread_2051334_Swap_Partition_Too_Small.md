---
title: "Swap Partition Too Small"
date: 2012-09-01
forum: General Help
---

### Post by NM5TF on 2012-09-01
I opened GParted to see why my Swap is always running at 100%...when I
installed 12.04 alongside 10.04 for some reason it only allocated a little
over 7MB for Swap....10.04 has the standard 2 GB Swap partition....

There is an unallocated partition of 2 GB that I would like to assign to
my 12.04 Swap partition, but GParted will not let me do it...
the only option I see is "new" or "information"....

There must be a way to do it, short of deleting 10.04....
I need to keep 10.04 for a while...
at least until all the bugs are out of 12.04; some
apps seem to crash 12.04 that never cause any problems 
with 10.04....

Any help out there???

attached is screenshot of GParted

TIA, 

Tommy

---

### Post by roger_1960 on 2012-09-01
Hi

I think you need to increase the size of your extended sda2 to include the unallocated space (it appears to be outside it) and then increase the size of sda5 within the extended partition.

---

### Post by jerome1232 on 2012-09-01
> **NM5TF said:**
> I opened GParted to see why my Swap is always running at 100%...when I
installed 12.04 alongside 10.04 for some reason it only allocated a little
over 7MB for Swap....10.04 has the standard 2 GB Swap partition....

There is an unallocated partition of 2 GB that I would like to assign to
my 12.04 Swap partition, but GParted will not let me do it...
the only option I see is "new" or "information"....

There must be a way to do it, short of deleting 10.04....
I need to keep 10.04 for a while...
at least until all the bugs are out of 12.04; some
apps seem to crash 12.04 that never cause any problems 
with 10.04....

Any help out there???

attached is screenshot of GParted

TIA, 

Tommy

I would just kill the 7 MB swap partiion and just share the 2 GB swap partition between OS's.

first you would need to turn swap off to remove that 7 MB swap
```
sudo swapoff -a
```
Then go into gparted and remove the 7 MB swap partition, it's not needed
Get the uuid of the 2 GB swap partition, and activate it so you have a swap atm
```
sudo blkid | grep swap
sudo swapon -a
```Add  a new entry to fstab for the new swap partition, remove the old one. A new entry would look like this, you can probably just copy and paste the new uuid over the old one.
```
UUID=uuid-goes-right-here         none            swap    sw              0 0
```To edit fstab use this command
```
gksu gedit /etc/fstab
```

---

### Post by NM5TF on 2012-09-01
> **jerome1232 said:**
> I would just kill the 7 MB swap partiion and just share the 2 GB swap partition between OS's.

Then go into gparted and remove the 7 MB swap partition, it's not needed

GParted will not let me delete the 7MB partition unless I unmount all logical partitions greater than 5.....

I worked around this by going into GParted and turning off /dev/sda5 swap, then turned swap on /dev/sda7.....maybe not the most elegant way to do it,
but it works OK now....

When I edited /etc/fstab & put the UUID for /dev/sda7 in, upon reboot it
gave me an error message stating the disk was not ready....I removed the entry for /dev/sda7...

Thanx for the response & help...

Tommy

---

### Post by dcstar on 2012-09-01
> **NM5TF said:**
> I opened GParted to see why my Swap is always running at 100%...when I
installed 12.04 alongside 10.04 for some reason it only allocated a little
over 7MB for Swap....10.04 has the standard 2 GB Swap partition....
..........
Any help out there???


Simply make the /etc/fstab entry for Swap in 12.04 **exactly** the same as in 10.04:

```
gksudo gedit /etc/fstab
```

---

### Post by NM5TF on 2012-09-02
thanks for the reply David....did this, but now get an error message
on boot stating that the disk /dev/sda5 is not ready, or not present...

because it was assigned as swap at 12.04 install, something other than
/etc/fstab still expects it to be there....

it's no big deal as I just use "s" for skip so it will boot, then go to
GParted & turn on both sda5 & sda7 as swap.....

Tommy

---

