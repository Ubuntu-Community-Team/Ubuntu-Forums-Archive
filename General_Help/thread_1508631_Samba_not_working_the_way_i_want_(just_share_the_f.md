---
title: "Samba not working the way i want (just share the files!)"
date: 2010-06-13
forum: General Help
---

### Post by Istrebitel on 2010-06-13
Greetings.

I am having a network at home with my Linux pc and a Windows pc. I want files to be accessible. My main pc holds some TB of music, videos etc and i want them to be shared to watch them from other pc. 

I heard samba does the trick. I used guides and successfully set it up. Unfortunately, it wont do what i want it to do.

I want all my NTFS drives available over the network. They are mounted by Ubuntu disk utility, that means, mountpoints are owned by my user and chmod is 0700 and i cannot change it anyhow (if i do chmod on it it has no effect!)
They look like this:

istrebitel@istrebitel-tux:/media$ ls -l
total 40
lrwxrwxrwx 1 root       root           7 2010-06-08 23:49 floppy -> floppy0
drwxr-xr-x 2 root       root        4096 2010-06-08 23:49 floppy0
drwx------ 1 istrebitel istrebitel  4096 2010-06-09 10:23 &#1055;&#1088;&#1080;&#1082;&#1083;&#1072;&#1076;&#1085;&#1086;&#1081; &#1052;&#1086;&#1079;&#1075;&#1086;&#1089;&#1086;&#1089;
drwx------ 1 istrebitel istrebitel  4096 2010-06-06 13:48 &#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1085;&#1099;&#1081; &#1040;&#1092;&#1077;&#1088;&#1080;&#1089;&#1090;
drwx------ 1 istrebitel istrebitel 16384 2010-06-13 14:57 &#1061;&#1091;&#1081; &#1042;&#1086;&#1076;&#1086;&#1074;&#1086;&#1079;&#1085;&#1099;&#1081;
drwx------ 1 istrebitel istrebitel 12288 2010-06-08 18:56 &#1063;&#1090;&#1086; &#1079;&#1072; &#1060;&#1080;&#1082;&#1091;&#1089;!?

Since i dont want it to bugger me with password inquiries, i've set "security=share" but now i cannot access my drives because Disk utility of Ubuntu makes them 0700 and thus only my user can access them. My samba config file is like this:

```
[global]
    ; General server settings
    netbios name = dom-tux
    server string =
    workgroup = STRONGHOLD
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
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

[Samba]
    path = /home/samba
    browseable = yes
    read only = yes
    guest ok = yes
    guest only = yes
    guest account = ftp   
    create mask = 0644
    directory mask = 0755
    ;force user = YOUR_USERNAME
    ;force group = YOUR_USERGROUP

[Media]
    path = /media
    browseable = yes
    read only = yes
    guest ok = yes
    guest account = ftp
    create mask = 0644
    directory mask = 0755

```

even if i do "guest account = istrebitel" or "guest account = root" it WONT help!

Does anyone have a clue how to make it work? I want my files (owned by istrebitel with 0700) be available w/o password over network.

---

### Post by Istrebitel on 2010-06-13
the only way i found was to move the guest account=ftp to the top and replacethat with my user name. But i feel i am compromising my system by that.

---

### Post by Morbius1 on 2010-06-13
You have an unnecessarily complicated smb.conf for what you want to do ( all guest access shares ) but here's the problem with the NTFS partitions:

You can't chown or chmod a windows filysystem ( NTFS or FAT32 ). You can change ownership or permissions only on a mount or through fstab but you can work around this problem by doing the following:
Change this:
> [Media]
    path = /media
    browseable = yes
    read only = yes
    guest ok = yes
    guest account = ftp
    create mask = 0644
    directory mask = 0755To this:
> [Media]
     path = /media
     browseable = yes
     read only = yes
     guest ok = yes
     [COLOR=Blue]#[/COLOR]guest account = ftp
[COLOR=Blue]force user = istrebitel[/COLOR]
     create mask = 0644
     directory mask = 0755Then restart samba.

"force user" will act as a mask ( for that share ) and convert the remote user to the only person who has access to those partitions and that's istrebitel. 

Oh and you need to reset "security = share" back to "security = user".

---

