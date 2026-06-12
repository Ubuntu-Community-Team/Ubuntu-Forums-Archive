---
title: "Mounting a fs changes permissions on a file. Why? and how can I prevent it?"
date: 2012-09-05
forum: General Help
---

### Post by cheerPuncH on 2012-09-05
Hi,

I'm mounting a file system. The mounting point folder has chmod 777 permission, but when I mount the fs the permissions change to chmod 755. Because the permissions change I am not able to transfer files without using sudo. (I want to be able to do this without using sudo). Why is this happening? How can I prevent it? or How can I change the permissions back to 777 once the fs has been mounted?
(I've attached an image.)

Thanks.

---

### Post by redmk2 on 2012-09-05
> **cheerPuncH said:**
> Hi,

I'm mounting a file system. The mounting point folder has chmod 777 permission, but when I mount the fs the permissions change to chmod 755. Because the permissions change I am not able to transfer files without using sudo. (I want to be able to do this without using sudo). Why is this happening? How can I prevent it? or How can I change the permissions back to 777 once the fs has been mounted?
(I've attached an image.)

Thanks.
Sounds like this is a remote partition that is being mounted and the file system is NTFS.  The file permission ore set upon mounting locally.  The *mount point* permissions do not have anything to do with setting the subdirectory permissions.

Am I correct?  What file system on the partition you are trying to mount?

---

### Post by TheFu on 2012-09-05
You need to set the userid and groupid in the mount command for cifs or smb mounts.

**$ man mount.cifs **
will explain everything.  There is a **CIFS how-to guide** here too.

---

### Post by cheerPuncH on 2012-09-06
Thanks redmk2 and TheFu for responding. Ultimately, my fstab file was correct (I double checked with man mount.cifs), but I was missing one small step. In the the [CIFS how-to-guide]("http://ubuntuforums.org/showthread.php?t=288534") (thanks TheFu), it had a step where I needed to edit nsswitch.cof by adding 'win'to the host line. That additional edit solved all my problems.

---

### Post by TheFu on 2012-09-06
I can't imaging that WINS would solve any issue, ever, but if you got it working ... that's good. ;)

---

### Post by redmk2 on 2012-09-06
> **cheerPuncH said:**
> Thanks redmk2 and TheFu for responding. Ultimately, my fstab file was correct (I double checked with man mount.cifs), but I was missing one small step. In the the [CIFS how-to-guide]("http://ubuntuforums.org/showthread.php?t=288534") (thanks TheFu), it had a step where I needed to edit nsswitch.cof by adding 'win'to the host line. That additional edit solved all my problems.

I agree with @TheFu.  This is no real fix and it will come back to bite you someday.  But...It does reveal some of your problem.  The lack of proper name resolution of the hosts in your network.

How about a peek at your /etc/fstab?

---

### Post by TheFu on 2012-09-06
There is nothing about WINS being needed in the mount.cifs man page.  I thought you were using the IP address, but if you aren't, can you "ping" each machine, by name, from the other?  If not, you need to either setup a DNS server "somewhere" on your network or drop an entry into each /etc/hosts file.

Many consumer routers can provide local DNS ... I know that DD-WRT supports this in the Administration-> Services though the text to enter isn't intuitively obvious.  I **know** this works.  I'd assume that Tomato can do it too, but have that router disconnected and reconfigured for an InstallFest in a few days.

The dd-wrt DNSmasq section:

-b --domain=yourdomain.com.
address=/xbmc1/192.168.1.23
address=/xbmc2/192.168.1.24
address=/xbmc3/192.168.1.25
....

The trailing '.' is critical above.  From any machine on the network, I can ping xbmc1, 2, or 3 without locally modifying /etc/hosts files.  I've run DNS on a linux server too, but that is more complex than most of us want and it can be a huge security issue. Bind (the DNS service) has been highly cracked over the years.  I've had a machine cracked into using BIND vulnerabilities (just 3 months behind on the version back in 2000) myself. I don't run bind any more.

---

