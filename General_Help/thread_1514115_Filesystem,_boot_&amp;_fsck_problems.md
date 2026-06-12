---
title: "Filesystem, boot &amp; fsck problems"
date: 2010-06-20
forum: General Help
---

### Post by hamzamian on 2010-06-20
Hi,
 
Been using Ubuntu about six months now but so far I've been able to solve any problems with all the existing postings on this board (thanks everyone!).
 
Unfortunately I've now run into a problem I can't solve. My machine was not shut down cleanly last time and I appear to have corrupted the filesystem as I get a message asking me to run fsck and drops me into a shell instead of booting.
 
running fsck from this shell didn't seem to produce much in the way of positive results unfortunately. (I have 3 hard drives and all report errors)... So i booted using a LiveCD and tried to run fsck from there
 
running
 
```

fsck -Cy /dev/sda1

```
 
seems to have fixed the first drive (the one with the system installed on it), or at least fsck reports its clean.
 
Unfortunately running
 
```

fsck -Cy /dev/sdb1
or
fsck -Cy /dev/sdc1

```
 
makes fsck run initially but then just makes the machine hang.
 
As stupid as this is ... I have data on these drives that wasn't backed up, I'm happy to take my chances as recover as much as I can from them but any suggestions as to what my next steps should be?
 
I tried mounting the disk anyway to copy the data onto another drive and it lets me mount it but when copying the data it invariably causes the machine to hang at some point as well :(
 
Any help would be greatly appreciated.
 
Running Ubuntu Desktop Edition x32 Karmic.
 
Thanks
Hamza

---

### Post by arrange on 2010-06-20
[COLOR="DimGray"]I tried mounting the disk anyway to copy the data onto another drive and it lets me mount it but when copying the data it invariably causes the machine to hang at some point as well[/COLOR]
So this mean you can mount the partitions without any error?
If you copy files one by one (for a test), copying works?

Try the original copying attempt again, and when it hangs, look at the end of the log file */var/log/syslog* to check if there are any related messages.

---

### Post by hamzamian on 2010-06-20
hi,
 
yes i can mount the drive and copy one or two files as test seems to work. I guess its the corrupted files that cause it to hang.
 
Unfortunately it doesn't just hang the copy process but the whole machine and since I'm running with a LiveCD I don't think there's any way for me to go back and look at logs from a previous session once I restart the machine is there?
 
I could in theory copy all the files one by one till it hangs and then I know which one to skip next time but there are many thousands of files so its not really a feasible solution.

---

### Post by arrange on 2010-06-20
OK, so can you launch the *Palimpsest Disk Utility* and check if the HDD is "healthy"?

---

### Post by hamzamian on 2010-06-20
thanks for the suggestion. I'll give this a go tomorrow evening when I'm back with the computer.

If it doesn't help, is it worth pulling the drives out and perhaps connecting them to another machine via USB? Will that help at all? I have another laptop running Karmic I can connect them to potentially...

---

### Post by hamzamian on 2010-06-21
ok so managed to run palimpsest and it reports that all the discs are healthy.
 
That's a good start i'm sure... but I'm still not sure how to actually manage to recover my data from them.
 
Any suggestions?
 
Thanks again for all your help so far.
 
Hamza

---

### Post by arrange on 2010-06-21
OK, I would run *rsync* to copy (back up) the data and see where the problem lies```
sudo rsync -av /where_from/ /where_to
```so for instance ```
sudo rsync -av /media/my_data/ /media/backup/my_data_backup
```As you will be running *rsync* with the **-v** (*verbose*) option, you'll be able to see where exactly it gets stuck.

---

### Post by hamzamian on 2010-06-21
now why didn't i think to use rsync...
 
that's copying over now, will see how far it gets.
 
I presume my best bet is to reformat the disks and start again once I've managed to recover the data from them correct? or should I just try and carry on using them as is somehow?

---

### Post by hamzamian on 2010-06-23
thanks for all your help arrange. I managed to get most of the data off the drives using a combination of rsync and cp -r
 
guess i should probably format the drives again and start from scratch to make sure i dont have any more problems?

---

### Post by arrange on 2010-06-23
[COLOR="DimGray"]i should probably format the drives again and start from scratch[/COLOR]
You don't write where exactly it got stuck or provide any logs so it's hard to say, but generally - yes :)

---

