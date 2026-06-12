---
title: "Error - sudo: must be setuid root while creating directory under /usr"
date: 2009-12-25
forum: General Help
---

### Post by prantikd on 2009-12-25
Hi,

I am trying to create a directory in /usr which is having root permissions -
```
drwxr-xr-x 11 root root 4096 2009-04-20 19:30 usr
```I tried the following command:
```
sudo mkdir /usr/prantikd
```But it is throwing error as:
```
sudo: must be setuid root
```It would be very kind if anyone knows how to resolve this issue.

Thanks,
Prantik

---

### Post by vishvesh on 2010-01-25
I am facing a similar issue. Every time I run sudo in terminal, I get this message "sudo: must be setuid root"

If I run "su", I get "setgid: Operation not permitted", If I try using "sudo su", I get "sudo: must be setuid root".

I haven't installed anything recently, It seems to have gone bad. My machine doesn't show option for shut down which it used to show previously.

---

### Post by vishvesh on 2010-01-25
I tried couple of things. I logged in as root user. Tried to run sudo. Terminal showed up different error "Segmentation fault" it also informed me that the permission had gone bad.

I tried this. Picked it up from this forum.
 > root>chown root:root /usr/bin/sudo
root>chmod 4111 /usr/bin/sudoIt didn't help. 

I tried  > chmod 0440 sudoers which solved the problem for me. It looks like the permission for sudoers file had gone bad. It had changed to 0777 instead of 0440

---

### Post by saurabhgeo on 2010-03-13
Hey Vishvesh 

Could you tell me How were you able to log in as root user since sudo is not working and I donot see How can i log in as root user

---

### Post by saurabhgeo on 2010-03-13
I tried this but I do not see it working in my case 

also I have tried the previous suggestions but it do not work 

saurabh@saurabh-laptop:/root$ chmod 0440 sudoers
chmod: cannot access `sudoers': No such file or directory

---

### Post by sisco311 on 2010-03-13
You have to boot into recovery mode:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

then run:
```
chown root:root /usr/bin/sudo
chmod 4111 /usr/bin/sudo
chmod 0440 /etc/sudoers
```

Did you play with the permissions/ownership of /usr/bin? What's the output of:
```
ls -al /usr/bin
```

---

### Post by saurabhgeo on 2010-03-13
Hello sisco311

thanks for your reply.

I have already executed these suggestions before but it did not solved the problem.

I have attached a partial output of the command ls -al /usr/bin.

any more suggestion would be greatly appreciated.

---

### Post by saurabhgeo on 2010-03-13
Hello sisco311

i tried again and it worked .

might be i was wrong in something previously

Thanks for your prompt reply 

Regards

---

### Post by trinity6 on 2010-06-24
I have tried all the above mentioned commands ,  still it doesnt work :( 
Can u suggest soemthing else ?

---

### Post by sisco311 on 2010-06-24
> **trinity6 said:**
> I have tried all the above mentioned commands ,  still it doesnt work :( 
Can u suggest soemthing else ?

Sorry, I just realized that there was a typo in the second command.


try:
```
chown root:root /usr/bin/sudo
chmod 4111 /usr/bin/sudo
chmod 0440 /etc/sudoers
```

I edited my first post as well.


If that doesn't work, then please post the output of:
```
ls -alh /usr/bin/sudo
ls -alh /etc/sudoers
```
```
mount
```
and
```
find /{s,}bin /usr/{s,}bin -perm +6000 -exec ls -alh '{}' +
```

---

### Post by sagethram on 2010-07-28
sudo not working.. unable to connect to network,mounted portion of hard disk.

sudo:must be setuid root --this is the message I'm getting in the terminal

History behind this is I ended up changing the owner by putting the following while fixing someother problem

sudo chown -R myusername:myusername /home/myusername/.*

after reboot, I'm unable to connect to the network and above mentioned problems (sudo:must be setuid root)

surfed through the net and tried some of the solutions provided in this link [http://ubuntuforums.org/showthread.php?t=1363859](http://ubuntuforums.org/showthread.php?t=1363859)

this is the output of the commands
ls -alh /usr/bin/sudo

---s--x--x 2 mohanram mohanram 106k 2010-06-19 01:58 /usr/bin/sudo

ls -alh /etc/sudoers

-r--r----- 1 mohanram mohanram 470 2010-04-24 05:38 /etc/sudoers

find /{s,}bin /usr/{s,}bin -perm +6000 -exec ls -alh '{}' +

-rwsr-xr-x 1 mohanram mohanram  25k 2008-12-08 14:44 /bin/su
---s--x--x 2 mohanram mohanram 106k 2010-06-19 01:58 /usr/bin/sudo
---s--x--x 2 mohanram mohanram 106k 2010-06-19 01:58 /usr/bin/sudoedit

Need ur help to solve this

Regards,
Ram

---

### Post by sisco311 on 2010-07-28
Hi, sagethram

and welcome to the forums!

It looks like you accidentally changed the owner of all the files from your root partitions. 

In theory, you could boot a LiveCD and  manually go through every file and directory in / and set the proper permissions, but that's very time consuming. 

So, backup your data and reinstall.

---

### Post by mlempenau on 2011-01-19
Well, I think I have a similar problem, I believe the ownership has been improperly set my accident.  Now I don't know what to do.  Thanks for helping.  

mikee@mike-desktop:~$ chown root:root /usr/bin/sudo
chown: changing ownership of `/usr/bin/sudo': Operation not permitted
mikee@mike-desktop:~$ chmod 4111 /usr/bin/sudo
chmod: changing permissions of `/usr/bin/sudo': Operation not permitted
mikee@mike-desktop:~$ ls -alh /usr/bin/sudo
-rwxr-xr-x 2 root administrator 125K 2010-09-01 03:38 /usr/bin/sudo
mikee@mike-desktop:~$ ls -alh /etc/sudoers
-r--r----- 1 root administrator 609 2010-09-17 19:03 /etc/sudoers
mikee@mike-desktop:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sdb1 on /media/Ubuntu type ext4 (rw,nosuid,nodev,group=administrator)
/dev/sdd2 on /media/Test type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd4 on /media/Backup type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1 on /media/MasterXP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/mikee/.Private on /home/mikee type ecryptfs (ecryptfs_sig=b345a1084d2bdc54,ecryptfs_fnek_sig=0c25c446f9d602b6,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/mikee/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mikee)
mikee@mike-desktop:~$ find /{s,}bin /usr/{s,}bin -perm +6000 -exec ls -alh '{}' +
mikee@mike-desktop:~$ find /{s,}bin /usr/{s,}bin -perm +6000 -exec ls -alh '{}' +
mikee@mike-desktop:~$

---

### Post by dhavaljparekh on 2011-09-15
Hi Sisco,

Thanks for the code, its really working for me.

Thanks again

---

### Post by dhavaljparekh on 2011-09-15
Hi mlempenau,

don't do at your current user console
login with recovery mode like below link
**[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)**
(use only "Booting into recovery mode" part)
 and run the below command after selecting root user

[B]chmod 4111 /usr/bin/sudo
chmod 0440 /etc/sudoers
exit

[/B]to reboot system
[B]sudo reboot

[/B]its done, enjoy :)

---

