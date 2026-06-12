---
title: "Startup Time - Seems longer"
date: 2010-11-26
forum: General Help
---

### Post by mathgeek2000 on 2010-11-26
Since the most recent kernel upgrade, from **2.6.32-25-generic to 2.6.32-26-generic**, Specifically 2.6.32.26.28, my startup time seems longer --
There is a noticeable delay waiting for the 'Starting up' line before the Ubuntu Splash screen.
--
Here is the Grub code:

```
title        Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic
uuid        d2c14fed-cf0e-4c66-bf80-4f8450a931a1
kernel        /vmlinuz-2.6.32-26-generic root=UUID=f10932af-7426-40a0-a3c7-f13d01273093 ro quiet splash 
initrd        /initrd.img-2.6.32-26-generic
quiet
```

And here is my disk space:

```
jonas@galileo:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              19G  3.8G   15G  21% /
none                  996M  292K  996M   1% /dev
none                 1003M  216K 1003M   1% /dev/shm
none                 1003M  304K 1003M   1% /var/run
none                 1003M     0 1003M   0% /var/lock
none                 1003M     0 1003M   0% /lib/init/rw
**/dev/sda1              64M   26M   36M  42% /boot**
/dev/sda3             126G   58G   63G  49% /home
/home/jonas/.Private  126G   58G   63G  49% /home/jonas
jonas@galileo:~$ 

```

The /boot partition, as with the others is ext4. I've read a lot about fragmentation, and not needing defragmentation utilities it in Linux, but what are the advantages here of ext4?
Since that partition is only needed for booting, would it help to convert it back to ext3, or could it be 'rebuilt'?

In adding the new kernel, when the patch came down, I installed the new kernel, then once it was working deleted the older obsolete one.

---

### Post by mathgeek2000 on 2010-11-27
> **mathgeek2000 said:**
> ... would it help to convert it back to ext3, or could it be 'rebuilt'? ....

Well I reformatted my /boot Partition as ext3, and the time went from 30 or 40 seconds to 0,  - which only begs the question. -- why? and if it had to do with fragmentation, how can you tell if an ext3, or ext4 partition needs defragging, or is fragmented.? -- Or was it something else.

---

