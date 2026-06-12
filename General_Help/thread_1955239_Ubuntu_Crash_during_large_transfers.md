---
title: "Ubuntu Crash during large transfers"
date: 2012-04-09
forum: General Help
---

### Post by DanFTP on 2012-04-09
Hi all,
I am using Ubuntu 11.04 as a file server with a few external hdd's attached. On my office network I have gotten complaints that when users transfer large files (100 GB and up) to their office PC (Win7) the transfer is killed about half way through. I go to the server room and notice that the Ubuntu box is locked up with a black screen and the only way to correct it is with a hard reset. This problem doesn't occur with smaller transfers.  However this is sporadic. I have looked around on a bunch of forums which say to look in the var/log/messages for more information. I can't seem to locate the messages folder. I get into the log and see a bunch of files and folder but not that one. Any ideas of where to find that or how to diagnose this issue?

---

### Post by kimda on 2012-04-09
Have a look at dmesg and syslog logs they also log system messages. Another thing you could do is do a file transfer and monitor what is happening. A crash could be caused by a system running out of memory (for instance). It will use up the fysical memory and then swap. Another thing could be bad hardware (try to check memory with the memtest86+ tool - has to run a long time - 8 hours+)

---

### Post by DanFTP on 2012-04-09
I looked in that folder and found:
Rx/Tx
-bash: [: missing `]'
psi@ftp2:/var/log$ [   20.270823] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
-bash: syntax error near unexpected token `('
psi@ftp2:/var/log$ [   21.455953] CIFS: Unknown mount option umask
-bash: [: missing `]'
psi@ftp2:/var/log$ [   21.457676] CIFS: Unknown mount option umask
-bash: [: missing `]'
psi@ftp2:/var/log$ [   21.458677] CIFS VFS: cifs_mount failed w/return code = -11
-bash: [: missing `]'
psi@ftp2:/var/log$ [   30.447499] CIFS: Unknown mount option umask
-bash: [: missing `]'
psi@ftp2:/var/log$ [   30.676200] eth0: no IPv6 routers present
-bash: [: missing `]'
psi@ftp2:/var/log$ [  159.239814] CIFS VFS: Send error in SessSetup = -11
-bash: [: missing `]'
psi@ftp2:/var/log$ [  159.239821] CIFS VFS: cifs_mount failed w/return code = -112
-bash: [: missing `]'
psi@ftp2:/var/log$ [  159.239832] CIFS VFS: cifs_mount failed w/return code = -11
-bash: [: missing `]'

---

### Post by kimda on 2012-04-09
These errors indicate that that you are mounting some folder with cifs but it has mistakes in the command. Are you mounting some drive via fstab? Maybe an external drive?

---

### Post by DanFTP on 2012-04-09
Yes, that is correct I am mounting an external drive and folders from a windows share.

 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_bdhjcfdcba_ARRAY1 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_bdhjcfdcba_ARRAY5 none            swap    sw              0       0
#/dev/sdd1      /media/backups2 auto rw,noauto,user,sync 0 0
/dev/sdd1       /media/backups auto rw,noauto,user,sync 0 0
//192.168.1.203/customer /media/file2/customer cifs uid=1000,gid=1000,username=mkarnick,password=XXXXXXX,file_mode=0777,dir_mode=$
//192.168.1.203/psi /media/file2/psi cifs uid=1000,gid=1000,umask=777,username=mkarnick,password=XXXXXXX,user 0 0
//192.168.1.203/vm /media/file2/vm cifs uid=1000,gid=1000,umask=777,username=mkarnick,password=XXXXXXX,user,noperm 0 0
########//192.168.1.203/vm /media/file2/vm cifs gid=1000,umask=777,username=mkarnick,password=XXXXXXX,user 0 0

#UUID=F1F2-0D03         /media/backups3 auto rw,user,sync 0 0
/dev/sdc1       /media/software ext4 defaults 0 0
#UUID=E79A-BF54 /media/backups2 auto rw,user,sync 0 0
#UUID=F326-FDAE /media/backups1 auto rw,user,sync 0 0
#UUID=DEA8C110A8C0E85B /media/backups auto rw,user,sync 0 0
UUID=B698A21B98A1D9DF /media/backups auto rw,user,sync 0 0
#UUID=E0A63B94A63B6A64 /media/ftpbackups_backup auto rw,user,sync 0 0

---

### Post by kimda on 2012-04-09
Check the fstab mounts (password is not with a space between pass and word ofr example). Also the option umask for cifs doesn't exist. Check the cifs mount options to make files with certain permissions.

---

### Post by DanFTP on 2012-04-09
I will check that but I'm just wondering why it works on transfers under 10GB but going over that gets the system to hang up and black screen.

---

### Post by kimda on 2012-04-10
It shouldn't crash because of these errors in the fstab file. 
I think its hardware related. Check the logs for error messages and check hardware. Maybe swap some hardware like networkcard, memory and see if it changes things. Another thing what you could do is load another kernel and see it fit changes things.

---

### Post by dcstar on 2012-04-10
> **DanFTP said:**
> Yes, that is correct I am mounting an external drive and folders from a windows share.

 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_bdhjcfdcba_ARRAY1 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_bdhjcfdcba_ARRAY5 none            swap    sw              0       0
#/dev/sdd1      /media/backups2 auto rw,noauto,user,sync 0 0
/dev/sdd1       /media/backups auto rw,noauto,user,sync 0 0
//192.168.1.203/customer /media/file2/customer cifs uid=1000,gid=1000,username=mkarnick,password=XXXXXXX,file_mode=0777,dir_mode=$
//192.168.1.203/psi /media/file2/psi cifs uid=1000,gid=1000,umask=777,username=mkarnick,password=XXXXXXX,user 0 0
//192.168.1.203/vm /media/file2/vm cifs uid=1000,gid=1000,umask=777,username=mkarnick,password=XXXXXXX,user,noperm 0 0
########//192.168.1.203/vm /media/file2/vm cifs gid=1000,umask=777,username=mkarnick,password=XXXXXXX,user 0 0

#UUID=F1F2-0D03         /media/backups3 auto rw,user,sync 0 0
/dev/sdc1       /media/software ext4 defaults 0 0
#UUID=E79A-BF54 /media/backups2 auto rw,user,sync 0 0
#UUID=F326-FDAE /media/backups1 auto rw,user,sync 0 0
#UUID=DEA8C110A8C0E85B /media/backups auto rw,user,sync 0 0
UUID=B698A21B98A1D9DF /media/backups auto rw,user,sync 0 0
#UUID=E0A63B94A63B6A64 /media/ftpbackups_backup auto rw,user,sync 0 0

**/media is a System Folder** for exclusive use of the system for mounting removable devices, **it is not for users to use** for mount points. Things like Nautilus uses /mount on the assumption that it has total control of that folder. Put them in /mnt or another totally separate folder.

This may not have anything to do with your issue, but by using /media you have introduced an unnecessary variable into the equation.

Large file transfers may load you CPU and it could be that the system overheats and causes the lockups. Instal lm-sensors and check the CPU temps.

---

### Post by DanFTP on 2012-04-10
> **kimda said:**
> Check the logs for error messages and check hardware. 

I am new to Linux and taking over for the previous admin. I can't seem to find the logs? When I go to the place where the logs should be located, looking for "messages" this is what I find. When I try to open these I get the error that the file doesn't exist or it is very unreadable.

alternatives.log       dpkg.log               samba
alternatives.log.1     dpkg.log.1             speech-dispatcher
alternatives.log.2.gz  dpkg.log.2.gz          syslog
apache2                faillog                syslog.1
apparmor               fontconfig.log         syslog.2.gz
apt                    fsck                   syslog.3.gz
auth.log               gdm                    syslog.4.gz
auth.log.1             installer              syslog.5.gz
auth.log.2.gz          jockey.log             syslog.6.gz
auth.log.3.gz          jockey.log.1           syslog.7.gz
auth.log.4.gz          kern.log               sysstat
boot                   kern.log.1             udev
boot.log               kern.log.2.gz          ufw.log
bootstrap.log          kern.log.3.gz          unattended-upgrades
btmp                   kern.log.4.gz          vsftpd.log
btmp.1.gz              lastlog                vsftpd.log.1.gz
ConsoleKit             mail.err               vsftpd.log.2.gz
cups                   mail.log               vsftpd.log.3.gz
dist-upgrade           news                   vsftpd.log.4.gz
dmesg                  pm-powersave.log       wtmp
dmesg.0                pm-powersave.log.1     wtmp.1.gz
dmesg.1.gz             pm-powersave.log.2.gz  Xorg.0.log
dmesg.2.gz             pm-powersave.log.3.gz  Xorg.0.log.old
dmesg.3.gz             pm-powersave.log.4.gz  Xorg.1.log
dmesg.4.gz             pycentral.log          Xorg.1.log.old

---

### Post by kimda on 2012-04-10
Any error messages in dmesg and syslog? You can also check dmesg with the following command:
```
dmesg
``` 

If you want to scroll through dmesg pipe output to less like this: 
```
dmesg | less
``` Or you can go to the /var/log and ```
less dmesg
```.

---

### Post by DanFTP on 2012-04-10
It looks like I have it narrowed down to samba crashing during these transfers. I used an FTP client Filezilla bypassing samba and the 100 gb transfer worked perfectly. Does this also rule out the network card. I am trying to view the samba logs and this is what I get:
psi@ftp2:/var/log/samba$ cat log.smbd
**2:30 is when I restarted it yesterday**
[2012/04/09 14:27:09,  0] smbd/server.c:1123(main)
  smbd version 3.5.8 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2012/04/09 14:27:09.779272,  1] param/loadparm.c:6494(map_parameter)
  Unknown parameter encountered: "refresh"
[2012/04/09 14:27:09.779281,  0] param/loadparm.c:7588(lp_do_parameter)
  Ignoring unknown parameter "refresh"
[2012/04/09 14:27:09.781291,  1] param/loadparm.c:6494(map_parameter)
  Unknown parameter encountered: "refresh"
[2012/04/09 14:27:09.781309,  0] param/loadparm.c:7588(lp_do_parameter)
  Ignoring unknown parameter "refresh"
**12:30 is when I restarted it today. It doesn't seem to be telling me much**
[2012/04/10 12:30:59,  0] smbd/server.c:1123(main)
  smbd version 3.5.8 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2012/04/10 12:30:59.303684,  1] param/loadparm.c:6494(map_parameter)
  Unknown parameter encountered: "refresh"
