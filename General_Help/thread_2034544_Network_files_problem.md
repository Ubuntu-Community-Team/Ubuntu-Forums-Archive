---
title: "Network files problem"
date: 2012-07-28
forum: General Help
---

### Post by dreKion on 2012-07-28
Hello! I have a router with OpenWRT, it has one HDD. I use samba to share folders.

All works good (create folder, copy, move...) in Windows 7, Kubuntu and others distros with KDE.

But in a fresh instalation of Ubuntu 12.04 I can access to the samba share, but I can't create folders, move files...

And the erros is: "The file or folder smb://192.168.1.3/myshare does not exists"

Any idea?

---

### Post by papibe on 2012-07-28
Hi dreKion.

Did you set access based on usernames (using smbpasswd)?

Do you have the same username and password as the other clients?

Regards.

---

### Post by dreKion on 2012-07-28
> **papibe said:**
> Hi dreKion.

Did you set access based on usernames (using smbpasswd)?

Do you have the same username and password as the other clients?

Regards.

Yes, I use "sudo smbpasswd -a drekion"

In my laptop I use Kubuntu 12.04 with the same username and same config and all works good

---

### Post by papibe on 2012-07-28
> **dreKion said:**
> Yes, I use "sudo smbpasswd -a drekion"
That was on the router, right?

> **dreKion said:**
> In my laptop I use Kubuntu 12.04 with the same username and same config and all works good
Does the Kubuntu and Ubuntu machines have the same password? 

Regards.

---

### Post by dreKion on 2012-07-28
In the router:

[PHP]root@SALA:/etc/samba# cat smb.conf
[global]
	netbios name = ROUTER-SALA 
	workgroup = WORKGROUP
	server string = openwrt
	syslog = 10
	encrypt passwords = true
	passdb backend = smbpasswd
	obey pam restrictions = yes
	socket options = TCP_NODELAY
	unix charset = ISO-8859-1
	preferred master = yes
	os level = 20
	security = share
	guest account = nobody
	invalid users = root
	null passwords = yes
	smb passwd file = /etc/samba/smbpasswd

[homes]
	comment = Home Directories
	browseable = no
	read only = no
	create mode = 0750

[COMPARTIR]
	path = /mnt/usb/contenido
	read only = no
	guest ok = yes
	create mask = 0777
	directory mask = 0777
root@SALA:/etc/samba# 
[/PHP]

The router allow to all devices without password (I need this because is my lan and all devices can access to this..)

My computer and my laptop has the same username and passwords. My brother and my father in Windows 7 can do anything with his diferent users and passwords. 
My brother has another laptop with kubuntu with diferent username and works well

---

### Post by papibe on 2012-07-28
> **dreKion said:**
> "The file or folder smb://192.168.1.3/myshare does not exists".

After a second look, that doesn't look like a typical router's address, since it usually ends on 1 or 254. Are you sure that's is the router's address?

Another question: are you having problems with 'homes' or 'COMPARTIR'?

Regards.

---

### Post by dreKion on 2012-07-28
This is because my home has 4 floor and the concrete no wifi signal passes.

In 192.168.1.1 - internet
1.2 - Third floor router
1.3 - Second floor router (this has hard drive)
1.4 - fourth floor router
1.5 - router of my other house at 2km....

and many more... 


[ATTACH]221928[/ATTACH]

The error info is in spanish but is translate in the first post. I try to make a folder but says "not exits". I think this isn't a permision problem.

I use "compartir" because this is used also in minidlna server...

---

### Post by dreKion on 2012-07-30
I change language from Spanish to English and now works well....

With English the unique problem is the symbol "ñ" typical in spanish language... If I want copy a folder with this symbol:

"No such file..."

any idea? I will change unix charset = ISO-8859-1 to utf...

---

