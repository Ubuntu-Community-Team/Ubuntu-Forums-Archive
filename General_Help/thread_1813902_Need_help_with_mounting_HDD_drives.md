---
title: "Need help with mounting HDD drives"
date: 2011-07-28
forum: General Help
---

### Post by ashwinrao on 2011-07-28
In my work place, system admin's allowed me to install Ubuntu 10.04 for my use. They have installed Ubuntu and created 2 ext4 partitions. They provided 2 users admin rights including me (I'm sharing machine with other). The issue is we both can't mount these additional partitions for use(installed with root ownership). I have tried all the methods so far. Even installed Storage Device Manager. But, it is little bit geek to me when comes to selecting options. Currently, I can access the drives. But, while other user logged in chooses the drive to mount, it simple disappears from the list. Please some body guide me through the settings so that these additional drives will be available for all the users. Please note all the users has admin rights and belongs to admin group. These drives were ext4 sd6 and sd7. If successful, many other machines in work place will have Ubuntu in it.

---

### Post by ashwinrao on 2011-07-28
I can not ask the help of system admins as Linux is geek to them. You can also provide the example of /etc/fstab for sda6 and sda7 so that it can be available for all the users to mount it and use it.

---

### Post by seawolf167 on 2011-07-28
Please post the output of the following commands inside CODE tags when you hit the reply button

```
sudo blkid
mount
fdisk -l
cat /etc/fstab
```

---

### Post by quadproc on 2011-07-28
> **ashwinrao said:**
>  The issue is we both can't mount these additional partitions for use(installed with root ownership).
I am not really sure what you have tried and what the system responded so I will write a bit about mounting and then suggest an experiment.

First, you mount* file systems,* not drives or partitions.  You mentioned sd6 and sd7 but those identifiers are not what you should have.  Normally, a file system will be identified as something like /dev/sdc5; this means a disk drive, the third one, and the fifth partition.

Here is the experiment:

