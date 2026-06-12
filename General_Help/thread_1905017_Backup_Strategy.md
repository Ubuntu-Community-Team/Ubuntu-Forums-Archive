---
title: "Backup Strategy"
date: 2012-01-05
forum: General Help
---

### Post by creiss on 2012-01-05
Hey folks,

I am running several Notebooks with Ubuntu 11.10. All Notebooks are 

sda1 /boot ext4
sda2 crypt (/, ext4)
sda3 crypt (swap, one-time-key)

Also, the user homes are additionally encrypted.

Now i am looking for a Backup solution that does allow disaster recovery, ie, the backup should contain the full system that can be restored without serious intervention. (Besides creating the partition layout, cryptSetup and editing fstab/ initramfs/ grub).

CloneZilla is neat, but its eating 1:1 of disk space, a premium I can't afford. Also, single file restoring is a pain, too.

To make things worse, the fileserver is NTFS, so rsync is out of the question. 

Any help / ideas would be greatly appreciated.
(How do you guys back up your encrypted systems?)

-Chris.

---

### Post by rsvancara on 2012-01-05
Bacula is an agent based backup solution. I have great luck with it restoring systems.  It can do bare metal recovery if you set it up correctly.  However, with encrypted file systems, you have the have the file system mounted.

---

### Post by jjex22 on 2012-01-05
Hi there, 

Not sure if it's what your looking for exsactly, but I use dd and 7za (7-zip) to image and backup my hard drive - this saves the drive exactly as it is - mbr, partition etc bit for bit?

It takes quite a while obviously, so I do it on a sunday  - I used to  use an ubuntu live cd, but I've lately been using a puppy install on my  hdd - just boot it up, make sure to unmount all partitions, I tend to  swapoff  also, mount the back up drive at /backup (I created this to  recuce errors then I use

```

dd if=/dev/sda conv=sync,noerror bs=64K | tar cf /backup/newhddimage.img | 7za a -si /backup/newhddimage.img.tar.7z

```I should point out that this method does require the 7za package to create the ultra small 7zip file - this isn't installed by default on most llinux distros, so if you want maximum ease of restoring your drive, use bzip2 the compression ratio is almost as good and it is supported out of the box by all linux distos. to do this you'd obviously get rid of the zda command and change the tar command to 

```

tar cjf /backup/newhddimage.img.tar.bz2

```Just to break down the command I've given you -> 

dd - copys the drive /dev/sda block by block - the conv=sync,noerror is just incase there's any errors on your drive. bs is the block size, I've seen this also set as low as 1K, but the tutorial I originaly used advised 64k to speed up the process (it's the bit I'm not certain of so I left alone!)

| - this symbol means take the output of that action and do this

tar - whatever compresion format you use, when backing up your hard drive it's really important to use tar as it stores the owner/group info.

7za - as I say this creats the z-zip compresson and you may not want this.


I also tend to keep a hard drive copy on online storage, and whilst I can easily store the image on adrive, I get stuck for maximum file sizes, so I then split the outputted file with the split command once a month. 

for example

```

split --bytes600M -d newhddimage.img.tar.bz2 newharddriveimage

```This splits the already compressed image up into little 600Mb parts that are easy to upload and dont hit Adrives 2gb upload limit, and can be burned to cd. I could set the size for the parts as 2GB with "--bytes2G"

Was this the kind of info you meant? I hope it helps, One very important disclaimer - I'm currently on a Windows machine and have rewritten these commands from memory with the help of man pages online - DO NOT stick them into your terminal - be sure to understand them by reading the man pages for DD and TAR atleast before you use them. 
Never use a command you don't understand :)

---

### Post by Habitual on 2012-01-06
> **rsvancara said:**
> It can do bare metal recovery if you set it up correctly...

I'd be interested in such a configuration please.

---

### Post by creiss on 2012-01-07
I am using CloneZilla for Barebone recovery.
But I also stumbled uppon this idea, which works (tried to restore my notebook in a VM):

on the notebook
1. Saved the dpkg-config of my notebook.
2. Did a tar of my ~ (user) and etc.

in the vm (recovery, replace with notebook in real case)
3. Install from Ubuntu Alternate cd, do encrypted stuff, normal install etc.
4. reimport the saved config from above: this installs all missing packages and removes all who were not present on the notebook. This syncs all the stuff I need.
5. Unpack the tarfile from your home.
6. Unpack selectively the etc tar (hosts & co)

This nets a running config of my system. Problem solved, case closed. Net usage: Only the data for ~ and the config file.

Thanks all for your ideas!

---

### Post by irw on 2012-01-29
> **jjex22 said:**
> ```

dd if=/dev/sda conv=sync,noerror bs=64K | tar cf /backup/newhddimage.img | 7za a -si /backup/newhddimage.img.tar.7z

```

jjex22, why do you use the tar command? would this not work as well:
```

dd if=/dev/sda conv=sync,noerror bs=64K | 7za a -si /backup/newhddimage.img.tar.7z

```

I found [this tutorial]("http://mark.koli.ch/2009/05/howto-whole-disk-backups-with-dd-gzip-and-p7zip.html") helpful, but wonder if there is any extra benefit using tar?

I have also recently discovered the 7za option -mx9 gives more ("ultra") compression than the default.

Ian.

edit: I've partially found the answer to my question [here]("http://pwet.fr/man/linux/commandes/7z"):
> DO NOT USE the 7-zip format for backup purpose on Linux/Unix because : - 7-zip does not store the owner/group of the file.

On Linux/Unix, in order to backup directories you must use tar : - to backup a directory : tar cf - directory | 7za a -si directory.tar.7z - to restore your backup : 7za x -so directory.tar.7z | tar xf - 

However, this is not necessary for disk partitions, is it?

---

