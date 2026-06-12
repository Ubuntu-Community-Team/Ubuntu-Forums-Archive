---
title: "NFS Install messes up server"
date: 2010-06-25
forum: General Help
---

### Post by Solignis on 2010-06-25
I need some help!

I am new to Linux and I am having a huge problem after install nfs-kernel-server. I run "apt-get install nfs-kernel-server"

It runs and says it installs without errors, at least what I saw. Also the syslog was clean of errors related.

Where the problem happens is when I try to start the NFS server and also on boot.

When I start the service manually, it says starting portmap and ...something else. Then it gets to the point of saying it is starting the NFS server and crashes and I have no prompt. On some cases I can break out of it with (ctrl+c).

The problem that happens on boot...and this is ONLY HAPPENS after nfs-kernel-server is installed. I reboot and I have no prompt. The only thing on the screen is a message complaining about something related to fsck, the odd thing is when I look to see if fsck has made any log outputs about fsck. When I cat the fsck log it says the log has no entries. The worst part is I have no way to log in from the console the machine gives me no prompt. What is going??

I know it is something related to NFS because I have reinstalled the machine and it work perfect until I install NFS.

---

### Post by bodhi.zazen on 2010-06-25
Check your logs for error messages.

could be anything from firewall settings to failure to configure nfs - have you configured any exports yet ?

Look in /var/log for error messages.

---

### Post by dca on 2010-06-25
You can try comparing what you've done so far to this how-to, seems pretty comprehensive:
 
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by Solignis on 2010-06-26
That is the guide I followed and it seemed easy enough. The thing that is wrong is all of this that I can't figure out is when I uninstall NFS the problems still exist/occur. I eventually had to reinstall the server. Everyday it seemed to get worse and worse, it was randomly kicking me out of putty and saying something about a network error. The fresh server minus NFS is solid.

If I was going to try this again I need to make a backup, any suggestions? I already have a backup of all of the NIC configs and my iscsi target. What more can I do?

Also I am running a bare version of Ubuntu Server 10.04. I did not willingly install a firewall or any extra software other than the following.

ifenslave (NIC Bonding)
iscsitarget (iSCSI target for my ESXi server)
lvm2 (already installed)
openssh-server (already installed)

---Update----

I am looking at the guide again. I was wondering if maybe trying to export an logical volumes would cause a problem.

I have just this one export I need.

/mnt/storage    10.0.0.1/8(rw,sync,no_root_squash,no_subtree_check)

The mount point is tied to /dev/vg1/vol1. I have not added it to fstab yet.

---

