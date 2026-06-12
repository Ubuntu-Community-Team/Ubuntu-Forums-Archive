---
title: "How to access locked directory"
date: 2011-07-27
forum: General Help
---

### Post by Blancpain on 2011-07-27
Hello,
 
I have a small problem with my Acer netbook (ao521) on which I dual boot windows7/ubuntu. I am new to linux and I didn't know much about dual booting so I made some errors when pratitioning and installing ubuntu (originally I had windows 7 only) but that is another issue. 
 
The problem is that I accidently wiped the /C partition of win7 thereby deleting windows (:D). I had made a backup since I knew something like this could happen and I saved it in /home so now it is in /home/backup. Here it gets interesting though..I tried recovering Windows (with the built-in Acer eRecovery) and apparently this messed up Grub so I couldn't boot ubuntu..Now, I don't have a problem installing windows from scratch and then installing ubuntu afterwards (I have learned my lesson and I think I would do it right this time), but there is one folder, which contains some valuable documents and I want to access it and save the documents on a USB drive.
 
So, I ran ubuntu from the live cd(usb) and I mouned the /home partition (of my previous installation) and I tried accessing the backup folder that I made earlier but it said that I do not have such permission. I did some searching arround and I found out that I should mount the partition as root and copy the contents of the folder from the terminal. So far so good, but when I wrote ```
sudo mount /dev/sda9
``` it said that no such mounting point is available in /etc/fstab.
 
It occured to me that I could use the data in the initial /etc/fstab (from the initial ubuntu installation) and insert what I need in the current fstab. I did that but when I write /home as mounting point it apparently confuses it with the current /home so that doesn't help.
 
Well my question is: how can I edit fstab so I would be able to mount the partition and use it or is there any other way to access the folder in question. Thank you in advance!

---

### Post by westie457 on 2011-07-27
> **Blancpain said:**
> Hello,
 
I have a small problem with my Acer netbook (ao521) on which I dual boot windows7/ubuntu. I am new to linux and I didn't know much about dual booting so I made some errors when pratitioning and installing ubuntu (originally I had windows 7 only) but that is another issue. 
 
The problem is that I accidently wiped the /C partition of win7 thereby deleting windows (:D). I had made a backup since I knew something like this could happen and I saved it in /home so now it is in /home/backup. Here it gets interesting though..I tried recovering Windows (with the built-in Acer eRecovery) and apparently this messed up Grub so I couldn't boot ubuntu..Now, I don't have a problem installing windows from scratch and then installing ubuntu afterwards (I have learned my lesson and I think I would do it right this time), but there is one folder, which contains some valuable documents and I want to access it and save the documents on a USB drive.
 
So, I ran ubuntu from the live cd(usb) and I mouned the /home partition (of my previous installation) and I tried accessing the backup folder that I made earlier but it said that I do not have such permission. I did some searching arround and I found out that I should mount the partition as root and copy the contents of the folder from the terminal. So far so good, but when I wrote ```
sudo mount /dev/sda9
``` it said that no such mounting point is available in /etc/fstab.
 
It occured to me that I could use the data in the initial /etc/fstab (from the initial ubuntu installation) and insert what I need in the current fstab. I did that but when I write /home as mounting point it apparently confuses it with the current /home so that doesn't help.
 
Well my question is: how can I edit fstab so I would be able to mount the partition and use it or is there any other way to access the folder in question. Thank you in advance!


Hello, just a little confused at the moment so some questions to answer first. Do you have Windows installed already and does it boot up okay?

---

### Post by nothingspecial on 2011-07-27
[COLOR="Red"]EDIT See my next post first. I'm not sure which you need but I think it's the next one.[/COLOR]


You don't need to edit fstab, you just need to specify a mount point and a file system (which should be ext4)
```

sudo mkdir /media/backup
sudo mount -t ext4 /dev/sda9 /media/backup
```

---

### Post by nothingspecial on 2011-07-27
Actually, rereading, you say it is already mounted.

Open a terminal and type ```
gksudo nautilus
``` and you should be able to copy your stuff.

I'll leave my first reply because I'm still not sure what you are trying to do.

---

### Post by Blancpain on 2011-07-27
@westie457 - I used the recovery tool but /C was already wiped so yes I can boot windows but my data is gone.
 
@nothingspecial - Thanks, I am not at home at the moment but I would try this later. I just have a stupid question about the syntax - why is the mkdir part necesarry (why create a /media/backup directory)?

---

### Post by nothingspecial on 2011-07-27
Because you need an empty directory to mount it to. Everything in linux is a file and must have a place in the file system.

It needs an empty directory to be mounted in. You can mount it in /mnt/bananas if you want to but you have to assign it a place.

---

### Post by Blancpain on 2011-07-27
@nothingspecial - I tried this (gksudo nautilus) yesterday and I couldn't locate the /home directory from the installation, just the /home from the live cd(usb).
 
 
Edit: I understand, you are right, however, that I can mount it(not from the terminal) but can't access the folder.

---

### Post by nothingspecial on 2011-07-27
The mounted ubuntu partition should appear on your desktop and the sidebar of your file browser.

From there go /home/username/ and you should see your folders.

---

### Post by Blancpain on 2011-07-27
Thanks 'nothingspecial' mounting the partition and then using gksudo nautilus worked and I can access the folder now :)

---

