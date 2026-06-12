---
title: "DD Help"
date: 2010-08-06
forum: General Help
---

### Post by oschoices on 2010-08-06
Hi

Am quite new to Ubuntu (10.04) and have recently reinstalled XP.  I want to make an image of my windows partition to save time and effort when wanting to restore this.  I read the Ubuntu documentation on Drive Imaging [https://help.ubuntu.com/community/DriveImaging](https://help.ubuntu.com/community/DriveImaging) and am wondering if I've done things ok?

I've booted using the Live CD.
Windows is on sda1 and is a 50GB partition.
I have a hidden ntfs partition on the same hard drive at sda9 of 10GB.

The first time I tried this I got an error regarding my output file saying "Not a directory".  I'm assuming that was because I hadn't mounted sda9.  It also reported an error saying permission denied on sda1.

I then mounted sda9
```

sudo mount /dev/sda9 /mnt

```

I then changed to root as I thought not being in that was why I was getting the permissions error.
```

sudo -s

```

I've then done the following;
```

dd if=/dev/sda1 bs=1024 | gzip > /mnt/sda1.bin.gz

```

The terminal window is just showing a flashing cursor in the bottom left corner under the above command line input.

Is the fact that my mount partition being smaller than my windows partition going to cause a problem or will gzip solve that? My Windows install occupies about 7.5GB of the 50GB partion.

I'm not sure if dd is just taking a long time to complete the task???

Any ideas please...

---

### Post by dino99 on 2010-08-06
the mount partition have to be larger that the one saved (logical as there are some transitional savings before the ultimate one, same thing when zipping, the system need free room to do the transitional work)

good to allow 120 % of initial space

---

### Post by oschoices on 2010-08-06
Hi dino99

Thanks for the quick response.

Is there a safe way to kill this dd process as I'm assuming it's still running?

Do you mean I should allow 120% of 50GB or 120% of 7.5GB?

---

### Post by dino99 on 2010-08-06
> **oschoices said:**
> Hi dino99

Thanks for the quick response.

Is there a safe way to kill this dd process as I'm assuming it's still running?

Do you mean I should allow 120% of 50GB or 120% of 7.5GB?

of 7.5 indeed  :)

---

### Post by oschoices on 2010-08-06
So 10GB should be large enough then for the output file?

---

### Post by oschoices on 2010-08-06
Anyone else here that can help with this please?

---

### Post by oschoices on 2010-08-06
Has everyone given up on this thread?  I would just like a courteous answer in plain english without being cryptic or ambiguous....

---

### Post by Ocxic on 2010-08-06
if your copying/saving an image of 10GB you need at least 11GB of free space in the drive/partition your saving the data to.

---

### Post by oschoices on 2010-08-06
Hi Ocxic

When your saying an image of 10GB are you referring to the overall size of the files, in my case my XP OS is 7.5GB or are you referring to the size of the source partition?

---

### Post by dandnsmith on 2010-08-06
> Is there a safe way to kill this dd process as I'm assuming it's still running?

Suspend the process, to allow you to access the command line, with ctrl-z
list the process(es) to get the process id for the dd command with 
ps -ef |grep dd   (you might need sudo for this and the next)
kill the process to stop the copy with 
kill -9 *process id*

HTH

---

### Post by Ocxic on 2010-08-06
ok, here we go..

The "dd" utility will create a "byte-for-byte" copy of whatever it is your copying. In this case a 7.5GB partition that you have Windows XP installed on.

So you will need enough free space on your destination to hold all that data. so you will need at least 8GB of free space on your destination in order to save all that data, i would recommend 10GB of free space, so you have a little bit of leeway while copying, you don't want to run out of space.

dd will NOT show any progress, and will simply look like it is doing nothing until it is finished, and returns you to a command prompt. This can take a long time, something like 15-20min for the amount of data you will be copying(longer if you use compression).

---

### Post by kibrg90 on 2010-12-15
can someone help me.....i need the command to create the image of sda8 to sda7/filename.iso

---

