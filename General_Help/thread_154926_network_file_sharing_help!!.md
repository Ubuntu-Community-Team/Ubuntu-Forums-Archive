---
title: "network file sharing help!!"
date: 2006-04-04
forum: General Help
---

### Post by gorilly on 2006-04-04
i got given a HP netserver800 with 1 ide drive and 2XSCSI drives...

it seemed silly not to use the scsi drives for storage.

i've never got to grips with linux, i've tried mandrake a few times but stick with windows, to TBH im a real clueless fool when it comes to linux

i manage a server 2k3 and SBS2k3 environment. i run 2 offices and have had at peak around 55 users... so although im not a networking pro im certainly not a newbie to networking in general.

im sharing the 2 scsi drives on this server individually.

so far i have installed ubuntu with gnome, i've then configured a shared folder and got the ubuntu box to show up in my domain.

im just stuck on the security now, when i try and connect to the ubuntu box from a windows workstation i get prompted for a usr and passwd. entering the username and passwd of my linux root or desktop user doesnt help...

how do i share with no real security or permissions set?

like on a windows machine i would allow read/write to everyone?

if i HAVE to add users is there a way to get my linux box to read active directory to save me sitting an entering loads of usernames..

thanks!!!

---

### Post by slazh on 2006-04-04
In your samba config file (/etc/samba/smb.conf), search for the line 'security='.
If it says
```
 security = user
``` Then you'll have to add users that are authorized to access the samba (your ubuntu station sharing) server.

If, however, it reads
```
security = share
``` then the shares should be available for others. 

Maybe this can help aswell:
[http://www.howtoforge.com/samba_setup_ubuntu_5.10]("http://www.howtoforge.com/samba_setup_ubuntu_5.10")

---

