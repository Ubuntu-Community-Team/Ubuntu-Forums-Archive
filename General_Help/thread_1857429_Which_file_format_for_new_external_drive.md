---
title: "Which file format for new external drive?"
date: 2011-10-10
forum: General Help
---

### Post by veroslav on 2011-10-10
Hi,

I bought a 2 TB external drive in order to make a backup of my data. Originally, it was formatted as NTFS, but I have read quite a few stories about such drives being corrupted sooner or later which required repairing it from within Windows.

I was thinking about formatting the drive to either FAT or EXT3/EXT4, however, FAT can't support files larger than 4 GB and I do have a few of such files that I need to backup.

So the choice felt on EXT3/EXT4, which is fine because I am not intending to share files with Windows.

Yesterday I formatted the drive to EXT3/EXT4 (right clicked on it from the Desktop and choose to format it).

However, when the formatting was done, I saw that ca 90 GB of the free space was unusable for some reason. There was a new empty folder called lost+found or similar, on the disk, which I couldn't open because it was forbidden for me to open it.

Question 1: Which format is common to choose for external drives and what are the advantages/disadvantages of each?

Question 2: How can I reclaim 90 GB of the space after formatting to EXT3/EXT4? What is the lost+found folder for?

Thank you in advance!

Kind Regards,
Veroslav

---

### Post by collisionystm on 2011-10-10
Did you choose EXT3 or EXT4

---

### Post by veroslav on 2011-10-10
Thank you for your fast reply.

I believe I chose EXT4, but after the formatting was done, I checked the properties of the external drive, and it showed the file system as EXT3/EXT4.

If I remember correctly, I was only given choice of EXT3/EXT4 before formatting, no separate choices for each.

My choice would most definately have been EXT4 because I always select it instead of EXT3.

Thanks.

/Veroslav

---

### Post by collisionystm on 2011-10-10
Did you format it with Gparted?

Give it a try again.. see if it lets you delete that 90gb and merge it with your main partition

---

### Post by WasMeHere on 2011-10-10
How did you format it?

- which tool? I would recommend *Gparted*, available when you run a live session from your installation disk or stick.

- which of ext3/4? I would recommend *ext3* on a backup disk, while I prefer ext4 on the system partition.

lost+found can be viewed as root (superuser) with

```
sudo ls -l
```

Have fun
Olle

---

### Post by veroslav on 2011-10-10
No I didn't, I did it directly from the desktop after it was mounted (right-click -> Format...), I will give it a go with gParted when I come home again. Thank you for the tip.

I don't have any data on it at the moment so I can reformat at any time.

What kind of file format would you recommend, what do you use, what is most common? How common is it for a NTFS formatted drive to become corrupted? I would prefer to be able to avoid such situations, as I no longer have a running copy of Windows.

Thanks.

/Veroslav

---

### Post by veroslav on 2011-10-10
Thank you for your reply, Olle Wiklund.

I will give gParted a try when I am at home. Do you mind sharing any particular reason as to why you prefer ext3 to ext4? Just curious :)

Thanks!

---

### Post by veroslav on 2011-10-10
And just one more (total noob) question: If I format the drive to any of the file systems that support access rights (ext3/ext4), will I be able to modify the files on the drive (move, copy and delete them) when I use the external drive on another system, where the user that created these files (myself) is not present?

/Veroslav

---

### Post by WasMeHere on 2011-10-10
> **veroslav said:**
> Thank you for your reply, Olle Wiklund.

I will give gParted a try when I am at home. Do you mind sharing any particular reason as to why you prefer ext3 to ext4? Just curious :)

Thanks!
*ext3* is old and very reliable, and the access is faster from linux than *ntfs*. Furthermore making backups, you can handle file access (ownership and read/write/execute which is good if/when you have to restore it. *ext4* is faster but not quite as reliable, because it is more sensitive to power-down events.

So as long as you do not intend to exchange data with Windows, *ext3* is my choice.

And yes, you can modify the access to your files. If you are another user (on another linux computer) you can always do it with root (superuser) privileges:
```
sudo chown
sudo chmod

```

---

### Post by veroslav on 2011-10-10
Great!

That is all I wanted to know, I will go with the ext3 format, I would like to thank you all for your fast help and suggestions!

Thanks!

Kind Regards,
Veroslav

---

### Post by viperdvman on 2011-10-10
Anything we can do to help.

Like they said, it depends on if you intend for your external hard drive to be read by Windows as well as Ubuntu. If so, then I'd go with NTFS. FAT, if I remember right, is supposed to be limited to 2TB, but more often isn't found on anything bigger than 32GB (which is why SD cards larger than 32GB are being formatted in exFAT). And exFAT isn't recognized by Linux... yet.

If you're just gonna have Linux read and write to it, then I'd go ahead and format it to ext3/ext4.

Good luck :)

---

