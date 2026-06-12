---
title: "I got the sshfs blues"
date: 2010-10-17
forum: General Help
---

### Post by jquis8411 on 2010-10-17
I'm trying to set up sshfs on a desktop/fileserver so that I can mount its HDD's I use for storage on my laptops. My issue seems to be getting permission to write to the mounted drives. I just keep getting permission denied. here is what I think are some relevant tidbits.
mount point on server,
```
 joe@joe-desktop:~$ ls -ld ~/sda2
drwxr-xr-x 2 root root 16384 1969-12-31 19:00 /home/joe/sda2

```
HDD I'm trying to mount
```
joe@joe-desktop:~$ ls -ld /dev/sda2
brwxrwxrwx 1 joe disk 8, 2 2010-10-17 15:22 /dev/sda2
 
```
mount point on client
```
 joe@joe-laptop:~$ ls -ld ~/sda2
drwxrwxrwx 2 joe joe 4096 2010-10-17 19:58 /home/joe/sda2

```
This is the command I'm trying to use to mount
```
 sshfs joe@192.168.1.103:/home/joe/sda2 ~/sda2 
```
I can chmod the mount on the server to 777 but as soon as I mount the HDD to the server all write permission just goes *poof* and its back to "drwxr-xr-x".Chown seems to offer me no help either, it just wont stick. I hope there is help for this frustrated guy. TY

---

### Post by 3Miro on 2010-10-17
My guess is that this is your problem:
```
joe@joe-desktop:~$ ls -ld ~/sda2
drwxr-xr-x 2 root root 16384 1969-12-31 19:00 /home/joe/sda2

```

/home/joe/sda2 is in the userspace of joe, therefore it should be owned by joe. Try:
```
 sudo chown joe:joe /home/joe/sda2 
```
and then mount the drive.

Basically, shfs should let you do anything that sftp would. If you can
```
 cd /some/folder/at/home
sftp <someone>@<server> 
cd /some/folder/at/server
get/put some.file

```
then 
```

sshfs <someone>@<server>:/some/folder/at/server /some/folder/at/home

```
and copy/paste files should do the exact same thing.

---

### Post by jquis8411 on 2010-10-17
I tried to use chown like you said and I get joe@joe-desktop:~$ sudo chown joe:joe /home/joe/sda2
[sudo] password for joe: 
chown: changing ownership of `/home/joe/sda2': Operation not permitted

---

### Post by jquis8411 on 2010-10-17
sorry didnt mean to sound mean in the reply, I was on the phone at the same time and could barely type:)

---

### Post by 3Miro on 2010-10-17
This makes no sense, a "sudo" command to see permissions denied, did you type the password correctly. Did you adjust for the right names (I don't know if /home/joe/sda2 is the real folder)? Everything in joe's home folder should be owned by "joe:joe" use 
```
 ls -al /home/joe 
```
to double-check (you probably don't want to post the content on-line).

Where you connected to the server when you did the command. You have to do this before you connect with sshfs. Unmount (or to be 100% sure, reboot) and then try the "chown" command again. (also make sure you don't have sudo before sshfs like you have in the example)

---

### Post by jquis8411 on 2010-10-17
OK, chown worked and ls -al gave a list of home with me owning everything. I tryed remounting and same problem. it mounts fine in the host but I cant write to it (permission denied). so I restarted and have /dev/sda2 is unmounted and has full r+w permission for all and is owned by me, the mount point on the server is full r+w as is the mount on the host so I am a blank slate for ideas. Now here comes the bad news, I forgot to mention that this sda2 that Im trying to mount has FAT as the file system, VFAT to be exact.

---

### Post by nothingspecial on 2010-10-18
You set the permissions of a fat partition when mounting using umask, dmask and fmask.

You can set ownership with uid= and gid=

Here is a link

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by 3Miro on 2010-10-18
>  joe@joe-desktop:~$ ls -ld /dev/sda2
brwxrwxrwx 1 joe disk 8, 2 2010-10-17 15:22 /dev/sda2 

>  sshfs joe@192.168.1.103:/home/joe/sda2 ~/sda2 

Something is wrong here. I should have seen it earlier.

When you use sshfs, you have to specify a folder on the server. You don't use sshfs to mount a device. Basically, on the server, you have to mount the device with automount (nautilus) or explicitly with
```
 mount /dev/sda2 /media/server_folder 
```
If "/dev/sda2" corresponds to a system partition (/ or /home) then it is mounted already, then you have to pick a folder on that partition.

Then on the client, you should make a folder of your own inside /home/joe_at_client and then try:
```
 sshfs joe@<server_ip>:/media/server_folder /home/joe_at_client/client_folder 
```

On the client folder, you will be able to do whatever your user normally can. On the server_folder, you should have the same access as user joe does.

---

### Post by jquis8411 on 2010-10-18
Ha got it, Thank you, thank you, thank you, I was mounting the VFAT partition wrong. Sorry I didnt mention it in the original post, I lost track of that very important fact. Anyway thanks again guys, you did it.

---

