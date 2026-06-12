---
title: "Corrupted ext4 /home partition while expanding it"
date: 2010-12-23
forum: General Help
---

### Post by behnaam on 2010-12-23
Long story short,

Last night I booted into the live cd to increase the size of my /home partition, when it the process was 50% done ubuntu froze and wouldn't respond to anything. Tried accessing tty and to kill gdm, but it simply didnt respond to anything. I let the computer to be on until this morning to see if it would magically start work, and it didnt. So I was forced to make a hard reboot, and I knew what the outcome of that would be

So now I have a corrupted /home partition. I tried to fsck it and repair it that way, but no luck on that end.

So my question is how I could possibly "reset" the separate /home partition if I choose to format it?
How can I restore as much data as possible from the /home partition?

I really don't want to reinstall ubuntu and set everything up again as I just did it 2 days ago :/

Output of sudo e2fsck -f -y -v /dev/sda7:
```

e2fsck 1.41.12 (17-May-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  123504 inodes used (3.77%)
     253 non-contiguous files (0.2%)
      68 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 2672/2670/2667
         Extent depth histogram: 111769/51/2
 7453073 blocks used (56.86%)
       0 bad blocks
       4 large files

  100851 regular files
   10787 directories
    1146 character device files
    1320 block device files
    1177 fifos
       3 links
    7126 symbolic links (6897 fast symbolic links)
    1088 sockets
--------
  123498 files

```Thanks in advance!

---

### Post by Quackers on 2010-12-23
Did you try to expand your /home partition while it was mounted?

---

### Post by behnaam on 2010-12-23
> **Quackers said:**
> Did you try to expand your /home partition while it was mounted?

Of course not, thats why I rebooted into the live cd :)

After fsck I've got a lost+found dir, trying to recover at least some files I've found there.

Anybody know how I could clean the /home partition without the need to do a complete fresh install?

---

### Post by Quackers on 2010-12-23
OK thanks.
I haven't used it myself but people have had a lot of success with testdisk. I'm not sure whether it is installed by default on the Live cd. In a terminal try ```
sudo testdisk
``` and see if it runs. If it doesn't you will need to install it via synaptic package manager, then run it with that command. 
Take your time and be careful :-)
More details are here
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by psusi on 2010-12-23
The output of e2fsck you posted doesn't seem to say anything is wrong.  Is e2fsck happy with the fs now or not?  If it is happy now but put a bunch of files in lost+found, then you will need to sort them out by hand.

---

### Post by behnaam on 2010-12-23
> **Quackers said:**
> OK thanks.
I haven't used it myself but people have had a lot of success with testdisk. I'm not sure whether it is installed by default on the Live cd. In a terminal try ```
sudo testdisk
``` and see if it runs. If it doesn't you will need to install it via synaptic package manager, then run it with that command. 
Take your time and be careful :-)
More details are here
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

> **psusi said:**
> The output of e2fsck you posted doesn't seem to say anything is wrong.  Is e2fsck happy with the fs now or not?  If it is happy now but put a bunch of files in lost+found, then you will need to sort them out by hand.

Thanks for helping out, I gave up as the lost+found directories and files where just partially restored from what I had in my home dir before.

I really hate doing a fresh installs and set up everything again when things go wrong, but that's the hit you have to take when you don't do stuff with precaution.

Merry Christmas and Happy New Year :)

---

