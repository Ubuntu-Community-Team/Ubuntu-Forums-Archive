---
title: "gconf/ICE problems after /home mounted in ext3"
date: 2010-09-25
forum: General Help
---

### Post by barefootpenguin on 2010-09-25
Hi,

I recently installed ubuntu 10.04 on a friend's Dell Inspiron 6000.  I partitioned the HD as follows:

sda1        ext4        Linux
sda2        Extended    default 1.5 GB
sda3        ext3        shared space
sda4        ntfs        (for future Windows installation)
sda5        swap        default 1.5 GB

I then mounted my /home directory onto sda3.  (During this process, I ran gedit with sudo instead of the recommended gksudo).  

The resulted in the following error messages ensued:

**During startup:**

> Could not update ICEauthority file /home/wildasin/.ICEauthority

Hitting Close resumes startup.

**After startup:**

> The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

and

> The panel encountered a problem while loading "OAFIID:GNOME_IndicatorApplet".

**Upon starting movie player the first time:**

> No database available to save your configuration: Unable to store a value at key '/apps/rhythmbox/library_locations', as the configuration server has no writable databases. There are some common causes of this problem: 1) your configuration path file /etc/gconf/2/path doesn't contain any databases or wasn't found 2) somehow we mistakenly created two gconfd processes* 3) your operating system is misconfigured so NFS file locking doesn't work in your home directory* or 4) your NFS client machine crashed and didn't properly notify the server on reboot that file locks should be dropped. If you have two gconfd processes (or had two at the time the second was launched), logging out, killing all copies of gconfd, and logging back in may help. If you have stale locks, remove ~/.gconf*/*lock. Perhaps the problem is that you attempted to use GConf from two machines at once, and ORBit still has its default configuration that prevents remote CORBA connections - put "ORBIIOPIPv4=1" in /etc/orbitrc. As always, check the user.* syslog for details on problems gconfd encountered. There can only be one gconfd per home directory, and it must own a lockfile in ~/.gconfd and also lockfiles in individual storage locations such as ~/.gconf 
(emphasis added)

Now, I understand that access rights are not maintained on ext3.  Does this mean that NFS file locking is impossible on ext3?  If so, is there a way to mount /home on an ext3 partition and still have gconf run?

Or is my problem elsewhere?

And, if the first of these error messages is related to my use of sudo instead of gksudo, how do I fix that problem?  I already tried running

> chown wildasin:wildasin /home/wildasin/.ICEauthority
chmod 644 /home/wildasin/.ICEauthority

as per suggestions on another thread, but to no avail.

Thanks in advance for any help on this!

Noah

---

### Post by barefootpenguin on 2010-09-26
Problem solved.  I ran:

> chown wildasin:wildasin /home/wildasin/.ICEauthority
chmod 644 /home/wildasin/.gconf 

in safe mode and it worked like a charm.

Cheers,

Noah

---

