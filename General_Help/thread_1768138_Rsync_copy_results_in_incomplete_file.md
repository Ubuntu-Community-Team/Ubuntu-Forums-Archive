---
title: "Rsync copy results in incomplete file"
date: 2011-05-26
forum: General Help
---

### Post by NeilR on 2011-05-26
Using Ubuntu Server 10.04 LTS.

I'm new to Ubuntu and testing Rsync.  I successfully copied 3TB of data from a Win7 machine to an MDADM Raid5 array.  All appears to be fine.  Used a Win app for the copy.

I then deleted a 250GB folder on the Raid5 array and recopied the data using Rsync.  Rsync was executed via a Putty session on a WinXP machine.  The source was an eSata attached drive (same drive used for the big 3TB copy) and the destination was the same Raid5 array.  That copied just fine.  I bit verified it with a Win7 app.  Perfect.

I then used the following Rsync script to copy a single 26GB file from that same eSata drive back to (what I intended to be) the Raid5 array:

```
neil@ANTECUBSV:/mnt$ rsync -r -a -v -e  ssh --delete /mnt/disk1/Test/ /mnt/Test
sending incremental file list
created directory /mnt/Test
./
C_VOL-S300-b001.spf

sent 3020267622 bytes  received 34 bytes  50760800.94 bytes/sec
total size is 3019898880  speedup is 1.00
neil@ANTECUBSV:/mnt$ cd raid
```

Note that only about 3GB copied.  No error messages were posted to the putty session.  I made a mistake in the Rsync command, creating the Test folder directly in the mount folder rather than the Raid array, as I intended.  that is a little strange, yes, but I would not think it would cause a partial copy?

The /mnt folder is on my system drive, which had about 34GB available space before the copy, so comfortably would have had 6GB or so after.

The eSata disk is mounted as /mnt/disk1
The Raid5 array is mounted as /mnt/raid

I then recopied the file to the correct intended destination on the Raid5 array, which has about 400GB free space (plenty).

```

neil@ANTECUBSV:/mnt/raid$ rsync -r -a -v -e  ssh --delete /mnt/disk1/Test/ /mnt/raid/Test
sending incremental file list
./
deleting 2010-07-05 Backyard Birds/Thumbs.db
deleting 2010-07-05 Backyard Birds/
C_VOL-S300-b001.spf

sent 11105775462 bytes  received 34 bytes  50366328.78 bytes/sec
total size is 11104419840  speedup is 1.00
neil@ANTECUBSV:/mnt/raid$ df -h

```

Note that only about 11GB was copied, and this was confirmed with an ls -l command.  Now I am correctly copying the file to the Raid array but it is still incomplete.

I then copied the file back to the /mnt folder to see if the problem reproduces:

```
neil@ANTECUBSV:/mnt/raid$ rsync -r -a -v -e  ssh --delete /mnt/disk1/Test/ /mnt/Test
sending incremental file list
created directory /mnt/Test
./
C_VOL-S300-b001.spf

sent 26327927554 bytes  received 34 bytes  56558383.65 bytes/sec
total size is 26324713984  speedup is 1.00
neil@ANTECUBSV:/mnt/raid$ cd /mnt/test
```

This time I got my full 26GB file.

Can anyone explain why I might be getting inconsistent results?  This is quite troubling of course.  I'd also be interested in basic a command line Linux diff app (that does file directory as well as bit level checking) if one is available.

---

### Post by oldfred on 2011-05-26
Is data in Test not just in sub folders of Test?

man rsync has explanation of trailing /. these are the same, trailing / copies contents:
 rsync -av /src/foo /dest
 rsync -av /src/foo/ /dest/foo

---

### Post by NeilR on 2011-05-26
Thanks for the very fast reply!

Yes, the data is directly in Test but I don't understand the significance.  I do understand the trailing slash issue.  If my path was wrong the file would not copy, or would copy someplace I don't want it.  But here I got 2 incomplete copies of the file.

---

### Post by NeilR on 2011-05-26
Just to be very clear, the incomplete copy consisted of one single 26GB file.  It should have not copied at all or copied completely.  It copied partially, twice.

---

### Post by oldfred on 2011-05-26
I was thinking it was more files. Not sure what the issue is as I just use rsync and know enough to get it to work for me.

What format are the partitions? From & to?

Have you tried mc? Midnight Commander

It is in synaptic.
GNU Midnight Commander is a text-mode full-screen file manager. It
uses a two panel interface and a subshell for command execution.

---

### Post by NeilR on 2011-05-26
The source partition is NTFS, created and maintained on Windows (never modified by Linux).

The two target partitions (both tests) are Ext4.

I'll look into Midnight Commander; thanks for the suggestion.

---

### Post by dragonfly41 on 2011-05-26
There is also 
GNOME Commander
and
Tux Commander

---

### Post by NeilR on 2011-05-26
Thanks for the suggestions.

Keep in mind this is for Ubuntu Server - no desktop.  I think that excludes GNOME Commander and Tux Commander?

I don't care if the app has a gui that can run in an SSH shell, as I believe  Midnight Commander does, but I don't want to have to install and boot up a desktop for this job.

---

### Post by dragonfly41 on 2011-05-26
I also have Total Commander ([www.ghisler.com](www.ghisler.com)) running in wine if that helps.

---

### Post by NeilR on 2011-05-27
I think I found the answer to my partial file copy problem...

