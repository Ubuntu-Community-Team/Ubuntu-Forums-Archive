---
title: "Create temporary filesystem on partition?"
date: 2011-06-03
forum: General Help
---

### Post by la_mer222 on 2011-06-03
Hi folks,
 
I have a question that I'm sure is so simple to answer, and I'm just overlooking the solution. What I want to do is have my /dev/sda3 partition always go back to default (the way it was when the computer first started up thanks to my /etc/skel/student directory.) But I can't seem to get this to work. Below are more details---
 
I have 3 separate partitions on my computer:
 
/dev/sda1 == "/"
/dev/sda2 == "swap"
/dev/sda3 == "/home/student/" (yes, that's intentional.)
 
I have the student home directory on /dev/sda3 because I was hoping to find a way that I could easily provide a rw environment while the student was logged into the machine, but is then erased and set back to default upon next reboot.
 
My original idea was on boot up was to use /etc/rc.local and...
 
1) rm -rf /home/student/*
2) mkhomedir_helper /home/student /etc/skel/student (which is where my skel directory is for my student account.)
 
Problem is, there are times where rm -rf fails and says a directory is not empty (and the directory that says is not empty varies from time to time, so I can't reliably delete the directory manually from /etc/rc.local). mkhomedir_helper won't run if it sees /home/student/, so on the next reboot, the student can't get to a desktop because it doesn't exist.
 
I've tried a number of things, even mkfs.ext3 /dev/sda3 as a way to quick format the hard drive on next boot up then use mkhomedir_helper, but that takes way too long in the boot up process as is just not an effective solution.
 
Any help would be so greatly appreciated. Thank you.
Hopefully, I'm not over complicating my explanation.

---

### Post by FormatSeize on 2011-06-03
Have you tried running cfdisk? You could do that, and delete the partition, and it will become free space. Then create another sda3 partition, and use the following as a guide for building an ext3 filesystem from the [Linux From Scratch]("http://www.linuxfromscratch.org/lfs/view/stable/") book replacing "LFS" with your corresponding items:
 
> 
 
To create an ext3 file system on the LFS partition, run the following:
```
mke2fs -jv /dev/<xxx>
```
Replace <xxx> with the name of the LFS partition (hda5 in our previous example).
 
If you are using an existing swap partition, there is no need to format it. If a new swap partition was created,
it will need to be initialized with this command:
```
mkswap /dev/<yyy>
Replace <yyy> with the name of the swap partition.
```
2.4. Mounting the New Partition
Now that a file system has been created, the partition needs to be made accessible. In order to do this, the partition
needs to be mounted at a chosen mount point. For the purposes of this book, it is assumed that the file system is
mounted under / mnt/ lfs, but the directory choice is up to you.
Choose a mount point and assign it to the LFS environment variable by running:
```
export LFS=/mnt/lfs
```
Next, create the mount point and mount the LFS file system by running:
```
mkdir -pv $LFS
mount -v -t ext3 /dev/<xxx> $LFS
```
Replace <xxx> with the designation of the LFS partition.
 
If using multiple partitions for LFS (e.g., one for / and another for / usr), mount them using:
```
mkdir -pv $LFS
mount -v -t ext3 /dev/<xxx> $LFS
mkdir -v $LFS/usr
mount -v -t ext3 /dev/<yyy> $LFS/usr
```
Replace <xxx> and <yyy> with the appropriate partition names.
Ensure that this new partition is not mounted with permissions that are too restrictive (such as the nosuid, nodev,
or noatime options). Run the mount command without any parameters to see what options are set for the mounted
LFS partition. If nosuid, nodev, and/or noatime are set, the partition will need to be remounted.
If you are using a swap partition, ensure that it is enabled using the swapon command:
```
/sbin/swapon -v /dev/<zzz>
```
Replace <zzz> with the name of the swap partition.

---

### Post by lmarmisa on 2011-06-03
I believe that Ubuntu (and other Debian distros) removes the contents of the folder /tmp at boot. So, you could try to map the files of the student account there.

My proposal does not use the /dev/sda3 partition. Anyway, you could map the /tmp dir in this partition, if you wish.

You could define a symbolic link for that purpose:

```

sudo mv /home/student /home/student.old
mkdir /tmp/home/student
sudo ln -s /tmp/home/student /home/student

```

In relation with the two commands of file /etc/rc.local, you do not need the first one now (rm -rf /home/student/*).

You need these commands for creating the student folder:

```

mkdir /tmp/home/student
chown student:student /tmp/home/student

```

Your second command is still useful:

```

mkhomedir_helper /home/student /etc/skel/studens

```

I hope that this idea could help you.

---

### Post by la_mer222 on 2011-06-06
@Format:
 
Thank you for the information you posted. I haven't gone through the steps yet but if I'm unable to get the post that Imarmisa made, I will look at doing that.
 
@Imarmisa:
 
Thanks for your information. I have a question as I can't seem to put the 2+2 together. When I tell /etc/rc.local to mkdir /tmp/student, it doesn't write anything to the /tmp directory. Once the distribution is finished loading (and where it should drop the user to the desktop), I open up a terminal and can run: sudo sh /etc/rc.local and the script follows through OK. Would there be any reason that the script can't create the folder under /tmp during boot up?

---

### Post by lmarmisa on 2011-06-06
> **la_mer222 said:**
> 
@Imarmisa:
 
Thanks for your information. I have a question as I can't seem to put the 2+2 together. When I tell /etc/rc.local to mkdir /tmp/student, it doesn't write anything to the /tmp directory. Once the distribution is finished loading (and where it should drop the user to the desktop), I open up a terminal and can run: sudo sh /etc/rc.local and the script follows through OK. Would there be any reason that the script can't create the folder under /tmp during boot up?

I forgot to add the option "**-p**" in the two commands **mkdir**:

```

mkdir -p /tmp/home/student

```

The option -p implies "no error if existing, make parent directories as needed".

The command mkdir /tmp/student does not require the option -p because the parent directory /tmp exists.

According to your comment, it seems the the directory is created by the script /etc.local and then it is removed with the other contents of the directory /tmp. Maybe this is a case of a critical race condition. Try to add a sleep command at the beginning of rc.local:

```

sleep 10

```

I have checked the method in my computer and it works just fine here. I do not need any sleep command. I am running Ubuntu 10.10 Desktop.

---

### Post by la_mer222 on 2011-06-08
@Imar, thank you for your help. You put me on the right direction and was able to get this ifgured out.

---

