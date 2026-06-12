---
title: "Samba Configuration"
date: 2010-05-30
forum: General Help
---

### Post by Bill555 on 2010-05-30
Problem Solved: 

I am using Ubuntu 10.4 LTS  and Samba3.4.7.
   
  I have read a lot of posts and different web pages on setting up Samba on a Peer-to-Peer network with Windows XP but just can’t make it work.
   
  I can see the Guest account in XP My Network Places but can’t access the folder when I click on it.   Network not accessible or you don’t have permission.
   
  I can PING both ways ok.  I have Firestarter turned OFF and I don’t have any third party firewall on XP.
   
  This is my samba config file:
   
  [global]
   
  netbios name = dolphin
  server string = Ubuntu
  workgroup = WATERLILLY      - same as XP
   
  interfaces = eth0 192.168.15.102/24
  bind interfaces only = true
   
  announce version = 4.9
   
  socket options =  TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE S0_RCVBUF=8192 SO_SNDBUF=8192
   
  security = share
   
  null passwords = true
   
  name resolve order = hosts wins bcast
  wins support = yes
  guest account = nobody
   
  [homes]
  browseable = no
  read only = yes
   
  [guest share]
   
   path = /guest
   browseable = yes
  read only = yes
  guest ok = yes
   
  I am very new at this and any help would be deeply appreciated.
  Bill

---

### Post by bakegoodz on 2010-05-30
I believe the problem is with linux file permissions on the shared folder. Set read and write permissions on group and other.

---

### Post by Bill555 on 2010-05-31
Thanks will have a second look at those permissions.

---

### Post by Bill555 on 2010-05-31
I found the problem:
This is my Samba Config:
[global]
    
    netbios name = DOLPHIN
    ;computer name
    server string = Ubuntu
    ;computer description
    workgroup = WATERLILLY
    ;same as windows workgroup]
    announce version = 4.9
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    security = share
    wins support = yes
    usershare owner only = False

    
[homes]

   comment = Home Directories
    browseable = no
    read only = yes
    
[Guest Share]

    comment = Guest access share
    path = /Guest
    browseable = yes
    read only = no
    guest ok = yes

I created a folder in ROOT called Guest and gave it full permissions and shared it.  I also have firestarter installed and had to allow the IP's of my two windows PC.

---

