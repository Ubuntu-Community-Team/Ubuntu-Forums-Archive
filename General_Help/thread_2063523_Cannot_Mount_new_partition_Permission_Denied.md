---
title: "Cannot Mount new partition Permission Denied"
date: 2012-09-27
forum: General Help
---

### Post by wt9bind on 2012-09-27
Hi,

I have a 1TB HDD that I use as my main drive in Ubuntu.

I partitioned 250GB of it and left the other 750GB Dormant until I required it, the time has come to partition it and use it to convert all of my kids cartoons from DVD to MP4 for our media player.

I created the partition as ext4 and all was good, i even copied data to it. I shut the server down and started it back up as I upgraded the RAM and now when I mount it in Disk Utility I get:
An error occurred while performing an operation on "Kids" (Partition 3 of ATA ST31000524AS): Permission Denied
[IMG]http://www.the-binghams.com/screen.jpg[/IMG]
[IMG]http://www.the-binghams.com/ErrorMount.jpg[/IMG]
Can anybody suggest what is going on? Also I can re-partition this section of drive if need be.

Thanks

---

### Post by oldfred on 2012-09-27
Please use paperclip icon in edit panel of new message to attach images. :)

You have to set permissions & ownership. And if permanent partition, best to edit fstab with exactly the permissions you want.

Details:
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Example:
from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6

For ext4 UUID is example, you must use your UUID :
```
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Kids ext4 defaults,noatime 0 2

```
** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example (actually does not have to be Kids as that is just label or you can use label to mount see details above):
sudo mkdir /media/Kids
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

---

### Post by wt9bind on 2012-09-27
Thanks for the reply, it appears to have worked and I can now access the drive, however I get this weird message.

In the GUI, if I click Places --> Computer, I can see my 3 Physical drives and then a kids drive, if I click it, says unable to mount kids /mount: /dev/sda3 already mount or /media/kids busy.

But then below amongst the likes of Home, Desktop, Documents etc. there is a kids disk that works properly there.

I don't know if this is a real problem or not though?

---

### Post by bab1 on 2012-09-27
> **wt9bind said:**
> Thanks for the reply, it appears to have worked and I can now access the drive, however I get this weird message.

In the GUI, if I click Places --> Computer, I can see my 3 Physical drives and then a kids drive, if I click it, says unable to mount kids /mount: /dev/sda3 already mount or /media/kids busy.

But then below amongst the likes of Home, Desktop, Documents etc. there is a kids disk that works properly there.

I don't know if this is a real problem or not though?

When you mount the partition via fstab the partition becomes mounted and part of the local filesystem.  When you go to "Places --> Computer, I can see my 3 Physical drives and then a kids drive", and click on it, you are attempting to mount it again.  No need to do that.  Looking for it via the local filesystem at /media/Kids is the correct way.

---

### Post by wt9bind on 2012-09-27
Excellent!

Thanks for all of your help guys, much appreciated.

Now to get my head around adding this to NFS Exports!

---

### Post by oldfred on 2012-09-27
Mounts in /home and /media will show twice. My work around has always been to mount in /mnt/Kids and then link each folder in that partition back into /home.

Or:

Duplicate mounts of partitions in Nautilus left panel
use /dev/disk/by-uuid/xxxxx...
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)

I really do not know NFS, but use some scripts to make mine work.

HOWTO: NFS Server/Client if no windows 
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)
Autofs mount directories on an as-needed basis.
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

---

### Post by bab1 on 2012-09-27
> **oldfred said:**
> Mounts in /home and /media will show twice. My work around has always been to mount in /mnt/Kids and then link each folder in that partition back into /home.

Or:

Duplicate mounts of partitions in Nautilus left panel
use /dev/disk/by-uuid/xxxxx...
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)

I really do not know NFS, but use some scripts to make mine work.

HOWTO: NFS Server/Client if no windows 
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)
Autofs mount directories on an as-needed basis.
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

I looked at the OP's reply a couple of times.  I wouldn't think that the OP needs NFS to mount to the local host.  More like it will be serving the exports to other hosts; yes?.  The exports would be for *other* hosts to mount these exports to their local file systems.

---

### Post by wt9bind on 2012-09-28
> **bab1 said:**
> I looked at the OP's reply a couple of times.  I wouldn't think that the OP needs NFS to mount to the local host.  More like it will be serving the exports to other hosts; yes?.  The exports would be for *other* hosts to mount these exports to their local file systems.

100% correct. Using NFS to be able to use it via my Mac. 

Shameless plug for any Mac users wanting to use NFS easily [http://www.bresink.com/osx/NFSManager.html]("http://www.bresink.com/osx/NFSManager.html")

---

### Post by isa.dsouza on 2012-11-25
> **oldfred said:**
> Please use paperclip icon in edit panel of new message to attach images. :)

You have to set permissions & ownership. And if permanent partition, best to edit fstab with exactly the permissions you want.

Details:
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Example:
from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6

For ext4 UUID is example, you must use your UUID :
```
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Kids ext4 defaults,noatime 0 2

```** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example (actually does not have to be Kids as that is just label or you can use label to mount see details above):
sudo mkdir /media/Kids
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

I could not find the commands to check the current permissions on my partitions. I have formatted my internal into ext4 and now when logged in as guest or even when booting from the live usb I cannot view the partition, It does not even mount. 

I did tick the take ownership check box when formatting in disk utility. I have the same issue with an external usb hard drive and a pen drive as well.

I must say that the data transfer rate is in excess of 32Mb/sec on ext4. This is a good way to secure data as well. I just want to be sure that in case my system crashes will I be able to recover the data?

I can see all data when logged in as admin, my guess is that a re-install of ubuntu would leave me with no permissions to view the partitions. Am I correct?

---

