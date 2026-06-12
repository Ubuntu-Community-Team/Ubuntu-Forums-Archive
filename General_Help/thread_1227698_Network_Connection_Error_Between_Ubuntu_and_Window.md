---
title: "Network Connection Error Between Ubuntu and Windows PC"
date: 2009-07-31
forum: General Help
---

### Post by aramshiro on 2009-07-31
Hi guys i just want to ask how can i view and access other pc in my windows work group. I already installed samba then although is a success but theres some problem i encounter. I can only access pc's in my workgroup where ubuntu joined. Although other work group is visible but if i click other work group i can't see other pc who are join in that work group so can you teach me what should i do for that.

Ex. The workgroup that my ubuntu pc was join is MIS DEPT then all pc's who are in that workgroup is accessible but if i try to click other workgroup like MARKETING DEPT i cant see pc's who are join in that workgroup

Thx

---

### Post by running_rabbit07 on 2009-07-31
You have to create a user account with the other windows PCs. From what I have been reading in my Network+ Manual is that you may have to install Samba on the Windows machines, too.

Edit:I had to remove screenshots because they are copyrighted.

---

### Post by aramshiro on 2009-07-31
Thx Rabbit. By d way how can i install samba in a windows pc and where can i get the installer  samba for windows pc's. thx for the help i will try what u say.

---

### Post by running_rabbit07 on 2009-07-31
[I just did a quick google search and this was the first listing.]("http://us3.samba.org/samba/")

---

### Post by aramshiro on 2009-07-31
Hellow rabbit, so if im using windows 98 and windows xp what samba should i use that is compatible w/ that Operating System and what Version is easy to use and easy to handle for that situation

---

### Post by running_rabbit07 on 2009-07-31
> **aramshiro said:**
> Hellow rabbit, so if im using windows 98 and windows xp what samba should i use that is compatible w/ that Operating System and what Version is easy to use and easy to handle for that situation

I haven't messed with them yet myself. As is obvious, Samba is quite easy for Ubuntu/Linux but from what I have read, it is a pain in the posterior to set up on Windows. I do plan to try it on my wife's system being that when I drag files from her system to mine while using her system it sets the permissions to where I can read only.

---

### Post by aramshiro on 2009-08-01
Okie. By d way I will tell you my situation.  In our office we are using windows operating system (Windows 98 & Windows Xp) We have a good network connection for both 98 and Xp. Now we try to Install ubuntu in 1 pc. Because we want to try it to be our server pc because as i heared from others  for now there are no viruses developed yet in ubuntu so we want to try it for our safety. Now the problem is that when i using our windows base computer we have access in all network group also we can access file from the ubuntu pc, but when i using ubuntu pc to access files from other network group, there i encounter some problem. Its like this when i open my windows network i see all the workgroup but if i double click one of my workgroup to see other pc who are connected in dat work group i cant see anything. So dats what i want to solve. Im sry because im just a bigginer. I really apriciate your help. thx alot.

  BY D WAY THIS IS MY CONFIGURATION. PLS TELL ME IF THERE'S SOMETHING I MUST TO CHANGE OR TO PUT ANOTHER CONFIG. 

[global]
    ; General server settings
    netbios name = Dbaseserveru
    server string =  %h (Ubuntu)
    workgroup = MIS Department
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

[MyFiles]
  comment = read and write
  path = /home/samba
  available = yes
  browsable = yes
  public = yes
  writable = yes
  create mask = 0700
  directory mask = 0755
  force user = nobody
  force group = nogroup

    ;path = /home/samba/
   ; browseable = yes
   ; read only = no
   ; guest ok = no
   ; create mask = 0644
   ; directory mask = 0755
   ; force user = nobody
   ; force group = nogroup

[D]
  comment = read and write
  path = /home/samba
  available = yes
  browsable = yes
  public = yes
  writable = yes
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup

[documents]
  comment = read and write
  path = /home/samba
  available = yes
  browsable = yes
  public = yes
  writable = yes
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup

---

### Post by lisati on 2009-08-01
> **running_rabbit07 said:**
> You have to create a user account with the other windows PCs. From what I have been reading in my Network+ Manual is that you **may** have to install Samba on the Windows machines, too.

Edit:I had to remove screenshots because they are copyrighted.

I've never had to install samaba on my Windows machines to get them "talking" with my Ubuntu installations.

Have a look here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by running_rabbit07 on 2009-08-01
> **lisati said:**
> I've never had to install samaba on my Windows machines to get them "talking" with my Ubuntu installations.

Have a look here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

That is a great tutorial. It explains everything needed. I am definitely saving it for future use. Thanx.

---