[2012/04/10 12:30:59.303693,  0] param/loadparm.c:7588(lp_do_parameter)
  Ignoring unknown parameter "refresh"
[2012/04/10 12:30:59.305770,  1] param/loadparm.c:6494(map_parameter)
  Unknown parameter encountered: "refresh"
[2012/04/10 12:30:59.305786,  0] param/loadparm.c:7588(lp_do_parameter)
  Ignoring unknown parameter "refresh"

Still drawing a blank. Any ideas?

---

### Post by kimda on 2012-04-10
You can check the smb.conf file with the command testparm to see if there are any errors in the config file. Another thing what you could do is increase the log level in smb.conf. Then you will get bigger logs, but they will give you some more information about what is going on.

---

### Post by DanFTP on 2012-04-11
This is the entire smb.conf The drive that fails is called backup


[global]
    ; General server settings
    netbios name = ftp2
    server string = PSI Samba Server
    workgroup = PSI
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    refresh = 1
    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
 path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes


;[customer]
 ;   writeable = yes
  ;  path = /media/file2/customer
  ;  browseable = yes
 ;   read only = no
;   guest ok = yes
 ;   create mask = 0644
 ;   directory mask = 0755
 ;   force user = psi
 ;   force group =  psi
 ;   comment = Customer Share on FILE2

