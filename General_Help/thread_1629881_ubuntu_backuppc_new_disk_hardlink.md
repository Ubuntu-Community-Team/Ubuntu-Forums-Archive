---
title: "ubuntu backuppc new disk hardlink"
date: 2010-11-24
forum: General Help
---

### Post by ChrisRob300 on 2010-11-24
Hi


I have added a new disk and formatted it ext3 and ext4.
I have called it backup, and mounted it /backup
i have amended /etc/backuppcconfig.pl to point to /backup.
I have copied /var/lib/backuppc/* to /backup all as installed
config.pl as installed

hosts:
host        dhcp    user    moreUsers     # <--- do not edit this line        #farside    0       craig   jill,jeff     # <--- example static IP host entry #larson     1       bill                  # <--- example DHCP host entry      localhost   0       backuppc                                                                                                                                192.168.1.21    0       backuppc                                              192.168.1.22    0       backuppc                                              

/etc/init.d/backuppc restart
The error I get is can't create a test hardlink


--

Chris

---

### Post by dcstar on 2010-11-25
> **ChrisRob300 said:**
> 
........
The error I get is can't create a test hardlink


--

Chris

Hardlinks can only exist on the same physical filesystem.

---

### Post by dpesec on 2011-01-14
I'm having the same issue. I moved all the folders and files to an external USB drive. The only issue I can think of is that the USB drive is formatted for Window NTFS? Could this be an issue?

---

### Post by dpesec on 2011-01-14
I'm having the same issue. I moved all the folders and files to an external USB drive. The only issue I can think of is that the USB drive is formatted for Window NTFS? Could this be an issue?

---

### Post by dpesec on 2011-01-31
> **dcstar said:**
> Hardlinks can only exist on the same physical filesystem.

I understand this but I was able to manually create a hardlink. I'm totally confused now as to my backuppc doesn't work. It did before I went to 10.04

---

### Post by capps1994 on 2011-06-17
You need to change the backup config file in  /etc/backuppc/config.pl

code:
sudo nano /etc/backuppc/config.pl

Change $Conf{TopDir}      = '/var/lib/backuppc/';
To this $Conf{TopDir}      = '/path/to/file/';

then

you need to copy the contents of /var/lib/backuppc

so 

sudo cp -Rv /var/lib/backuppc /path/to/files

Then you need to change the permissons.

sudo chmod 777 /path/to/dir/
sudo chown backuppc.backupc /path/to/dir

Chris

---

