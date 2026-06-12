---
title: "Help with mounting an NTFS volume"
date: 2009-09-19
forum: General Help
---

### Post by Redbomber on 2009-09-19
I have a secondary 250GB HDD that has all of my docs and apps from when I used Windows (still have a duel boot).  I set up sharing of this volume, and was able to access it via my notebook with Windows 7.  So that was all good.

Then, I thought, it was a bit annoying having to manually click Places>250GB Media every time I wanted to access this over the network, so followed a thread to auto-mount this volume.  This involved installing NTFS-Config, and using that.  It auto-mounted the volume, but then I couldn't access it over the network anymore.  I think it may have had something to do with the mount point, even though I edited smb.conf to reflect the change.  Most annoying is that it has removed my privileges to mount and unmount the volume.  Is someone able to assist me to

i) Get my privileges back, and
ii) Have this auto mounted and be able to access it over the network?

Here is the contents of fstab, which from what I have found already, may need to be editied to fix this?

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=6ae06a71-29ee-4cd0-bff5-cb4e3c146ff9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ef21dbcd-0136-4376-abae-526573a5076f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /media/Data ntfs-3g defaults,locale=en_AU.UTF-8 0 0
```

Help appreciated.

---

### Post by SoftwareExplorer on 2009-09-19
I think if you change the line ```
/dev/sdb1 /media/Data ntfs-3g defaults,locale=en_AU.UTF-8 0 0
``` in fstab to ```
/dev/sdb1 /media/Data ntfs-3g defaults,user,auto,locale=en_AU.UTF-8 0 0
```
(notice I added the user and auto options)

Also, Samba might not let you share folders that you don't own. So, could you post smb.conf and the result of ```
ls -l /media
``` 
Thanks.

---

### Post by Redbomber on 2009-09-19
I changed the line you suggested.  I still don't have privileges to change unmount or mount using the GUI, nor can I access shares.  Here is the smb.conf:

```
[global]
    ; General server settings
    netbios name = SERVER
    server string =
    workgroup = BAKER
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

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

[MyFiles]
    path = /media/data
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = baker
    force group = baker
```

And 

```
baker@server:~$ ls -l /media
total 12
lrwxrwxrwx 1 root root    6 2009-08-16 22:50 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-08-16 22:50 cdrom0
drwxrwxrwx 1 root root 8192 2009-09-19 16:25 Data
baker@server:~$ 
```

---

### Post by DeMus on 2009-09-19
> **Redbomber said:**
> I have a secondary 250GB HDD that has all of my docs and apps from when I used Windows (still have a duel boot).  I set up sharing of this volume, and was able to access it via my notebook with Windows 7.  So that was all good.

Then, I thought, it was a bit annoying having to manually click Places>250GB Media every time I wanted to access this over the network, so followed a thread to auto-mount this volume.  This involved installing NTFS-Config, and using that.  It auto-mounted the volume, but then I couldn't access it over the network anymore.  I think it may have had something to do with the mount point, even though I edited smb.conf to reflect the change.  Most annoying is that it has removed my privileges to mount and unmount the volume.  Is someone able to assist me to

i) Get my privileges back, and
ii) Have this auto mounted and be able to access it over the network?

Here is the contents of fstab, which from what I have found already, may need to be editied to fix this?

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=6ae06a71-29ee-4cd0-bff5-cb4e3c146ff9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ef21dbcd-0136-4376-abae-526573a5076f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /media/Data ntfs-3g defaults,locale=en_AU.UTF-8 0 0
```

Help appreciated.


I have always used this and wrote it here several times in the forum for others:

**[SIZE="4"]Auto mount Windows disks[/SIZE]**
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have **NO** drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

---

### Post by Redbomber on 2009-09-19
> **DeMus said:**
> I have always used this and wrote it here several times in the forum for others:

**[SIZE="4"]Auto mount Windows disks[/SIZE]**
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have **NO** drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

This is exactly the instructions that I used.  This issue is that once I did that, I was unable to access the network share.

---

### Post by Redbomber on 2009-09-24
Anyone?  Surely I don't have t reload the PC in order to get my permissions to the 250Gb drive back?

---

