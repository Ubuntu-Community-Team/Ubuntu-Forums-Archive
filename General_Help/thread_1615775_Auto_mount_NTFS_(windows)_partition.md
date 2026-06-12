---
title: "Auto mount NTFS (windows) partition"
date: 2010-11-07
forum: General Help
---

### Post by Strategist01 on 2010-11-07
Hi guys.

I have a windows partition on my drive, and I want to access it without having to mount it first, etc. There are just two partitions, windows and Ubuntu. I am running Ubuntu 10.04.1 so I want to mount it on startup.

How would I do this? I saw this article: [http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14) but I don't know if what it describes will work as it's almost 2 years old. I'm not adverse to commands, in fact would probably prefer those.

Thanks.

---

### Post by sikander3786 on 2010-11-07
There are tools like ntfs-config for make that automount easier. Both auto and manual mounting is explained here.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

But mounting a Windows partition inside Ubuntu is not recommended. It might corrupt your Windows install.

---

### Post by Strategist01 on 2010-11-07
I just wanted it to mount in the same way as I mount it normally by clicking in the "50GB Filesystem" button under places. That hasn't caused me any problems, so this shouldn't either?

---

### Post by kniwor on 2010-11-07
10.04 comes with all the necessary tools to mount the NTFS partition I suppose. All you have to do is add another line to your /etc/fstab file to mount it at startup.

```
sudo cp /etc/fstab /etc/fstab.bak 
gksudo gedit /etc/fstab
```

and then add something like this to the file (at the very bottom).

> /dev/sda2 /media/Windows ntfs rw,nosuid,nodev,uid=<user>,gid=<user>,umask=022 0 1

where "/dev/sda2" is the name of your device. If you do not know the name of your device, the  run the "df" command _when you have the windows partition mounted_. It will show the list of all the mounted devices and there you can see the name of your windows partition as something like "/dev/sdaX" or similar. _Replace <user> by your username. _

---

### Post by dino99 on 2010-11-07
if these packages are installed you might find it under: Places - mobil devices

ntfsprogs
ntfs-3g

---

### Post by Strategist01 on 2010-11-07
> **kniwor said:**
> 10.04 comes with all the necessary tools to mount the NTFS partition I suppose. All you have to do is add another line to your /etc/fstab file to mount it at startup.

```
sudo cp /etc/fstab /etc/fstab.bak 
gksudo gedit /etc/fstab
```and then add something like this to the file (at the very bottom).

> /dev/sda2 /media/Windows ntfs rw,nosuid,nodev,uid=<user>,gid=<user>,umask=022 0 1 			 		

where "/dev/sda2" is the name of your device. If you do not know the name of your device, the  run the "df" command _when you have the windows partition mounted_. It will show the list of all the mounted devices and there you can see the name of your windows partition as something like "/dev/sdaX" or similar. _Replace <user> by your username. _

Hi, just to clarify on the line I add to the fstab file, would "/media/windows" be replaced with the drive name?

here's the output of df, with the line pertaining to my NTFS partition:

```
/dev/sda1             48837576  43720952   5116624  90% /media/2E94B9A794B97247
```

so like:

```
/dev/sda1 /media/2E94B9A794B97247 ntfs rw,nosuid,nodev,uid=<user>,gid=<user>,umask=022 0 1
```

With the appropriate user name in place?

Thanks.

---

### Post by lmm5247 on 2010-11-07
ntfs-config is the way to go. easy gui.

```
sudo apt-get install ntfs-config
```

---

### Post by kniwor on 2010-11-07
@Strategist01

That is right, but the name does not have to be that, you can pick whatever you like. But exactly that line should also work fine (with the appropriate username).

---

### Post by Strategist01 on 2010-11-07
> **kniwor said:**
> @Strategist01

That is right, but the name does not have to be that, you can pick whatever you like. But exactly that line should also work fine (with the appropriate username).

Ok thanks, I added that line - now I will see if it will work when I next boot up.

---

### Post by Coplen on 2010-11-07
> **sikander3786 said:**
> There are tools like ntfs-config for make that automount easier. Both auto and manual mounting is explained here.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

But mounting a Windows partition inside Ubuntu is not recommended. It might corrupt your Windows install.

That's a BIG might there, pal. I've never corrupted a windows install when mounting a windows partition inside linux. Or is this some Ubuntu only problem I don't know about?

---

### Post by sikander3786 on 2010-11-07
> **Coplen said:**
> That's a BIG might there, pal. I've never corrupted a windows install when mounting a windows partition inside linux. Or is this some Ubuntu only problem I don't know about?
You can easily corrupt the install :P.

The important Windows files are hidden in Windows drive and you cannot delete them from inside Windows. But if you mount the Windows drive in Ubuntu or any other OS, if you by mistake delete or rename any important file as they are not hidden/protected here, or do something equally silly, you can easily make Windows unbootable or to the least, corrupt some part of it :-)

---

### Post by Morbius1 on 2010-11-07
> **Coplen said:**
> That's a BIG might there, pal. I've never corrupted a windows install when mounting a windows partition inside linux. Or is this some Ubuntu only problem I don't know about?
Then you haven't been doing this very long ;)

SuSE 6.2 used to corrupt the Windows partition all the time and this was in the good old days when there was no write access to NTFS.

I'll agree that the linux ntfs driver has come a long way since then but even today I always mount my Windows system partition - not an ntfs data partition, I'm talking about the system partition - with either a ro option or a umask=227 or both.

---

### Post by sikander3786 on 2010-11-07
> **Morbius1 said:**
> Then you haven't been doing this very long ;)

SuSE 6.2 used to corrupt the Windows partition all the time and this was in the good old days when there was no write access to NTFS.

I'll agree that the linux ntfs driver has come a long way since then but even today I always mount my Windows system partition - not an ntfs data partition, I'm talking about the system partition - with either a ro option or a umask=227 or both.
+1 for that too. Ntfs driver is not known to cause problems like that nowadays but it actually still can...

---

### Post by kniwor on 2010-11-07
That is perhaps true, but I would not worry so much about it. Besides, windows is perfectly capable of screwing it's own files for no reason at all (and often does). So really, while I keep my windows system partition seperate and never mount it unless i need something, it is more because of fear of a human error that I think is more likely. I keep my other NTFS partition mounted all the time with rw permission because that is my primary data partition.

---

### Post by Strategist01 on 2010-11-07
> **kniwor said:**
> @Strategist01

That is right, but the name does not have to be that, you can pick whatever you like. But exactly that line should also work fine (with the appropriate username).

Ok, after I booted back up, my NTFS partition was auto-mounted, so that worked for me. Thanks.

---

