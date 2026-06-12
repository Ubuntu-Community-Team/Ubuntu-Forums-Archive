---
title: "Can't Mount NFS shares with IP address"
date: 2010-03-21
forum: General Help
---

### Post by rustyhann on 2010-03-21
I'm setting up an NFS server on a command line install (9.10) to share a directory for a farmerjoe render farm.  My instructions are from 


[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)


Here is what I have done so far

```
sudo apt-get install portmap nfs-kernel-server
sudo mkdir /farmerjoe
sudo nano /etc/exports
```

With this in my /etc/exports file

```
/farmerjoe 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check)
```

Followed by

```
sudo exportfs -ra
sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-kernel-server restart
```

On the client

```
sudo apt-get install portmap nfs-common
sudo mkdir /render
```

Using this command I can manually mount the NFS share

```
sudo mount 192.168.1.2:/farmerjoe /render
```

When I edit my /etc/fstab to mount the share automatically, it fails

```
sudo nano /etc/fstab
```

With this in the /etc/fstab file

```
192.168.1.2:/farmerjoe /render nfs rw,hard,intr 0 0
```

I do not have DNS installed.  I cannot install a stand alone DNS server on the network which the render farm will run.  I cannot point any of the machines in the render farm to the current DNS server.  The render farm is on a VLAN (in a design lab) with the NFS server receiving a reserved static IP address and the clients receiving DHCP addresses from a currently running server.  After reading this post


[http://ubuntuforums.org/showthread.php?t=321926](http://ubuntuforums.org/showthread.php?t=321926)


it seems that I should be able to mount NFS shares using an IP address.  I have no idea what to do.  Any help would be appreciated.

---

### Post by dcstar on 2010-03-21
> **rustyhann said:**
> 
.........
Using this command I can manually mount the NFS share

```
sudo mount 192.168.1.2:/farmerjoe /render
```

When I edit my /etc/fstab to mount the share automatically, it fails
.........
it seems that I should be able to mount NFS shares using an IP address.  I have no idea what to do.  Any help would be appreciated.

When does it "fail"?, you provide no circumstances or error messages.

If, by chance, it "fails" at boot-up then you probably should be using the fstab/mount parameter that **waits** until the network is up** before** attempting to mount any network share.

---

### Post by rustyhann on 2010-03-21
I noticed an error in my original post

```
/farmerjoe 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check)
```

needs to be

```
/farmerjoe 192.168.**1**.0/255.255.255.0(rw,sync,no_subtree_check)
```

The error I receive is:

mount.nfs: DNS resolution failed for 192.168.1.2: Name or service not known 
mountall: mount /render [643][ terminated with status 32
mountall: Filesystem could not be mounted: /render

The static IP address of the NFS server is 192.168.1.2

---

### Post by rory526 on 2010-03-22
there seem to be a lot of problems with nfs in Ubuntu 9.10. There are a few bug reports with error messages similar to yours. On this page, a few work-arounds are suggested; adding the "nolock", "nobootwait" or "_netdev" options in fstab.

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/504224](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/504224)

From the man page for mount:
```

       _netdev
              The filesystem resides on a device that requires network  access
              (used  to  prevent  the  system  from  attempting to mount these
              filesystems until the network has been enabled on the system).
```

```
nolock
    Do not use locking. Do not start lockd.
```


nobootwait isn't there...


In this one, the poster found a fix to be adding "sleep 5s" in 
/etc/init/mountall-net.conf

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/501678](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/501678)


In this one, the problem was fixed by updating to nfs-common 1:1.2.0-2ubuntu7.

[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/445181](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/445181)

---

### Post by rustyhann on 2010-03-23
I didn't like the work arounds because this will be a production system.  I rolled back to 8.04.  Problem solved.

---

### Post by rory526 on 2010-03-24
great! :)

---

### Post by rustyhann on 2010-03-25
Thanks for the help :), I managed to get the workarounds to work on the testbed (an esxi box), but I didn't feel comfortable with them because when finals time rolls around, the students turn into wailing banshees when the render farm is down ;)

---