[backups]
    writeable = yes
    path = /media/backups
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = psi
    force group =  psi
    comment = Backups1 - 2TB USB External (Westernal Digital)
;[backups2]
;       writeable = yes
 ;   path = /media/backups2
  ;  browseable = yes
   ; read only = no
   ; guest ok = yes
   ; create mask = 0644
   ; directory mask = 0755
   ; force user = psi
   ; force group =  psi
   ; comment = Backups2 - 200GB External (Grey Maxtor Laying Flat)

;[backups3]
;       writeable = yes
;    path = /media/backups3
;    browseable = yes
;    read only = no
;    guest ok = yes
;    create mask = 0644
;    directory mask = 0755
;    force user = psi
;    force group =  psi
;   comment = Backups3 - 750GB USB External (Black/Grey Maxtor Stand-up)
[software]
        path = /media/software
        writeable = yes
        browseable = yes
        read only = no
        guest ok = yes
        create masl = 0644
        directory mask = 0755
        force user = psi
        force group = psi
        comment = Software Share

[wwwfiles]
        path = /media/wwwfiles
        writeable = yes
        browseable = yes
        read only = no
        guest ok = yes
        create masl = 0644
        directory mask = 0755
        force user = psi
        force group = psi
        comment = Location for sending customers links to large files

[customerFTP]
    writeable = yes
    path = /media/customerFTP
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = psi
    force group =  psi
    comment = Folder containing all Customer Specific FTP folders for 2 way file transfer

;[backups]
;    writeable = yes
;    path = /media/backups
;    browseable = yes
;    read only = no
;    guest ok = yes
;    create mask = 0644
;   directory mask = 0755
;   force user = psi
;   force group =  psi
;   comment = Backups - 3TB USB External (Seagate)

---

### Post by kimda on 2012-04-12
I saw that you have two lines in fstab to /media/backups. One with /dev/sdd1 and one with a UUID entry. I would comment out one of these entries so that you have only one pointing to /media/backups. 

Also have you tried switching the external harddrive to another usb port on the machine? Try copying stuff to this harddrive directly from the commandline/gui on the server to see if its working correctly. If you connect a different external harddrive to the machine on the same share does it give the same behavior? 

> **DanFTP said:**
> This is the entire smb.conf The drive that fails is called backup

[backups]
    writeable = yes
    path = /media/backups
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = psi
    force group =  psi
    comment = Backups1 - 2TB USB External (Westernal Digital)


---

