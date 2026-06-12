---
title: "mounting and binding via fstab"
date: 2010-12-10
forum: General Help
---

### Post by fmhoyt on 2010-12-10
I have a dual boot setup with Ubuntu 10.10 and Windows 7 on an Asus UL80jt (64-bit). 

I am trying to keep various data directories on a separate partition which can be accessed by both Ubuntu and Windows. This is sda3, labelled as "shared": 

```
% sudo blkid 
...
/dev/sda3: LABEL="shared" UUID="fab4ccb2-3642-4f17-b82f-337201d19d3c" TYPE="ext3"
...
```

I modified my fstab file to mount this partition, and then to bind (for example) a Music directory on this partition to ~/Music: 

```
% more /etc/fstab 
...
# Mount sda3
UUID=fab4ccb2-3642-4f17-b82f-337201d19d3c /media/shared ext3 defaults 0 0
...
#Linking /media/shared/Music to ~/Music
/media/shared/Music /home/fmhoyt/Music none bind 0 0

```

This successfully mounts "shared" as /media/shared, but fails to bind /media/shared/Music to ~/Music. 

I get no errors from: 

```
% sudo mount -a
```. 

The following works in a shell: 

```
% sudo mount --bind /media/shared/Music ~/Music
```

I would rather have the binding take place as startup (or login). However, a shell script containing this does not work at startup (perhaps because of sudo?). 

I have tried both adding a script containing the command above to Startup Applications, and adding it to /usr/local/bin (without the sudo commands) and calling it in /etc/rc.local. As far as I can tell, neither of these approaches has any effect. 

As such, the only way I can mount /media/shared/Music as ~/Music is by executing a shell command after startup/login.

One of my goals with this setup is to be able to use UbuntuOne synchronization, which does not work with symlinks. 

Can anyone tell what I am doing wrong? 

Thank you

---

### Post by lmarmisa on 2010-12-10
I recommend to use a symbolic link.

Simply type these commands:

```

cd
mv Music Music.old
ln -s /media/shared/Music Music

```I have moved the Music dir to a different directory named Music.old. Remove Music.old it if you want.

---

### Post by fmhoyt on 2010-12-10
Thank you for the reply!

I should have mentioned in my initial post that I am trying to use UbuntuOne synchronization with my setup. In other words, I want to be able to synchronize the directories that I'm mounting with my Ubuntuone account. 

UbuntuOne sync apparently does not work with symlinks. So, the solution that Imarmisa suggests will allow me to link my ~/Music with /media/shared/Music, but it won't allow me to use UbuntuOne synce. 

