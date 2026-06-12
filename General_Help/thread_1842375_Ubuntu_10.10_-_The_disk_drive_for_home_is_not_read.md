---
title: "Ubuntu 10.10 - The disk drive for /home is not ready yet or not present"
date: 2011-09-11
forum: General Help
---

### Post by A4orce84 on 2011-09-11
Hey Guys,

Been enjoying my Ubuntu 10.10 setup on my desktop for a few months (had to reformat it since it started acting up, and don't like 11.04 that much so reverted back) but recently have a problem.

Turning on my computer I was greeted with the following message:

"The disk drive for /home is not ready yet or not present"

I tried a few things and did my homework:

#1. [http://ubuntuforums.org/showthread.php?t=1466555&page=3](http://ubuntuforums.org/showthread.php?t=1466555&page=3)

#2. [http://neophyteman.wordpress.com/2010/06/06/ubuntu-10-04-boot-or-devsda-startup-mount-problem/](http://neophyteman.wordpress.com/2010/06/06/ubuntu-10-04-boot-or-devsda-startup-mount-problem/)

I know from reading, the error means that it's basically having trouble finding my /home mount, and I'm not sure how to correct this. Everything I've tried has failed so far.

Anyone have any ideas / tips on how to beat this please? Thanks!


--Asif

---

### Post by A4orce84 on 2011-09-11
Ttt

---

### Post by TeoBigusGeekus on 2011-09-11
Lets try this from the beginning.
Can you post us the contents of your fstab file?
```
nano /etc/fstab
```
Also, can you post us the output of
```
sudo blkid
```
and 
```
sudo fdisk -l
```
?

---

### Post by A4orce84 on 2011-09-11
I believe dev/sdb7 is the mount for the /home directory.

```
nano /etc/fstab
```
[IMG]http://img.photobucket.com/albums/v405/A4orce84/8272946f.jpg[/IMG]

```
sudo blkid
```
```
sudo fdisk -l
```

[IMG]http://img.photobucket.com/albums/v405/A4orce84/bd06e5aa.jpg[/IMG]


Let me know if you need anything else! Thanks! =)

---

### Post by TeoBigusGeekus on 2011-09-11
There's the mistake:
The output of the blkid command, shows that the UUID of sdb7 is 3e1bd...etc.
But in your fstab file, the UUID of your home partition is reported as 6a6c30...etc.
Ctrl+x to close your fstab file and
```
gksu gedit /etc/fstab
```
to open it with writing priviledges.
Copy the 3e... value and replace the 6a6c30... one.
Save, exit and give
```
sudo mount -a
```
so that your system mounts all your partitions mentioned in fstab.

PS: You didn't have to take photos man; you've killed me :D
You could just copy and paste the output of the commands to your post.

---

### Post by A4orce84 on 2011-09-11
Sorry for the pics man, the desktop (the one that is having issues) doesn't boot fully. So I can't do a direct copy and paste from it. I'm making this post from my laptop! =)

I don't think the change worked! I made the changes and I get some weird errors like, "Could not update ICEauthority file /home/asif/.ICEauthority" and "Could not create the following required folders: /home/asif/Desktop, home/asif/.nautilus."

Sorry for the picture, here is the updated fstab file:

As you can see I added the new line and commented out the old one:
[IMG]http://img.photobucket.com/albums/v405/A4orce84/9b8ce236.jpg[/IMG]

---

### Post by TeoBigusGeekus on 2011-09-11
Try these
```
sudo chown asif:asif /home/asif/.ICEauthority 
sudo chmod 600 /home/asif/.ICEauthority
```
and then reboot.

---

### Post by A4orce84 on 2011-09-11
Get an error, don't think it's able to find it:

"chown: cannot access `/home/asif/.ICEauthority`: No such file or directory"

---

### Post by TeoBigusGeekus on 2011-09-11
Yes, of course, it's not mounted yet.
Try changing the ownership of the whole home partition
```
sudo chown -R asif:asif /home/asif
```

---

### Post by A4orce84 on 2011-09-11
"chown: cannot access `/home/asif': No such file or directory"

---

### Post by TeoBigusGeekus on 2011-09-11
Ok...
Let's try to mount it
```
sudo mkdir /home/asif
sudo mount /dev/sdb7 /home/asif/
```

---

### Post by A4orce84 on 2011-09-11
Success! I was able to boot back into my system successfully, but have a new / fresh home folder. So lost some of my settings and files! Boo! =(

Oh well, I guess that's the price to pay to have everything working again right?

Thanks for your help TeoBigusGeekus! =)


--Asif

---

### Post by TeoBigusGeekus on 2011-09-11
You're welcome and don't forget to mark the thread as solved, but...

...why would ubuntu delete everything from your home partition?
Does anyone have any idea?

---

### Post by A4orce84 on 2011-09-11
Didn't we just create a new directory and mount it?

---

### Post by TeoBigusGeekus on 2011-09-11
Yes, but you said that you've rebooted.
Your fstab file should instruct the system to mount /dev/sdb7 as your home partition, thus giving you your old home folder back.
All we did was create a mount point for your home partition and make you the owner.

---

### Post by A4orce84 on 2011-09-11
Is there a way to see if my old home folder exists?

---

### Post by TeoBigusGeekus on 2011-09-11
Post the output of
```
df -h
```

---

### Post by A4orce84 on 2011-09-11
```
df -h
```[/QUOTE]


asif@asif-dt:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6              14G  4.5G  8.6G  35% /
none                  2.0G  276K  2.0G   1% /dev
none                  2.0G  588K  2.0G   1% /dev/shm
none                  2.0G   92K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/dev/sdb7             104G  467M   99G   1% /home
asif@asif-dt:~$

---

### Post by TeoBigusGeekus on 2011-09-11
Yes, sdb7 is mounted as your home folder, but where did all the data go?
Have you done anything to your hard drives lately? (Suspicion might as well arise from the change of the UUID value)

---

### Post by A4orce84 on 2011-09-11
I copied a lot of data to it recently, but besides that no.

---

### Post by TeoBigusGeekus on 2011-09-11
> **A4orce84 said:**
> I copied a lot of data to it recently, but besides that no.

I don't know what to say.
df reports only 467mb of data in that partition, so I guess the rest is unfortunately lost.
I'd be very cautious in the future putting data in that hard drive...

---

