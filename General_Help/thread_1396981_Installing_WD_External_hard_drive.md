---
title: "Installing WD External hard drive"
date: 2010-02-02
forum: General Help
---

### Post by Gretl on 2010-02-02
I just bought WD External Hard drive for my laptop and found out
that there is no support for Linux. I am running Ubuntu 9.10 and would greatly appreciate any advice on installation. Thank you.

---

### Post by Leppie on 2010-02-02
hi and welcome to the community,

this sounds a bit odd...
i'd say that most external drives do not any particular drivers in order to use them with linux.
what model is the device?
could you post the output of the following command:
```
dmesg | tail
```

---

### Post by Gretl on 2010-02-02
Hi,Leppie. Basically, I bought a new hard drive (WD My Book Essential 1 TB) for backup only. The instructions are for windows/mac only. I am not sure how to install this new drive.Thank you.

---

### Post by Gretl on 2010-02-02
Just to be clear here - I looked at the installation instructions for windows/mac and there were multiple setup steps. I want to know how to setup my new hard drive so that I can backup my files onto it. Again, thank you.

---

### Post by Leppie on 2010-02-02
is the drive supposed to do something else by itself other than "just being a drive"?

have you tried connecting it to your ubuntu box?

---

### Post by Gretl on 2010-02-02
No, I haven't connected the new drive to my Linux box.
All I am trying to find out is how to setup this drive on my Ubuntu laptop. In other words, do I need to use the terminal and enter any commands,worry about partitioning the disk, etc. Or, do I just plug it in the USB drive and start using right out of the box?

---

### Post by ks07 on 2010-02-02
As it's just a USB hard drive, you should be fine just plugging it in and saving your files to it. Seeing as it's made for windows it probably is formatted in ntfs or FAT32, but there's no real need to reformat. I'd just plug it in and see what happens.

EDIT: Just looked up the model, says it comes formatted as FAT so read/write support will be great. Supposedly the drive comes preinstalled with some software (disk diagnostics, google toolbar...), but you should be able to just ignore it (or delete it from the drive).

---

### Post by robert shearer on 2010-02-02
Fat 32 has a 2gb file  limit so if you need to save large files or find the copy operation fails for no reason then you may need to reformat the disc with a different filesystem.

Using ntfs as the filesystem would give the greatest compatibility for Ubuntu and Windows.

You may need to install the ntfs3g package depending on the Ubuntu version you are running.

Search for ntfs in synaptic.

Post if you need more details.

---

### Post by Leppie on 2010-02-02
if you're only storing stuff to this disk from linux, i'd suggest formatting to xfs or ext4.
otherwise in combination with windows, you can just convert to ntfs (doesn't need to be reformatted) using the convert tool in windows.

---

### Post by robert shearer on 2010-02-02
> **Leppie said:**
>  you can just convert to ntfs (doesn't need to be **reformatted**) using the convert tool in windows.

So going from one format (fat32) to another format (ntfs) what is that operation called again ? :)

---

### Post by Leppie on 2010-02-02
> **robert shearer said:**
> So going from one format (fat32) to another format (ntfs) what is that operation called again ? :)
it's called converting:[http://technet.microsoft.com/en-us/library/bb456984.aspx](http://technet.microsoft.com/en-us/library/bb456984.aspx)
it's like converting ext3 to ext4, just that the name is completely different going from fat32 to ntfs.

---

### Post by robert shearer on 2010-02-02
Cool ! Thanks for the link. :D

> This kind of conversion keeps your files intact (unlike formatting a partition).

I think if it was a new drive without any data I would reformat expecting it to be a quicker operation but I see how it would be useful to convert if data had already been written.

---

### Post by Leppie on 2010-02-02
> **robert shearer said:**
> Cool ! Thanks for the link. :D
you're welcome



> **robert shearer said:**
> I think if it was a new drive without any data I would reformat expecting it to be a quicker operation but I see how it would be useful to convert if data had already been written.
i think converting would still be much faster as i believe only the journalling function and a minor upgrade of the partition table are implemented. formatting a 1tb drive to ntfs from scratch can take quite a while.

---

