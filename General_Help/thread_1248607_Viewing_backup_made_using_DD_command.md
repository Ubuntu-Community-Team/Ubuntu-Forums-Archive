---
title: "Viewing backup made using DD command"
date: 2009-08-24
forum: General Help
---

### Post by ZenMasta on 2009-08-24
I used a live cd yesterday to backup a windows hard drive prior to reformatting.  I used this command dd if=/dev/hdx | gzip > /path/to/image.gz

I've used DD to clone disks before never to make a backup file. Well I forgot some files and I need to explore the backup to get them. Problem is I don't know how.

When I open the .gz file all I see is another file called backup and it does not have a file extension.

How can I explore the backup file so I can retrieve some files I need?

---

### Post by dandnsmith on 2009-08-24
I think you need to restore the backup to a partition (by reversing the dd|gzip process). This will get you a mountable partition which you can handle normally. I'm sure other techniques could be utilised (eg creating an iso file, and mounting that) but this is the 'quickest'.

---

### Post by ZenMasta on 2009-08-24
> **dandnsmith said:**
> I'm sure other techniques could be utilised (eg creating an iso file, and mounting that) but this is the 'quickest'.

Well, ISO sounds appealing since I can easily read that in windows. How would I convert the file that was created into .iso?

---

### Post by dandnsmith on 2009-08-25
Having had a little time, I realise that I just threw out the idea ...

Now, I think you'd probably have to recreate the partition anyway, and then get to the iso from that. The problem is that the *dd* command results don't get you any easy handle on the files, as what you get is the copy of the partition content, regarded as a bit-stream.

What I cannot think is what subconscious train of ideas brought up the iso anyway (except that it would have been easier to handle for your purposes)

---

### Post by miklcct on 2009-08-25
You need to gunzip the .gz and mount it in a directory

---

### Post by dandnsmith on 2009-08-25
Of course - that one eluded me.

---

### Post by ZenMasta on 2009-08-25
How do I mount the file? keep in mind the backup was of an NTFS hard drive.

---

### Post by dandnsmith on 2009-08-26
try *mount -loop*, and check the mount man pages

---

### Post by sevenflo on 2009-09-21
It'll go something along these lines:
[FONT=monospace]mount -o loop -t ntfs **sda1.img** /mnt/**sda1-image**[/FONT]

You will need to change the bold to match your file and mount point.

sda1.img will be your image (for those who don't know)
sda1-image will be an EMPTY folder in your /mnt folder that you might need to create. This will be the address you use to access the file.

-o loop allows the image to be mounted as the image is not a block device, the loopback will allow mounting the image.

---

