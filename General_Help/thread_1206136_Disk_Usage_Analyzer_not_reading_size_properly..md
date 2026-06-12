---
title: "Disk Usage Analyzer not reading size properly."
date: 2009-07-06
forum: General Help
---

### Post by Wiebelhaus on 2009-07-06
As you can see in the screen shot , The windows partition has been scanned with DUA and it has detected Stacey's profile as having 566.6MB , But properties has detected the proper size of Stacy's Vista profile as being 12.7GB large. Also in the screen shot is the location so that you can see that I've scanned an external windows vista drive for data recovery reasons and the DUA is mis-detecting the size.

Anyone have a solution?

Thanks.

---

### Post by Wiebelhaus on 2009-07-07
As you can see in this screen shot , It reads perfectly once the data is local.

---

### Post by Wiebelhaus on 2009-07-09
Just that 24 hour bump.

Thanks.

---

### Post by Wiebelhaus on 2009-07-10
Another screenshot of DUA mis-detecting the proper size but Nautilus properties correctly detecting size.

---

### Post by Wiebelhaus on 2009-07-10
CLI alternative.

you can use "du [options] [path]"

Or durep "[options] [path]"

and of course you can cd to the directory and run them.

Not as pretty as the graphical representation but it gets the job done just the same.

---

### Post by MystaMax on 2009-07-30
I'm having a very similar problem. I actually get different results from the command line (using du -hs), the nautilus folder properties window, and Disk Usage Analyzer.

For example, I have a 7GB folder on my desktop. Nautilus says 7GB, "du -hs" says 7.3GB, and Disk Usage Anaylzer states 7.2GB. This example isn't as drastic as some others I've run into.

Did you ever find out why it was doing this?

---

### Post by Wiebelhaus on 2009-07-30
> **MystaMax said:**
> I'm having a very similar problem. I actually get different results from the command line (using du -hs), the nautilus folder properties window, and Disk Usage Analyzer.

For example, I have a 7GB folder on my desktop. Nautilus says 7GB, "du -hs" says 7.3GB, and Disk Usage Anaylzer states 7.2GB. This example isn't as drastic as some others I've run into.

Did you ever find out why it was doing this?

No , I have not found a solution to this as of 7/30/09.

---

### Post by ler0nudb2 on 2009-09-12
Dell Vostro A90, 1GB, 16GB SSD, Ubuntu 8.4

Disk Usage Analyzer reports:
   Total filesystem capacity 27.8 GB (used: 13.8 GB available: 14.0 GB)
   Total filesystem usage: 49.6% 13.8 GB

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              14G  6.9G  6.3G  53% /
varrun                501M  104K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   36K  501M   1% /dev
devshm                501M   52K  501M   1% /dev/shm
lrm                   501M  1.9M  499M   1% /lib/modules/2.6.24-24-lpia/volatile
gvfs-fuse-daemon       14G  6.9G  6.3G  53% /home/ler0nldb2/.gvfs

Why DUA reports twice the actual size?

---

### Post by riverfr0zen on 2009-09-25
> **Wiebelhaus said:**
> As you can see in the screen shot , The windows partition has been scanned with DUA and it has detected Stacey's profile as having 566.6MB , But properties has detected the proper size of Stacy's Vista profile as being 12.7GB large. Also in the screen shot is the location so that you can see that I've scanned an external windows vista drive for data recovery reasons and the DUA is mis-detecting the size.


I have the same problem analyzing an NTFS partition. DUA is reporting the wrong usage both overall, and on specific folders.

---

### Post by Wiebelhaus on 2009-10-21
Issue resolved in 9.10 Beta.

Cheers and thanks.

---

