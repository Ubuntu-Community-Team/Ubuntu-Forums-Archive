---
title: "Win7 to Samba"
date: 2011-03-12
forum: General Help
---

### Post by kalebr on 2011-03-12
Hi all,

I'm having trouble setting up a samba share that I can access from my Win7 machine.  I attached an external usb drive to my linux box that I want to share with fairly open permissions to do automated backups to.  I can read from the share, but cannot write to it.  

The in my config, the external drive partition is /dev/sdb2 formatted as FAT32.  I mounted it with the command: ```
mount -o rw /dev/sdb2 /mnt/usbdrive/
```  I mention this because when I try to chmod the mount point, it doesn't change.  

```
robbie@ubu-kalebr:~$ ls -l /mnt/
total 16
drwxr-xr-x 2 root root 16384 1969-12-31 19:00 usbdrive
robbie@ubu-kalebr:~$ sudo chmod +w /mnt/usbdrive/
robbie@ubu-kalebr:~$ ls -l /mnt/
total 16
drwxr-xr-x 2 root root 16384 1969-12-31 19:00 usbdrive


```

Here is testparm output.
```

robbie@ubu-kalebr:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[backup]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = bcast host lmhost wins
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[homes]
        comment = Home Directories
        guest ok = Yes
        browseable = No
        browsable = No

[backup]
        comment = Backup USB Drive
        path = /mnt/usbdrive
        read only = No
        guest ok = Yes

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No
        browsable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers


```

At this point, I'm at a loss.  Any help would be appreciated.

thanks,

robbie

---

### Post by cap10Ibraim on 2011-03-12
I don't know if you like to use the terminal , but basically you can right click the folder and select share ( which is a samba share)

---

