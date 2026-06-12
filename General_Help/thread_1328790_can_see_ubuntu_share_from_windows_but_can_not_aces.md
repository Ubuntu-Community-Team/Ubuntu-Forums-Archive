---
title: "can see ubuntu share from windows but can not acess them"
date: 2009-11-16
forum: General Help
---

### Post by chrismitt2002 on 2009-11-16
can see ubuntu share from windows but can not acess them here is a copy of my samba setup

[global]
; General server settings
netbios name = intel-quad
server string =
workgroup = MSHOME
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



;[homes]
;valid users = %S
;create mode = 0600
;directory mode = 0755
;browseable = no
;read only = no
;veto files = /*.{*}/.*/mail/bin/



;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
;read only = no


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


[D-931gb]
path = /home/owner/D-931gb/
browseable = yes
ready only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = owner

[E-931gb]
path = /home/owner/E-931gb/
browseable = yes
ready only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = owner

[F-931gb]
path = /home/owner/F-931gb/
browseable = yes
ready only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = owner

[G-931gb]
path = /home/owner/G-931gb/
browseable = yes
ready only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = owner

[H-931gb]
path = /home/owner/H-931gb/
browseable = yes
ready only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = owner

[I-931gb]
path = /home/owner/I-931gb/
browseable = yes
ready only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = owner

[J-931gb]
path = /home/owner/J-931gb/
browseable = yes
ready only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = owner

i can mount and acess windows shares from ubuntu 910 to xp but not from xp to ubuntu in virutual box i can see the ubuntu shares but i get path not found i was getting this error but it suddenly went away Multiple connections to a server or shared resource by the same user, using more than one user name, are not allowed. Disconnect all previous connections to the server or shared resource and try again.

---

### Post by chrismitt2002 on 2009-11-30
bump

---

### Post by chrismitt2002 on 2009-11-30
plez someone plez help i have no clue how to fix this problem

---

### Post by zaphod777 on 2009-11-30
I also have this same issue I just haven't gotten around to hunting down a solution. let me see what I can find.

---

### Post by zaphod777 on 2009-11-30
I was able to get it to work by unticking guest access on the share and then it prompted for credentials and I could access.

---

### Post by jamesisin on 2009-11-30
I ran into this and found it was a permissions issue:

[http://ubuntuforums.org/showthread.php?p=8409281#post8409281](http://ubuntuforums.org/showthread.php?p=8409281#post8409281)

That should solve it (including providing guest access).

---

### Post by zaphod777 on 2009-11-30
what permissions did you need to change for guest access?

---

### Post by jamesisin on 2009-11-30
From rw - - to rw r r is what I am using.

---

