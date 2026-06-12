---
title: "Help on mounting a spare HDD from another ubuntu install"
date: 2010-04-26
forum: General Help
---

### Post by hcaleman on 2010-04-26
I previously had a system running 8.04 for a few years utilizing a 320GB drive as root and a 100GB drive as a spare XP install (never used it).  It recently started acting up so I pulled out the 320gb drive and did a clean install of hardy on the 100gb drive (full format, no more XP) and upgraded to 10.04 RC.  

My new drive setup is as follows: 
100gb SATA drive (now sda1) ext3, LVM with a swap, root and home volume.  Working fine now after some initial setup issues.  

Old drive setup that I want to mount and browse: 
320gb SATA drive, also ext3 with LVM.  But only a swap and root volume. I knew nothing of what I was doing when I partitioned that drive as it was my first linux foray.  

What I am mainly concerned with is getting my music, documents, etc. off my 320gb drive's home folder (which is under the root volume).  

Ultimately I would like to re-connect the 320gb drive and wipe out what I don't want (the old install basically) only preserving the media, then somehow merge that LVM volume into my new existing /home volume.  Effectively making my current home volume go from 76GB up to 396gb (or whatever I decide) whilst preserving the data on the old drive I want.

Any pointers on where I can start, I did some searching and poked around for utilities a bit but am still lost.

---

### Post by TitanusEramius on 2010-04-26
Well, I guess there is many ways to do what you want, one of them being this:
Connect the drive
Mount the drive
Browse, delete and rearrange the content of the drive
Make a entry in fstab so Ubuntu mounts the drive on boot
And then you can make links to the folder on that drive and place them on the desktop for easy access.

Since I don't know how well you can use the terminal, here are some of the commands you would use to do this:
After you have the drive in the computer and Ubuntu is running you can type "sudo blkid" to get a list of the drives connected to the computer. An example would be
/dev/sdd1: UUID="4cc71ab2-7d34-42da-b9cd-935956793d06" TYPE="ext4"
/dev/**** is what you need to find for now. Later when working with fstab you will need the UUID, but you just run the blkid-command again.
Then make a folder in /media called "data" with "sudo mkdir /media/data" and write "sudo mount /dev/**** /media/data" to mount the disk in the folder /media/data. This is just examples, you can change the name and place of the folder as you please.

The part about fstab is very good explained in details here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
In the end you should end up with a line like this:
UUID=4cc71ab2-7d34-42da-b9cd-935956793d06 /media/data ext3 defaults 0 1
Where UUID and mountpoint will be different and you have to be sure what filesystem the disk is using, and write it where I have ext3.

There is also a good guide to mount:
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

Good luck and if you get stuck, just post :P

---

### Post by hcaleman on 2010-04-26
Thanks I'll start with what you suggested when I get home.  

I'm fairly comfortable with terminal once I figure out what commands I need to run and I browse through the man pages a bit.

---

### Post by hcaleman on 2010-04-27
Great, you got me started off in the right direction.  

Once I mounted and did some rearranging I used a few different guides on LVM to resize my filesystem in the existing volumes, shrink and then created some new volumes with the new space to segregate the data I wanted over several partitions.

This provided helpful in that process: [http://blog.shadypixel.com/how-to-shrink-an-lvm-volume-safely/](http://blog.shadypixel.com/how-to-shrink-an-lvm-volume-safely/)

---

### Post by TitanusEramius on 2010-04-27
Happy to help :P
And thanks for link about resizing, every day you learn is a good day.

---

