---
title: "partimage not in 64bit repos"
date: 2009-12-18
forum: General Help
---

### Post by lavinog on 2009-12-18
Is there a reason why partimage is only available for 32bit installs?

---

### Post by yavoh on 2009-12-18
I'm not sure of the reason, but it is true that there hasn't been a 64-bit build in a while.  Some people have had luck using older builds, others have not.  If you want to image your drive, the easiest way is to boot into a livecd and use the "dd" command:
```
sudo dd if=/input/device/node of=/path/to/output/file.extension
```Remember that if you do it using sudo, the output file will be owned by root at the end.  You can change this using the chown command:
```
sudo chown newowner:newownergroup /file/or/directory
```

---

### Post by dcstar on 2009-12-19
> **lavinog said:**
> Is there a reason why partimage is only available for 32bit installs?

Get it here:

[http://packages.ubuntu.com/search?suite=intrepid&arch=amd64&searchon=names&keywords=partimage](http://packages.ubuntu.com/search?suite=intrepid&arch=amd64&searchon=names&keywords=partimage)

---

### Post by fyo on 2010-02-21
> **dcstar said:**
> Get it here:

[http://packages.ubuntu.com/search?suite=intrepid&arch=amd64&searchon=names&keywords=partimage](http://packages.ubuntu.com/search?suite=intrepid&arch=amd64&searchon=names&keywords=partimage)

Except that version is old and doesn't appear compatible with newer, so if you need to use networking, it won't cut it.

---

### Post by DMurray on 2010-02-24
The disadvantage of using "dd" is that source and target partitions must be EXACTLY of the same size in bytes, because all bytes are read and backed up.
While "partimage" backs up only the bytes in use, so it can be restored to any partition with enough size to receive the data.

---

### Post by lavinog on 2010-02-24
> **DMurray said:**
> The disadvantage of using "dd" is that source and target partitions must be EXACTLY of the same size in bytes, because all bytes are read and backed up.
While "partimage" backs up only the bytes in use, so it can be restored to any partition with enough size to receive the data.

dd_rescue with sparse writes enabled (-a) can be used to conserve space.

---

### Post by Max-B on 2010-06-28
Hi,
I compiled the most recent versione of partimage that should be compatible with Ubuntu 10.04 64bit.
You can downloaded from here:

[partimage_0.6.8_amd64.deb]("http://jumbo.terra.unimo.it/repo/binary/partimage_0.6.9-1_amd64.deb")

or simply type:
```
wget http://repo.max-b.org/binary/partimage_0.6.8_amd64.deb
sudo dpkg -i partimage_0.6.8_amd64.deb
```

Please note that this is the first time I create a deb package from a source. I tested the deb installation on a couple of PC running Ubuntu 10.04 64bit without problem.
Anyway suggestions are more than appreciated.

I hope my post will be useful...
ciao,
Max-B

---

### Post by philinux on 2010-06-28
There is partitionmanager in the 64 bit repo.

Partition Manager is a utility program to help you manage the disk devices,
partitions and file systems on your computer. It allows you to easily create,
copy, move, delete, resize without losing data,** backup and restore partitions.**

---

### Post by Max-B on 2010-06-28
> **philinux said:**
> There is partitionmanager in the 64 bit repo.

Thanks for your suggestion, but I personally prefere to use partimage that run under the terminal.
I saw that partitionmanager have more than 80Mb of dependencies...
ciao,
Max-B

---

### Post by philinux on 2010-06-28
> **Max-B said:**
> Thanks for your suggestion, but I personally prefere to use partimage that run under the terminal.
I saw that partitionmanager have more than 80Mb of dependencies...
ciao,
Max-B

Yep that's cos of kde dependencies however I'm a fan of K3B. ;)

---

### Post by OmahaVike on 2010-09-15
[QUOTE=Max-B;9521112]Hi,
I compiled the most recent versione of partimage that should be compatible with Ubuntu 10.04 64bit.
You can downloaded from here:

[partimage_0.6.8_amd64.deb]("http://repo.max-b.org/binary/partimage_0.6.8_amd64.deb")

or simply type:
```
wget http://repo.max-b.org/binary/partimage_0.6.8_amd64.deb
sudo dpkg -i partimage_0.6.8_amd64.deb
```

THANK YOU Max-B !

---

### Post by Max-B on 2010-09-16
Hi,
if someone is interested I compiled the most recent versione of partimage compatible with Ubuntu 10.04 64bit.
You can downloaded from here:

[partimage_0.6.9-1_amd64.deb]("http://repo.max-b.org/binary/partimage_0.6.9-1_amd64.deb")

To install just type:

```
wget http://repo.max-b.org/binary/partimage_0.6.9-1_amd64.deb
sudo dpkg -i partimage_0.6.9-1_amd64.deb

```

ciao,
Max-B

---

### Post by lproven on 2010-10-27
This is fantastic stuff - many many thanks! I was utterly baffled as to why I could find the partimage *docs* but not any binary... Know I know!

---

### Post by drs305 on 2010-10-27
I left partimage for fsarchver when I switched to ext4. Has partimage added capability to backup ext4 yet? Thanks in advance.

---

### Post by aev on 2011-01-27
> **Max-B said:**
> Hi,
if someone is interested I compiled the most recent versione of partimage compatible with Ubuntu 10.04 64bit.
You can downloaded from here:

[partimage_0.6.9-1_amd64.deb]("http://repo.max-b.org/binary/partimage_0.6.9-1_amd64.deb")

To install just type:

```
wget http://repo.max-b.org/binary/partimage_0.6.9-1_amd64.deb
sudo dpkg -i partimage_0.6.9-1_amd64.deb

```

ciao,
Max-B

Thanks a lot man! \\:D/

I am using it to backup the Lenovo hidden partition, since I am planning to completely wipe out the Window$ software.

---

### Post by LewRockwellFAN on 2011-04-25
I'm kinda curious about the original question, why in the 32 and not the 64 repositories? Maybe the 64 is buggier? Maybe somebody decided that FSArchiver was just so much better, that between that, the KDE PM, and DD there just isn't that much reason to go to the work of getting it debugged enough to be confident in it? That would seem reasonable. Experimenting with these and settling on a convenient procedure for backing up my unmounted bootable partitions while I'm running from another, which in turn gets backed up from some other when it isn't mounted is my main current system tinkering project. FSArchiver seems really good and should be easy to use in a script. The KDE PM has a nice gui but as far as I can tell doesn't have adjustable compression, maybe no compression at all. I aborted it when I realized the archive was going to be outrageously humongous. Guess I'll give up on partimage at least for the moment. Must be some good reason it's not in the repository. Now I'll check out DD.  This approach beats the hell out running an imager from a CD or giving Clonezilla its own boot partition.

---

### Post by n8bounds on 2011-05-07
This works (install &#65279;&#65279;&#65279;libssl0.9.8 with apt first) as-is on Natty: [http://packages.debian.org/sid/amd64/partimage/download]("http://packages.debian.org/sid/amd64/partimage/download")

Just in case, I also have it mirrored here: [http://n8.thruhere.net/export/free/debs/partimage_0.6.8-1+b1_amd64.deb]("http://n8.thruhere.net/export/free/debs/partimage_0.6.8-1+b1_amd64.deb")

[http://n8.thruhere.net/blog/?p=1119]("http://n8.thruhere.net/blog/?p=1119")

---

### Post by n8bounds on 2011-05-07
> **drs305 said:**
> I left partimage for fsarchver when I switched to ext4. Has partimage added capability to backup ext4 yet? Thanks in advance.

Yep: [http://www.partimage.org/Supported-Filesystems]("http://www.partimage.org/Supported-Filesystems")

---

### Post by drs305 on 2011-05-07
> **n8bounds said:**
> Yep: [http://www.partimage.org/Supported-Filesystems]("http://www.partimage.org/Supported-Filesystems")

The partimage link lists ext4 but in the right hand column still says it's unsupported...  ?

---

