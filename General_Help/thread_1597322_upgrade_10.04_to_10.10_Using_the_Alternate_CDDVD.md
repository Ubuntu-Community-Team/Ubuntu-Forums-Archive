---
title: "upgrade 10.04 to 10.10 Using the Alternate CD/DVD"
date: 2010-10-15
forum: General Help
---

### Post by behzadsh on 2010-10-15
hi,

I have a problem with upgrading from alternative CD...

I followed [https://help.ubuntu.com/community/MaverickUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD](https://help.ubuntu.com/community/MaverickUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD). but the upgrade dialog is not displayed even when I run
```

gksu "sh /media/cdrom/cdromupgrade"

```

---

### Post by dino99 on 2010-10-15
workaround: add your cdrom to synaptic repo tab, then update

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Bobi86 on 2011-01-22
Hi all,
I have been using ubuntu 8.10 and now i have upgraded to 9.04.
I want to upgrade it to 10.04 LTS. I have both 9.10 and 10.04  CD obtained from ubuntu.

But when i insert the 9.10 into CD drive, the message notifier is not showing any pop ups prompting for updates/upgrades, even when i use this command
gksu "sh /media/cdrom/cdromupgrade"But I'm able to access the disk contents in the CDROM, going to PLACES menu.

When i tried adding the CD to the repositories as mentioned above, the CD is not getting detected.
I don't wish to upgrade over the network with my extremely slow connection.

When i tried adding the CDROM using commands(surfed from net) i get the following error.
root@ubuntu:~# apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
E: Failed to mount the cdrom.
root@ubuntu:~# 

Kindly help me out upgrading to the later version of the Ubuntu using the CD rom.

Thanks and Regards,
Bobi

---

### Post by theozzlives on 2011-01-22
Are you sure it's a good burn? Did you run a MD5SUM?

---

### Post by andymorton on 2011-01-22
> **Bobi86 said:**
> Hi all,
I have been using ubuntu 8.10 and now i have upgraded to 9.04.
I want to upgrade it to 10.04 LTS. I have both 9.10 and 10.04  CD obtained from ubuntu.

But when i insert the 9.10 into CD drive, the message notifier is not showing any pop ups prompting for updates/upgrades, even when i use this command
gksu "sh /media/cdrom/cdromupgrade"But I'm able to access the disk contents in the CDROM, going to PLACES menu.

When i tried adding the CD to the repositories as mentioned above, the CD is not getting detected.
I don't wish to upgrade over the network with my extremely slow connection.

When i tried adding the CDROM using commands(surfed from net) i get the following error.
root@ubuntu:~# apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
E: Failed to mount the cdrom.
root@ubuntu:~# 

Kindly help me out upgrading to the later version of the Ubuntu using the CD rom.

Thanks and Regards,
Bobi

Hi Bob, 

I've never actually heard of anyone upgrading Ubuntu using a CD without doing a fresh install. You could put your home directory on a separate partition so you don't lose your files and settings and then install from the CD. 

andy :)

---

### Post by theozzlives on 2011-01-22
> **andymorton said:**
> Hi Bob, 

I've never actually heard of anyone upgrading Ubuntu using a CD without doing a fresh install.

I've done it a million times with the alternate CD. However, I recommend a separate /home and a fresh install. Go [here]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/") to move your /home to it's own partition.

---

### Post by Bobi86 on 2011-01-22
Hi Theozzlives,
      I have obtained the CD from canonical. When i tried running MD5 check,
I got the following error.
"The file integrity cannot be checked
You do not have required permissions to use this disk"

Moreover i faced the same problem when upgrading from ubuntu 8.10 to 9.04 using CD, then i upgraded using network which took 1 complete day. I don't wish that to happen.

FYI: I'm trying to upgrade from the root login.
During the previous upgrade i got an error related to linux-image.

Hi Andy,
    Forgive me, i don't get the context of your reply. can you please elaborate a little bit

---