The source file that Rsync copied from one test folder to another test folder was copied into the source folder yesterday from a Win7 machine via a Win7 app.  I think I know what time I copied it into the source folder based on the time stamp of the (Test) folder created just previously.  I don't think Rsync generates any logs that time stamp it's copies?  And it does not time stamp the output from the verbose logging created when running the command. 

It is very possible that the source file copy was still in process when I first started testing the Rsync command since the operation would have taken about 15 minutes.  That would explain why the first copy delivered only 3GB, the second copy delivered 11GB and all the succeeding copies (4 or 5) delivered the entire 26GB file.  Without time stamped logs of the Rsync operations I can only speculate on this.

If I am right about that it solves one problem and creates another problem, which is that even NTFS files are not write locked during their creation.  Being a long time windows user I am accustomed to having write locks placed on files when they are being created.  This will take some getting used to and of course raises the issue of corrupted files generated from automated backups where something else is writing at the same time.

---

### Post by collisionystm on 2011-05-27
use a capital W to copy the WHOLE file. 

see rsync --help in the terminal

```
rsync -raveW  ssh --delete /mnt/disk1/Test/ /mnt/Test
```

---

### Post by NeilR on 2011-05-27
Thanks for the -W tip, Collision!

But it did not quite work.  I set up a fresh copy into the source folder and immediately re-rean Rsync, getting the following output:


```
neil@ANTECUBSV:/$ rsync -raveW  ssh --delete /mnt/disk1/Test/ /mnt/raid/Test
sending incremental file list
rsync: link_stat "/ssh" failed: No such file or directory (2)
./
IO error encountered -- skipping file deletion
.fuse_hidden0016c1d600000001
C_VOL-S300-b001.spf

sent 42216841937 bytes  received 53 bytes  38361510.21 bytes/sec
total size is 27053007360  speedup is 0.64
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]
neil@ANTECUBSV:/$ ls /mnt/raid/Test
C_VOL-S300-b001.spf



neil@ANTECUBSV:/$ sudo ls /mnt/raid/Test -A -l
total 41222364
-rwxrwxrwx 1 neil neil 15886974976 2011-05-27 10:00 C_VOL-S300-b001.spf
-rwxrwxrwx 1 neil neil 26324713984 2010-12-20 00:37 .fuse_hidden0016c1d600000001
neil@ANTECUBSV:/$

```

Rather than skip the file it appeared to stay with the copy, copying and waiting for the data to come in.  Because of the network throughput, the copy into the Rsync source folder was much slower than the Rsync copy is capable of (by about 2-3x).

The .fuse file is the correct size.  The C_VOL-S300-b001.spf file is not.  Both files were generated by the Win7 copy app (a 3rd party copy app called Teracopy) during the copy.  Not sure why there are two files since most copy apps just make one file and then rename the file when it's done.   The copy app did leave just the correct file in the source Rsync source folder, as it should.

I guess Rsync got confused?

---

### Post by collisionystm on 2011-05-27
```
rsync -rqaHpEAXogt -e/usr/bin/ssh root@192.168.7.1:/ /media/usb0/rsync_backups/PA_Server
```

Thats what I use

---

### Post by collisionystm on 2011-05-27
Woops, on your command, try this...

```
rsync -raveW --delete /mnt/disk1/Test/ /mnt/Test
```

---

### Post by NeilR on 2011-05-27
> **collisionystm said:**
> Woops, on your command, try this...

```
rsync -raveW --delete /mnt/disk1/Test/ /mnt/Test
```

In my last test above I did this:

```
rsync -raveW  ssh --delete /mnt/disk1/Test/ /mnt/raid/Test
```

How does that differ from your suggestion?  I changed the output folder by intent because the I think the /mnt/Test partition (the OS partition!) was filling up after adding -W because two files were output and that partition has little spare space.  I really want this output in /mnt/raid/Test anyway.

---

### Post by collisionystm on 2011-05-27
....because you cant use SSH to copy to a local directory ;)

If you were indeed using ssh to another box, you would use something along the lines of my command 

> rsync -rqaHpEAXogt -e/usr/bin/ssh root@192.168.7.1:/ /media/usb0/rsync_backups/PA_Server

---

### Post by NeilR on 2011-05-27
My ssh session was on an XP machine running Putty.

If my ssh session basically works, why do I need more options?  I'm not sure what in your suggested command is important in this context.  Being a newbie :D

Thanks for your indulgence!

---

### Post by collisionystm on 2011-05-27
> **NeilR said:**
> My ssh session was on an XP machine running Putty.

If my ssh session basically works, why do I need more options?  I'm not sure what in your suggested command is important in this context.  Being a newbie :D

Thanks for your indulgence!

No I mean don't use ssh in your rsync command lol.

You are copying from one directory on your server to another, yes?

You dont need ssh unless you are copying from one server to the other

---

### Post by NeilR on 2011-05-27
> **collisionystm said:**
> No I mean don't use ssh in your rsync command lol.

You are copying from one directory on your server to another, yes?

You dont need ssh unless you are copying from one server to the other

OK, here is my latest test:


```
neil@ANTECUBSV:~$ rsync -raHpEAXogtvW  --delete /mnt/disk1/Test/ /mnt/raid/Test
sending incremental file list
C_VOL-S300-b001.spf

sent 3288735851 bytes  received 31 bytes  40352587.51 bytes/sec
total size is 3288334336  speedup is 1.00

```

I used your options that I think you were suggesting I use (??), but replacing -q with -v to better monitor things, and adding -W, which you previously suggested.

I still get a partial file.  This time I did not get any strange errors in the Rsync output; maybe that had something to do with removing SSH from the command.  The important thing is that -W is not changing anything.

---

