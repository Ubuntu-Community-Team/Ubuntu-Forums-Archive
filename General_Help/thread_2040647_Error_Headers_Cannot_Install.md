---
title: "Error: Headers Cannot Install"
date: 2012-08-11
forum: General Help
---

### Post by Katla on 2012-08-11
I am trying to install the latest headers and kernels using the Update Manager. Getting an error telling me that the generic headers cannot install as there is no room. It needs 11 MB. I've got 285 free. Tried using the install -f command as well as Package Manager. Nothing doing. Elsewhere it tells me there are unmet dependencies. 

I've been racking up errors ever since upgrading to 12.04 a few months ago (reboots frighten me nowadays). Furthermore, I've got 7GB for my / partition, but less than 300MB free. I'd made the mistaken assumption earlier of thinking that what I was downloading was going into my Home partition. I could use some advice on cleaning that up. Beyond the apt-get clean command. 

But first and foremost, getting these headers installed. Any advice would be appreciated, and don't be afraid to dumb it down. Thank you.

---

### Post by spjackson on 2012-08-11
Could you please post the output of:
```

df -h
df -i

```A filesystem has a maximum size for the sum of the size of all its files. The first command shows used/free in terms of this. However, a filesystem also has a maximum number of files it can hold, irrespective of the size of the file contents. The second command shows used/free in these terms - these are know as inodes. If you are running short of inodes, then see if you have old versions of kernel headers that can be removed.

---

### Post by Katla on 2012-08-11
> johnny@johnny-GA-MA69GM-S2H:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       7.5G  6.8G  330M  96% /
udev            3.9G   12K  3.9G   1% /dev
tmpfs           1.6G  940K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  768K  3.9G   1% /run/shm
/dev/sda1       448M  342M   82M  81% /boot
/dev/sda6       912G  357G  510G  42% /home

> johnny@johnny-GA-MA69GM-S2H:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda5        488640 481631     7009   99% /
udev             195449    567   194882    1% /dev
tmpfs            199089    495   198594    1% /run
none             199089      3   199086    1% /run/lock
none             199089      6   199083    1% /run/shm
/dev/sda1        244320    313   244007    1% /boot
/dev/sda6      59834368  84075 59750293    1% /home


Where would I find these old kernel headers? I suspect i have a lot of such clutter, but am not sure where to go.

---

### Post by spjackson on 2012-08-11
They are in /usr/src, but the right way to remove them would be via synaptic or apt-get.

---

### Post by Katla on 2012-08-11
And I just delete them all, save for the latest batch (3.2.0-29, in my case)? 

I'd assumed they were removed upon upgrade. Shows what I know.

---

### Post by spjackson on 2012-08-13
> **Katla said:**
> And I just delete them all, save for the latest batch (3.2.0-29, in my case)? 

Yes. You don't need old kernel headers, unless you are going to build modules for those old kernels.

---

### Post by Katla on 2012-08-13
Thanks for the help. I cleaned out a lot of the old kernels, enabling me to complete that install. It is also good knowledge to have going forward. As well I updated grub2. Hoping that future reboots go more smoothly for me now.

---

