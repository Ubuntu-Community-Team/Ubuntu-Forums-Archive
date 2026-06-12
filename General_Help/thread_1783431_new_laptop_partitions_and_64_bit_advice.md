---
title: "new laptop partitions and 64 bit advice"
date: 2011-06-15
forum: General Help
---

### Post by EmuAlert on 2011-06-15
I recently got a new laptop and I'm trying to figure out how to divide up its partitions. I was thinking that I would install Ubuntu on a relatively small partition and store all of my files on the NTFS parition, linking them back to Ubuntu.

Is this a bad idea?
What's a comfortable size for an Ubuntu parition?

Also, I've tested 64-bit Ubuntu and it doesn't seem to have any major problems. Though I might upgrade, I only have 4 GB of ram right now. Should I install 64- or 32- bit?

---

### Post by DirtyPC on 2011-06-15
You might aswell get 64 bit, just for the extra 512mb. RAM, if you run the live cd you can choose your partition options there. I generally run ubuntu/windows on a 70/30% size divide. But I only use Windows in extreme cases. It's all preference. 30GB seems average

---

### Post by HunkirDowne on 2011-06-15
> **harrylucas1 said:**
> I generally run ubuntu/windows on a 70/30% size divide. But I only use Windows in extreme cases. It's all preference. 30GB seems average

Assuming you mean 70% for Windows and 30% for Ubuntu, is your 30% all in one partition?  Does this include '/home'?

There are many reasons to partition certain ways and each person has their reasons for doing them different.  But I find it increasingly difficult to partition a Windows PC (without blowing away Windows) such that I can have two Windows partitions (C:\Windows, C:\Program Files; D:\Users; etc.) and I like to have at least three logical partitions for Linux (<swap>; '/' (root); and '/home').  If you haven't already noticed, I greatly prefer to keep my data files away from my operating system files.

I don't know if using the NTFS partition for your home files is a bad idea, although I would highly recommend linking (as suggested) in such a way that the environment files (.bashrc; etc.) and directories (.cache; .config; .local; etc.) on a Linux partition.  But one could create a link as follows to write all the data files to the NTFS partition.

EXAMPLE ONLY:
```
ln -s /mnt/sda2/Users/hunkirdowne/Documents
```

Permissions in NTFS do not jive with the permissions in, say, ext3 and I am much more familiar with the latter.  Other than that caveat, ntfs-3g is mature enough by now to trust a write from Linux and not mess up Windows.  

I have only had one instance recently where I had to run a checkdisk in Windows before it would boot.  This may/may not have been related to immediately previous file movements in a Linux session, but I suspect that if it wasn't a glitch in the disk writing, it was something I did or didn't do correctly.  Bottom line, I have nothing against NTFS other than I am not as familiar with it.  It is a robust file system, in my experience.

---

### Post by DirtyPC on 2011-06-15
70% Ubuntu. :)

---

### Post by HunkirDowne on 2011-06-15
> **harrylucas1 said:**
> 70% Ubuntu. :)

So 30 GB for Windows then, or do you have an incredibly small HDD?  (I have two old laptops, Linux only, with 20GB and 30GB HDDs.)

---

### Post by DirtyPC on 2011-06-15
% is not GB's............
Just a ratio

---

### Post by DirtyPC on 2011-06-15
What I meant was 30GB's would be a good partition size for him to start off on. If you ever want to increase you could always use LVPM

---

### Post by EmuAlert on 2011-06-15
Can NTFS handle all the hidden files and soft links required in all of the dotfiles in my home directory? I could individually link ~/Pictures, ~/Videos, etc., but it'd rather link /home/emualert to C:\Users\EmuAlert. Thanks a bunch for the info so far.

---

### Post by HunkirDowne on 2011-06-15
> **EmuAlert said:**
> Can NTFS handle all the hidden files and soft links required in all of the dotfiles in my home directory? I could individually link ~/Pictures, ~/Videos, etc., but it'd rather link /home/emualert to C:\Users\EmuAlert. Thanks a bunch for the info so far.

Yes and no.  The "dot" files (environment files in my above post) will live on the NTFS partition, but they will not be hidden in Windows and they could easily be trashed.  What I would do is to do a single- or dual-partition Ubuntu installation where all of '/' is on one partition.  Even if you were to put '/home' on a separate partition, there would still be a skeletal '/home' on the root partition.

So let '/home' stay on the root partition, but individually link ~/Pictures, ~/Videos, etc.  Linking /home/emualert to C:\Users\EmuAlert, while technically feasible, will only work if nothing goes wrong (ha! I laugh at my logic!).  Seriously, if one of your environment files get's compromised you might spend hours or days trying to get back to normal.

---

### Post by btindie on 2011-06-15
Earlier on I was looking to see if it would be better to install a 32bit or 64bit version  and came across [this]("http://www.linuxtoday.com/infrastructure/2009123101735RVHWSW") article which is quite conclusive. You can install the 32bit PAE kernel to get access to upto 64GB of RAM but going from the above article you'll also get quite a considerable performance boost from using a 64bit system.

As for how you split your disk, it depends on what your requirements are - what you want to do with Windows and the same for Ubuntu. Though I would **not** store system files on an NTFS partition as it does not support all the required acl's and it's sure to just cause problems. It's fine for storing downloads, music, videos, etc... 

I think with the Wubi install it installs it into a large file within an NTFS partition which should do if you haven't made your mind up though it does have a performance hit.

Without a SWAP partition, you could easily do an Ubuntu install in a 5GB partition but it would leave you with a limited amount of storage space.

---

### Post by Dngrsone on 2011-06-15
Currently, I have a 320GB hard drive with Vista and 10.04 dual-boot.

The Vista partition was cloned from a 170GB drive and then reduced down to 84GB and then a 43GB NTFS data partition (holding my music and other files to use between the two OSs).

I have a small /boot partition, a 21GB / (root) partition and a 32GB /home partition.

As I said, my music and such will be stored on the NTFS data partition so it can be accessed by both Vista and Ubuntu.

I made an 8.6GB /swap partition at the end of the drive (I have 8GB RAM, but that should be enough swap) and that leaves me with 130GB unallocated for more operating systems as required (11.04, when it becomes more usable, for instance) or more media storage, if necessary.

I have used similar numbers in the past with no real problems, as long as I don't start storing a bunch of movies or .iso images in my /home directory.

---

