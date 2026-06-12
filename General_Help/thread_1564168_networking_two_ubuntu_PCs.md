---
title: "networking two ubuntu PCs"
date: 2010-08-30
forum: General Help
---

### Post by princeofnam on 2010-08-30
I previously used SSH to communicate  between my two ubuntu PCs, but my new internet connection is far too slow for this method.  Is there someway I can directly communicate between my two PCs using the router. Samba?

moreover, my ip seems to be dyanamic through my internet, how can i change it to static? or will it not matter for Local area connections?

---

### Post by lmarmisa on 2010-08-30
Are your two PCs connected to the same LAN (local area network)?.

Samba/CIFS is a very good and safe protocol for sharing files between both PCs.

---

### Post by princeofnam on 2010-08-30
yes they are. i believe i already have samba installed actually. it must have come with 10.04.  before when I opened up "Networks" I could see my own PC and "Windows Network
" but now i see nothing but windows and when i double click it i get "unable to mount location. failed to retrieve share list from server"

---

### Post by lmarmisa on 2010-08-30
If both computers are connected to the same LAN, they do not need Internet for the communication between them. So, it sounds  stranger your comment about the too slow connection. Are you using Ethernet and some router/switch in your LAN?. Standard speed for such type of LANs is 100/1000 Mbps. So, this is really fast.

In relation with Samba, check if the packages samba and system-config-samba are installed in the PC that you want to play the server role. Use the package manager System -> Administration -> Synaptic for this purpose.

After this installation you will be able to configure your Samba server selecting System -> Administration -> Samba.

---

### Post by zaphod777 on 2010-08-30
just right click on a folder and select share.
If samba isn't installed it will give you the option to install it. 

For me it kept giving me errors when I tried accessing the folder so I manually needed to add the share entry to the bottom of the /etc/samba/smb.conf file then reboot.

in the example bellow my share name is Downloads and the username is user
```

[Downloads]
path = /home/user/Downloads
available = yes
valid users = user
read only = no
browsable = yes
public = yes
writable = yes

```

---

### Post by zaphod777 on 2010-08-30
> **lmarmisa said:**
> If both computers are connected to the same LAN, they do not need Internet for the communication between them. So, it sounds  stranger your comment about the too slow connection. Are you using Ethernet and some router/switch in your LAN?. Standard speed for such type of LANs is 100/1000 Mbps. So, this is really fast.

In relation with Samba, check if the packages samba and system-config-samba are installed in the PC that you want to play the server role. Use the package manager System -> Administration -> Synaptic for this purpose.

After this installation you will be able to configure your Samba server selecting System -> Administration -> Samba.
that system-config-samba is pretty awesome that takes the pain out of manually editing the file.

---

