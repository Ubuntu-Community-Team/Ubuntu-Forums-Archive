---
title: "Root Partition Almost FULL"
date: 2010-03-02
forum: General Help
---

### Post by liferules on 2010-03-02
I few months ago I was forced to do a fresh clean install of Karmic becasue my root partition (then 80 GB) was full. I shooulkd have used a LiveCD to resize partitions then but I didn't so when I installed Karmic this time I ended up with a 160GB partition for /.

Color me surprised when last night I got a message that / was at less than 5% free space.

```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            147549816 132358208   7696484  95% /
udev                   1996476       328   1996148   1% /dev
none                   1996476      1692   1994784   1% /dev/shm
none                   1996476       776   1995700   1% /var/run
none                   1996476         0   1996476   0% /var/lock
none                   1996476         0   1996476   0% /lib/init/rw
/dev/sdb1            153834852 127988632  18031804  88% /home

```

What I have done:

1. I routinely do a apt clean so the cache is not an issue. 

2. I do not store backups on /. I use rsnapshot to same backup on an external hard drive.

3. I use Virtualbox but all my hard drives (VDI) are on /home.

I desperately need help or I am on the way to another fresh install.

---

### Post by cd-r80 on 2010-03-02
Clean trash as root?

---

### Post by QLee on 2010-03-02
[QUOTE=liferules]I few months ago I was forced to do a fresh clean install of Karmic becasue my root partition (then 80 GB) was full. I shooulkd have used a LiveCD to resize partitions then but I didn't so when I installed Karmic this time I ended up with a 160GB partition for /.

Color me surprised when last night I got a message that / was at less than 5% free space.[/QUOTE]

What was causing the drive to fill up the first time?

You might try disk usage analyser from the accessories menu with a filesystem scan to identify where all the GBs are ending up and troubleshoot after you have that information.

---

### Post by liferules on 2010-03-02
> **cd-r80 said:**
> Clean trash as root?

I thought of that but I haven't been able to find it. I looked for /root/.local/share/Trash but it does not exist. Any suggestions on how to follow up?

---

### Post by philinux on 2010-03-02
> **liferules said:**
> I thought of that but I haven't been able to find it. I looked for /root/.local/share/Trash but it does not exist. Any suggestions on how to follow up?

What does this command show.

```
df -h
```

See this doc.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by liferules on 2010-03-02
> **philinux said:**
> What does this command show.

```
df -h
```

See this doc.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

```

chuck@chimera:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             141G  127G  7.6G  95% /
udev                  2.0G  340K  2.0G   1% /dev
none                  2.0G  1.7M  2.0G   1% /dev/shm
none                  2.0G  776K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sdb1             147G  122G   19G  87% /home

```

---

### Post by liferules on 2010-03-02
> **philinux said:**
> What does this command show.

```
df -h
```

See this doc.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

I do a pretty good job of managing the obvious disk usage problems. I had already looked over that URL and nothing helped to the degree that I needed it too. I was able to clean out 1GB from various orphaned libs, etc. But the issue ended up being over 130 GB backups storaged in the wrong location. I have concluded that there was a communication error with my external USB backup drive and rsnapshot stored backups at a physical location in /media. The the drive became availabe the system renamed it to /media/backup_ . Per the conf file, rsnapshot continued to store backups at /media/backup not understanding that it was not the desired location    

Thanks for you help. Crisis is over.

---

### Post by Pritamsng on 2010-03-02
check you "trash" or related folder..

---

### Post by Dougie187 on 2010-03-02
You have quite a lot of stuff on your / partition. Mine is never that big and I never fill it up.

What kind of stuff do you store there?

you could try this.

```
sudo apt-get clean
sudo apt-get autoclean
```

They do something like removing the packages that are just sitting around. Not uninstalling anything mind you.

Edit: NM about what you store, I read you had backups going to the wrong place.

---

### Post by liferules on 2010-03-02
> **Pritamsng said:**
> check you "trash" or related folder..

I all ready had. I never was able to find the root Trash folder, but I script Trash cleanup in /home and my external USB before backups run every evening via crontab.

---

### Post by mikewhatever on 2010-03-02
What's the output of <sudo du -hs /*> ?

---

### Post by liferules on 2010-03-02
> **mikewhatever said:**
> What's the output of <sudo du -hs /*> ?

I have already fixed the issue. I can post the results but they will no longer be accurate. I have been able to reduce the disk usage from 95% full to 4%.

---

### Post by mikewhatever on 2010-03-02
That's great.

---

### Post by Pritamsng on 2010-03-03
try rm -rf ~/.Trash/*

---

### Post by mikewhatever on 2010-03-03
> **Pritamsng said:**
> try rm -rf ~/.Trash/*

Did you mean ~/.local/share/Trash/*? Anyway, using 'remove -rf' on local files is a bad practice, sort of like killing a fly with a bomb.

---

### Post by liferules on 2010-03-03
> **mikewhatever said:**
> Did you mean ~/.local/share/Trash/*? Anyway, using 'remove -rf' on local files is a bad practice, sort of like killing a fly with a bomb.

Actually it was the root partition I was having problems with and /home was on a different partition. So the correct command is:

```

sudo rm -rf /root/.local/share/Trash/*

```

I actually have this scripted to run in crontab an hour before my nightly rsnapshot backup begins on /root, /home, and /media/backup.

---

