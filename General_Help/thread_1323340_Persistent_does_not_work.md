---
title: "Persistent does not work"
date: 2009-11-11
forum: General Help
---

### Post by sh_eva on 2009-11-11
Hi,

I am using Ubuntu 9.10 - the Karmic Koala and would like to use   my external USB hard disk for the persistent mode.
For this reason I created two partitions: "casper-rw" (ext3, 75GB) and "d" (NTFS, 389GB).

I was trying both labels: "casper-rw" and "casper-cow" but it seems that the persistence does not work (e.g. after changing desktop background and rebooting I have the default background).

I am running Ubuntu with the following boot options (default ones + persistence):

```

file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd/lz quiet splash -- persistent

```Unfortunately the boot options are poorly documented and I am not sure if the options are correct.

If you have any ideas why the persistent mode is not working please let me know. ;)
Thanks for any help.

---

### Post by 824957q on 2009-11-11
you have to delete a partion then re-add a new partion that should fix it :)

---

### Post by sh_eva on 2009-11-11
> **824957q said:**
> you have to delete a partion then re-add a new partion that should fix it :)


Why?

I re-created the partitions but the result is still the same.

Do you mean that it works only with **one partition**? My intention was to have another (NTFS) partition since Ubuntu doesn't need 500GB! I will check it out tomorrow.

---

### Post by sh_eva on 2009-11-12
I tried Ubuntu 6.12 on that partition and it worked fine!!! Ubuntu 9.10 created only folder "Lost+found" but Ubuntu 6.12 created all necessary folders! After that I ran Ubuntu 9.10 in persistent mode and it worked although I had some errors.

After then I removed all files from the partition ("casper-rw", ext3) and Ubuntu 9.10 still has problems to create all necessary files.
Why Ubuntu 9.10 cannot create the files when Ubuntu 6.12 can? Any ideas?

---