Using sudo, create a new mounting place for your new file system to reside.  Assume that you call the new place extra_users.
```
sudo mkdir /extra_users

```Now, assuming that you have already created file systems on your new drives (use gparted to do this if you haven't already), mount a new drive:
```
sudo mount -t [COLOR=Red]ext3[/COLOR] /dev/[COLOR=Red]sdc5[/COLOR] /extra_users
```Substitute the actual file system type for [COLOR=Red]ext3[/COLOR], and the actual file system for [COLOR=Red]sdc5[/COLOR].

Be sure to umount the drive before quitting your session or shutting down the computer.

If you have trouble then please post a copy of the terminal window so that we can see the details.

quadproc

---

### Post by ashwinrao on 2011-07-28
Sure, I'll do that when I go to office tomorrow. Currently, I'm posting question from my home machine. Thanks for your reply and I'll let you know. My office hours is: 1 pm -9 pm IST.

---

### Post by ashwinrao on 2011-07-28
@[quadproc]("http://ubuntuforums.org/member.php?u=1004489") Thanks! yes, they were /dev/sd6 and /dev/sd7 and they were labled as DiskD and DiskE. They were separate from file system. First, it was created as NTFS and then changed to ext4. It seems that I have misunderstood 'users' option in Storage Device Manager while using it. It seems that I need to provide 'rw' option to them.

---

### Post by seawolf167 on 2011-07-28
> **ashwinrao said:**
> Sure, I'll do that when I go to office tomorrow. Currently, I'm posting question from my home machine. Thanks for your reply and I'll let you know. My office hours is: 1 pm -9 pm IST.

You may want to setup your work machine as an [SSH]("https://help.ubuntu.com/community/SSH") server so you can remotely connect to it.

The basics:

Install the server

```
sudo apt-get install openssh-server
```

Ask your network admins to poke a hole in their firewall and forward it to your machine. You can find your LAN IP from 

```
ifconfig
```

Once (if) they open a port for you, edit your ssh config file to reflect that port

```
sudo gedit /etc/ssh/sshd_config
```

And change from Port 22 to Port XYZ, where XYZ is your forwarded port

```
Port 22
```

Then restart the ssh-server

```
sudo service ssh restart
```

Now you can connect to your machine from [home]("https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo") (and forward X windows if you want), with 

```
ssh -l *username* -p *port_number* *work.wan.ip.address*
```

---

### Post by ashwinrao on 2011-07-28
It is not possible as our company is dealing with sensitive data and will not be allowed to accessed from other public IP addresses. Any how, I'll check this in depth since my colleagues are now interested in Linux and wants to convert their OS.

---

### Post by Mark Phelps on 2011-07-28
> **ashwinrao said:**
> Please some body guide me through the settings so that these additional drives will be available for all the users.

I don't think that ALL of you will be able to mount the same filesystems read/write -- at the same time.

Sure, servers can do this, but I don't believe that desktop computer OSs can do this.

---

### Post by ashwinrao on 2011-07-29
@ seawolf167 : Thanks for your help so far. Please review the outputs you have asked for: 

For sudo blkid:
[PHP]
/dev/sda1: UUID="56e455b4-3fe5-4f2b-9384-aa880720afde" TYPE="swap" 
/dev/sda5: UUID="d08d12d4-1847-4d71-a427-7d07e21960fe" TYPE="ext3" 
/dev/sda6: LABEL="DiskE" UUID="9c7d11bb-d8f8-4587-bde7-4257aa392f2f" TYPE="ext4" 
/dev/sda7: LABEL="DiskD" UUID="30bb260c-7ab1-424d-9584-ce1110c1c4ea" TYPE="ext4" 
[/PHP]

For mount:
[PHP]
one on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda6 on /media/DiskE type ext4 (rw,noexec,nosuid,nodev)
/dev/sda7 on /media/DiskD type ext4 (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/myusername/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=myusername)
[/PHP]

For cat /etc/fstab:
[PHP]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc       /proc         proc  nodev,noexec,nosuid  0  0  
/dev/sda5  /             ext3  errors=remount-ro    0  1  

/dev/sda1  none          swap  sw                   0  0  


/dev/sda6  /media/DiskE  ext4  users                0  0  
/dev/sda7  /media/DiskD  ext4  users                0  0  
[/PHP]

There is no output for fdisk -l. 

@Mark Phelps: Thanks! But, I don't want to mount the drives for all users at the same time. If another user is using my machine those drives should be available to them.

---

### Post by seawolf167 on 2011-07-29
First, are the 2 users of the computer in the same group? If not, please add them to the same group. You can either use the chmod command or do it graphically by following [this link]("https://help.ubuntu.com/community/AddUsersHowto").

```
man chmod
```

After you do that, please use the chown command to change the ownership of the two drives so that the group owns the drives

```
man chown
```

Then, edit the /etc/fstab file  to reflect the changes below.

> **ashwinrao said:**
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc       /proc         proc  nodev,noexec,nosuid  0  0  
/dev/sda5  /             ext3  errors=remount-ro    0  1  

/dev/sda1  none          swap  sw                   0  0  


/dev/sda6  /media/DiskE  ext4  **rw, suid, dev, exec, auto, users, and async**      0  0  
/dev/sda7  /media/DiskD  ext4  **rw, suid, dev, exec, auto, users, and async**      0  0  


Change the contents of /etc/fstab

```
gksu gedit /etc/fstab
```

to reflect the bolded changes above, then restart and see if everything works alright?

---

### Post by Morbius1 on 2011-07-29
> /dev/sda6  /media/DiskE  ext4  **rw, suid, dev, exec, auto, users, and async**      0  0  
/dev/sda7  /media/DiskD  ext4  **rw, suid, dev, exec, auto, users, and async**      0  0 That won't work for a number of reasons ( spaces, no such thing as an "and" option, etc )

* If the partitions are mounted unmount them:
```
sudo umount /media/DiskE
sudo umount /media/DiskD

```* Try changing those lines to this:
```
/dev/sda6  /media/DiskE ext4 defaults,noatime 0 2  
/dev/sda7  /media/DiskD ext4 defaults,noatime 0 2
```* Then run the following command to test for errors and mount the new partitions without a reboot:
```
sudo mount -a
```Now you have to define what you mean by "sharing" the partition. This can get complicated depending on what you want each user to do.

You can just set the partitions to allow everyone to access it:
```
sudo chmod 777 /media/DiskE
```Both user1 and user2 will be able to add files but user2 will also be able to delete user1's files. And neither user will be able to edit the others files.

You can add the sticky bit to the chmod command:
```
sudo chmod 1777 /media/DiskE
```This will make it so user1 can't delete user2's files but user1 will still not be able to edit user2's files.

If you want both users to access the folder and allow both to edit each other's files:
```
sudo chmod 3770 /media/DiskE
sudo chown :plugdev /media/DiskE
```Then you are going to have to change the default umask in /etc/profile to 002 and all users will have to logoff and logon again for the umask to take affect.

When user1 adds a file it will save as:
owner = user1
group = plugdev
permissions = 664

Since user2 is also a member of plugdev both users will be able to edit the other's files. The "3770" is a combination of the "sitcky bit" and the "setgid" bit which will make it so that all new files will inherit the group of the mount point and only the owner and root can delete a file.

---

### Post by Mikhail Titov on 2011-07-29
> **ashwinrao said:**
> There is no output for fdisk -l. How is that possible?

---

### Post by Morbius1 on 2011-07-29
Didn't even see that.

Maybe he forgot the sudo:
```
sudo fdisk -l
```

---

### Post by ashwinrao on 2011-07-29
@ [seawolf167]("http://ubuntuforums.org/member.php?u=1042634") and [Morbius1]("http://ubuntuforums.org/member.php?u=982144") : Thanks a lot! I'll try these and post the results on Monday as this is a weekend. It is okay with the full access for files as I have already encrypted '/home' folders for both where the logins and SSH details are there.

@ [Mikhail Titov]("http://ubuntuforums.org/member.php?u=1090148") and [Morbius1]("http://ubuntuforums.org/member.php?u=982144") : This thought came to mind. But, I already used sudo for previous command and thought it is not necessary :D . My Bad, thought I'm already authenticated as sudo. Does it makes difference in the same terminal window and used sudo for previous command?

---

### Post by seawolf167 on 2011-07-29
> **Morbius1 said:**
> That won't work for a number of reasons ( spaces, no such thing as an "and" option, etc )

Thanks for the corrections, I wrote this in a hurry and didn't go back and check it :( I obviously needed to!

---

### Post by Morbius1 on 2011-07-29
If you use sudo once and you give it the next sudo command quickly you won't be prompted for a password again but you still need the sudo. It tells the system you are running the command as root.

You may be thinking about a non-sudo setup where you do a :
```
su root
```In those distros that have a separate root user set up then all the operations done in the the terminal session are assumed to be root.

---

### Post by ashwinrao on 2011-08-01
@ seawolf167 and  Morbius1, Thanks a lot! your valuable suggestions and feedback's resolved my issue completely. Proud to me member of Ubuntu community! Thanks again!:popcorn:

---

