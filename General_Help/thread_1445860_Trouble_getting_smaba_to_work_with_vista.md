---
title: "Trouble getting smaba to work with vista"
date: 2010-04-03
forum: General Help
---

### Post by watersa8 on 2010-04-03
Hey I've not used ubuntu in a while and am having a bit of difficulty connecting to my laptop which i use as a mule for downloading i currently dual boot my desktop with xp so know that i can access it in that but for some reason it doesn't seem to want to let me connect through linux

Here's my smb.conf file

[global]
    ; General server settings
    netbios name = watersa8-desktop
    server string = watersa8-desktop
    workgroup = HOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

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
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = watersa8
    force group = watersa8

I did check it over with the guide available here
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
but still to no avail is there specific issues surrounding vista im not aware of as ive only ever set up a home network between ubuntu and xp

---

### Post by CharlesA on 2010-04-03
Check here: [http://blogs.zdnet.com/Bott/?p=237](http://blogs.zdnet.com/Bott/?p=237)

---

### Post by Morbius1 on 2010-04-03
Your netbios name is one character too long. If must be 15 characters or less. Try to change the following line in smb.conf:
```
     netbios name = watersa8-desktop
```

To say....
```
     netbios name = watersa8-dtop
```

Then restart samba: **sudo service samba restart**

See if that works.

---

### Post by watersa8 on 2010-04-03
Hey sorry i accidently double posted 
[http://ubuntuforums.org/showthread.php?p=9070581&posted=1#post9070581](http://ubuntuforums.org/showthread.php?p=9070581&posted=1#post9070581)
please reply here

and no sadly that didnt help i can get as far as seeing the home workgroup through network but when i try double clicking on it i get "Unable to mount location "\n" Failed to retrieve share list from server" as an error message

---

### Post by Morbius1 on 2010-04-03
Can the other machine access the share by ip address.

In Nautilus type **smb://192.168.0.100** for example.

Or even more directly: **smb://192.168.0.100/Share_name**

---

### Post by garvinrick4 on 2010-04-03
I have mine set up with a Windows Workgroup and samba. As long as I shared what I wanted in Windows and I had to set a user password to log-in with in windows both in
Vista and 7. Without user password to log in with it did not work. Karmic and Lucid both are
seen in Workgroup with samba. Version below.

ick@rick-laptop:~$ aptitude show samba
Package: samba
State: installed
Automatically installed: no
Version: 2:3.4.7~dfsg-1ubuntu1
Priority: optional
Section: net
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 18.4M
Depends: samba-common (= 2:3.4.7~dfsg-1ubuntu1), libwbclient0 (=
         2:3.4.7~dfsg-1ubuntu1), libacl1 (>= 2.2.11-1), libattr1 (>= 2.4.41-1),
         libc6 (>= 2.8), libcap2 (>= 2.10), libcomerr2 (>= 1.01), libcups2 (>=
         1.4.0), libgnutls26 (>= 2.7.14-0), libgssapi-krb5-2 (>= 1.7dfsg~beta1),
         libk5crypto3 (>= 1.6.dfsg.2), libkrb5-3 (>= 1.7dfsg~alpha1),
         libldap-2.4-2 (>= 2.4.7), libpam0g (>= 0.99.7.1), libpopt0 (>= 1.15),
         libtalloc2 (>= 2.0.0), zlib1g (>= 1:1.1.4), debconf (>= 0.5) |
         debconf-2.0, upstart-job, libpam-runtime (>= 1.0.1-11), libpam-modules,
         lsb-base (>= 3.2-13), procps, update-inetd, adduser
Recommends: logrotate

---

