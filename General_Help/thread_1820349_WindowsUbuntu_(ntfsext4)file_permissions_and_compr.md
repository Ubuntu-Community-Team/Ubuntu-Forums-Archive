---
title: "Windows/Ubuntu (ntfs/ext4)file permissions and compression"
date: 2011-08-07
forum: General Help
---

### Post by Moyamo on 2011-08-07
Hello

First, I would like you all to understand that I **_know_** that you cannot preserve the file permissions from ntfs to ext4.

My problem is that I duel boot windows 7 and ubuntu and would like to have my personal files accessible from each OS yet I would not like the data to be duplicated. I already have 4 copies of the data that I will have on my laptop and do not need/want a 5th copy.

I tried keeping all my files on the windows partition and then mounting it in ubuntu. I then symlinked certain directories in my home directories to the directories holding my personal files on the windows partition (e.g. My Documents, My Videos etc.). This didn't work to well as the file permissions were unchangeable.

I then googled around a bit and found that tarballs preserve file permissions. So now I come to my question:"How do I efficiently use tarballs to store my personal files and have them easily accessible from windows and ubuntu?"

I thought about compressing my files in the window partition into  a tarball when logging off and then mounting the tarball in ubuntu. Then I found out that you can't mount tarballs.

Any help would be appreciated.

Thanks in advanced.

---

### Post by daccount10 on 2011-08-07
You could try sharing a ntfs or fat32 partition.

---

### Post by Moyamo on 2011-08-16
Sorry for the late reply and thank you for the reply.

That would not solve my problem as I still would have permission errors.

---

### Post by Morbius1 on 2011-08-16
I'm confused by the "permissions errors" you are getting. Are you trying to set permissions an on individual file within say "My Documents"?

---

### Post by Moyamo on 2011-08-17
It's not really errors. It's just that I can't change the permissions. 

For example let's say I symlinked /home/username/music to /mnt/windows/Documents\ and\ settings/username/music and then run

```
$ sudo chown user:group /home/user/Music/Hindi/Munni\ Badnaam\(DjMates.CoM\).mp3 
[sudo] password for user:
$ ls -l  /home/user/Music/Hindi/Munni\ Badnaam\(DjMates.CoM\).mp3 
-rwxrwxrwx 1 root root 9962882 2011-07-04 09:59 Music/Hindi/Munni Badnaam(DjMates.CoM).mp3

```

I mounted the windows partition with the nouser flag enabled. (I don't want any old user to mess with my windows partition:-))

---

### Post by Morbius1 on 2011-08-17
Here's the problem with any type of Windows filesystem:

You can't change the Linux file permissions on individual files / folders because there are no Linux permissions bits on a Windows filesystem.

What you can do however is create a mask at mount time that makes the filesystem appear to have permissions bits to Linux but it will apply to all child folders and files.

In your particular case it's true that it mounts with user = group = root but with permissions of 777 allowing read/write access to everyone so I don't see this as a problem unless you want more restrictive permissions.

If you want to mount it so that you have a particular user and group that can be done but it will apply to every single file and folder in that partition. [COLOR=Blue]EDIT: Didn't see the last line of your post.[/COLOR] If you post the output of your fstab I can help with that:
```
 cat /etc/fstab
```

---

### Post by Moyamo on 2011-08-17
Is the no way to mask a specific directory?

---

### Post by Morbius1 on 2011-08-17
Nope

---

### Post by Moyamo on 2011-08-17
thanks for your help. I try your solution when I have time

---

### Post by Morbius1 on 2011-08-17
> **Morbius1 said:**
> Nope
That statement may not be entirely accurate. There is something called bindfs which I keep forgetting about because I don't use it any more and when I did use it it was only with Linux fileystems.

I don't know if it even works with NTFS but if anyone does know it would be the author of this HowTo: [http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by WorMzy on 2011-08-17
> **Morbius1 said:**
> I don't know if it even works with NTFS but if anyone does know it would be the author of this HowTo: [http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

I've just tested it, and it works fine. Thanks for posting it, I'll certainly find it useful.

---

### Post by Moyamo on 2011-08-21
Thank you! That's perfect! Exactly what I wanted. It does seem to work with ntfs.

---