The setup I am trying for has apparently worked for others, such as poster Krippa (see reply #4): 

[http://ubuntuforums.org/showthread.php?t=1477147&highlight=mount+bind+Music](http://ubuntuforums.org/showthread.php?t=1477147&highlight=mount+bind+Music)

So I'm puzzled as to why it isn't working for me.

---

### Post by lmarmisa on 2010-12-11
Edit the file /etc/rc.local (** sudo gedit /etc/rc.local** ) and add this line:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

**mount --bind /media/shared/Music /home/fmhoyt/Music**

exit 0

```Save, exit and reboot your system.

I hope this solution will work fine (at least it runs ok on my computer).

---

### Post by fmhoyt on 2010-12-11
Unfortunately your solution does not work. 

Adding the following to /etc/rc.local has no (apparent) effect: 

```
$ sudo nano /etc/rc.local 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

mount --bind /media/shared/Music /home/fmhoyt/Music

exit 0
```

Interestingly, after start up "mount -a" has the following results: 

```
$ sudo mount -av
...
mount: /media/shared/Music already mounted on /home/fmhoyt/Music
nothing was mounted
```

However, none of the contents of /media/shared/Music appear in ~/Music: 

```
$ ls ~/Music
$
```

Once I run: 

```
$ sudo mount --bind /media/shared/Music ~/Music
```

Then the contents appear. 

For what it's worth, I have also made sure that ownership of /media/shared is assigned to my username. 

```
$ sudo chown fmhoyt:fmhoyt /media/shared
```

Also, I notice that if I place a simple shell command in /etc/rc.local, or place the command in /usr/local/bin and call in in /etc/rc.local (with the appropriate permissions), nothing happens: 

```
$ sudo nano /etc/rc.local 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo "My name is Fred" > /home/fmhoyt/Desktop/Fred.txt"

exit 0
```

The same command works if I create in my home directory and add it to Startup Applications.

Still mystified.

---

### Post by argedion on 2010-12-11
Hope this doesn't make me look dumb *L* but could you now write a script to run at start up to do this for you? Maybe it could run after fstab has run like right after you log on.

---

### Post by fmhoyt on 2010-12-11
> **argedion said:**
> Hope this doesn't make me look dumb *L* but could you now write a script to run at start up to do this for you? Maybe it could run after fstab has run like right after you log on.
Thank you for the reply. 

Like I said above, I wrote the following script: 

```

#!/bin/sh
mount --bind /media/shared/Music /home/fmhoyt/Music

```

I have tried both putting this in my Startup Applications (so that it runs at log-in, after fstab applies), as well as including it in or calling it from /etc/rc.local (which, I believe, runs before fstab?). 

Neither approaches had any effect. The script does, however, work when I run it after login.

---

### Post by lmarmisa on 2010-12-12
I would like to check if the problem is limited to the directories of your account.

Please, delete the **mount** command of the file **/etc/rc.local**.

Then type this command

```

sudo mkdir /media/Music

```and change the line of the file **/etc/fstab** corresponding to **/media/shared/Music**:


```

...
#Linking /media/shared/Music to /media/Music[FONT=monospace]
[/FONT]/media/shared/Music /media/Music none bind 0 0

```Restart your system and type these commands:

```

cat /etc/ftab
cat /etc/mtab
mount
ls -l /media
ls -l /media/shared
ls -l /media/shared/Music
ls -l /media/Music

```Please, post the outputs of the commands.

Best regards,

Luis

---

### Post by Morbius1 on 2010-12-12
I don't want to contradict anything that lmarmisa has posted because as far I can tell everything posted was textbook correct. But I think the problem is Ubuntu's use of mountall and Upstart. I think that the bind operation is happening before the /media/shared partition is actually mounted.

One possible way around this was suggested by sisco311 in another post. Create an Upstart job that will bind the subdirectory after mountall has completed its job:

Create an upstart file:
```
gksu gedit /etc/init/mount-bind.conf
```With this content:
```
#
# bind mounts
#

description "bind"

start on stopped mountall 

script 

   mount --bind /media/shared/Music /home/fmhoyt/Music 

end script
```

---

### Post by matt_symes on 2010-12-12
Hi

This is, i expect, a silly, silly question but you rc.local file is executable?

sudo chmod 755 /etc/rc.local

Kind regards

---

### Post by fmhoyt on 2010-12-12
Thank you all for your helpful replies!

Responding in order of simplicity: 

> **matt_symes said:**
> Hi

This is, i expect, a silly, silly question but you rc.local file is executable?

sudo chmod 755 /etc/rc.local

Kind regards

I did as Matt suggested but with no change in results: There are still no files listed in ~/Music. 

> **Morbius1 said:**
> I don't want to contradict anything that lmarmisa has posted because as far I can tell everything posted was textbook correct. But I think the problem is Ubuntu's use of mountall and Upstart. I think that the bind operation is happening before the /media/shared partition is actually mounted.

One possible way around this was suggested by sisco311 in another post. Create an Upstart job that will bind the subdirectory after mountall has completed its job:

Create an upstart file:
```
gksu gedit /etc/init/mount-bind.conf
```With this content:
```
#
# bind mounts
#

description "bind"

start on stopped mountall 

script 

   mount --bind /media/shared/Music /home/fmhoyt/Music 

end script
```

Likewise, Morbius' suggestion has no effect: There are still no files appearing in ~/Music. 

> **lmarmisa said:**
> I would like to check if the problem is limited to the directories of your account.

Please, delete the **mount** command of the file **/etc/rc.local**.

Then type this command

```

sudo mkdir /media/Music

```and change the line of the file **/etc/fstab** corresponding to **/media/shared/Music**:


```

...
#Linking /media/shared/Music to /media/Music[FONT=monospace]
[/FONT]/media/shared/Music /media/Music none bind 0 0

```

Restart your system and type these commands:

```

cat /etc/ftab
cat /etc/mtab
mount
ls -l /media
ls -l /media/shared
ls -l /media/shared/Music
ls -l /media/Music

```Please, post the outputs of the commands.

Best regards,

Luis

There is no /etc/ftab. Do you mean fstab? If so:  

```

$ cat /etc/fstab
[comments]
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=eee1d8fd-2289-4224-a8b8-7e5961607eeb /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=9620a39f-20c0-471e-8777-b080f1d40517 /home           ext3    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=6d22b653-67f9-4455-83f4-a138bce2aaaa none            swap    sw              0       0
UUID=fab4ccb2-3642-4f17-b82f-337201d19d3c /media/shared ext3 defaults 0 0
/media/shared/Music /media/Music none bind 0 0 

$ cat /etc/mtab 
/dev/sda6 / ext3 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
/dev/sda3 /media/shared ext3 rw,commit=0 0 0
/media/shared/Music /media/Music none rw,bind,commit=0 0 0
/dev/sda5 /home ext3 rw,commit=0 0 0
/media/shared/Music /home/fmhoyt/Music none rw,bind,commit=0,commit=0 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/home/fmhoyt/.Private /home/fmhoyt ecryptfs ecryptfs_sig=bcb21da60e985097,ecryptfs_fnek_sig=fb8404e866e42f72,ecryptfs_cipher=aes,ecryptfs_key_bytes=16 0 0
gvfs-fuse-daemon /home/fmhoyt/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=fmhoyt 0 0

$ mount 
/dev/sda6 on / type ext3 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda3 on /media/shared type ext3 (rw,commit=0)
/media/shared/Music on /media/Music type none (rw,bind,commit=0)
/dev/sda5 on /home type ext3 (rw,commit=0)
/media/shared/Music on /home/fmhoyt/Music type none (rw,bind)
/media/shared/Music on /home/fmhoyt/Music type none (rw,bind,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/fmhoyt/.Private on /home/fmhoyt type ecryptfs (ecryptfs_sig=bcb21da60e985097,ecryptfs_fnek_sig=fb8404e866e42f72,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/fmhoyt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fmhoyt)

$ ls -l /media
ls -l /media/
total 24
drwxr-xr-x 317 fmhoyt fmhoyt 20480 2010-12-09 00:12 Music
drwxrwxr-x  11 fmhoyt fmhoyt  4096 2010-12-09 23:52 shared

$ ls -l /media/shared
ls -l /media/shared/
total 68
drwxr-xr-x   7 fmhoyt fmhoyt  4096 2010-12-07 03:52 Bibfiles
drwxrwxr-x   3 root   fmhoyt  4096 2010-11-28 10:31 Documents
drwxr-xr-x   2 fmhoyt fmhoyt 12288 2010-12-11 21:09 Downloads
drwxrwxr-x   2 root   root   16384 2010-11-28 00:31 lost+found
drwxr-xr-x 317 fmhoyt fmhoyt 20480 2010-12-09 00:12 Music
drwxr-xr-x   3 fmhoyt fmhoyt  4096 2010-12-09 08:07 Pictures
drwxr-xr-x  10 fmhoyt fmhoyt  4096 2010-12-09 23:41 texmf

$ ls -l /media/shared/Music
[lots of music files]

$ ls -l /media/Music
[lots of music files]

```

So in other words, the procedure is successful at mounting /media/shared/Music as /media/Music.

---

### Post by Morbius1 on 2010-12-12
The only problem now is we don't know which method was successful.

 **matt_symes**'s method required a reboot.

My method required a reboot.

**lmarmisa** was the only one who had the sense to explicitly state a reboot.

Did you undo every other attempt or are all methods still in place?

---

### Post by matt_symes on 2010-12-12
Hi

You can also try
[FONT=monospace]
[/FONT]/media/shared/Music /home/fmhoyt/Music none **defaults**,bind 0 0

in your fstab file.

And if that does not work try

/media/shared/Music /home/fmhoyt/Music **bind** **defaults**,bind 0 0

Kind regards

---

### Post by fmhoyt on 2010-12-12
> **Morbius1 said:**
> The only problem now is we don't know which method was successful.

 **matt_symes**'s method required a reboot.

My method required a reboot.

**lmarmisa** was the only one who had the sense to explicitly state a reboot.

Did you undo every other attempt or are all methods still in place?
I rebooted after each change, and undid changes between methods.

---

### Post by lmarmisa on 2010-12-12
This is not a problem related to mountings or things like that.

All the mountings seem correct.

The problem is related to encryption. All your home folder is encrypted but you are adding to this structure one non-encrypted folder, **/home/fmhoyt/Music**. And, this does not work. The system is unable to decrypt the information of this folder **/home/fmhoyt/Music **because its information is not encrypted. Result: the system does not show any file.

I believe it is not a good idea to mix encrypted and non-encrypted folders.

Best regards,

Luis

---

### Post by fmhoyt on 2010-12-13
> **lmarmisa said:**
> This is not a problem related to mountings or things like that.

All the mountings seem correct.

The problem is related to encryption. All your home folder is encrypted but you are adding to this structure one non-encrypted folder, **/home/fmhoyt/Music**. And, this does not work. The system is unable to decrypt the information of this folder **/home/fmhoyt/Music **because its information is not encrypted. Result: the system does not show any file.

I believe it is not a good idea to mix encrypted and non-encrypted folders.

Best regards,

Luis



You are correct sir. 

I removed the encryption from ~ by using the procedure here: 

[http://ubuntuforums.org/showthread.php?t=1471498](http://ubuntuforums.org/showthread.php?t=1471498)

Having done so, /media/shared/Music mounts as ~/Music. 

Thank you.

---

### Post by lmarmisa on 2010-12-13
Great. :D

Please, mark the thread as SOLVED.

---

