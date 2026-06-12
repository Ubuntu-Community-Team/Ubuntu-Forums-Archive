---
title: "Samba share problems on ubuntu server 12.04"
date: 2012-09-18
forum: General Help
---

### Post by undeadmechanic on 2012-09-18
First off I'm not exactly new to linux, but this is the first time I've tried to use Samba and it doesn't seem to want to cooperate...

I've been trying to get Samba to allow any and all users on my network full access (R+W)  to all files in /home/david on the server and have just about reached my wits end. So far, I can access the files from only one PC, and I must log in each time I reboot the PC. Samba rejects the same credentials from any other PC I try to log in from.

I am not concerned with security on my home network since it's just myself and my wife. This box is just a torrent slave.

As it is now, I have to log in with this PC, copy the files I want to access to this one, and *then* I can access them from any computer in my network. Please help! I've attached a copy of the smb.conf file (renamed as smb.conf.txt to allow me to upload it). I would appreciate it if someone could peruse it and tell me what I have done wrong.

Please forgive my ignorance. :)

Thanks,
David

---

### Post by Morbius1 on 2012-09-18
I didn't quite follow the logging into and out of and the credentials part of your post because this is a guest share you created. 

Anyway give this a shot:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to your share definition:
> [Guest Share]
        comment = Guest access share
        path = /home/david/
        browseable = yes
        read only = no
        guest ok = yes
        [COLOR=Blue]**force user = david**[/COLOR]
Then restart samba:
```
sudo service smbd restart
```If that doesn't work outright you might want to bring your smb.conf back to the modern default by:

Change this:
```
security = share
```To this:
```
security = user
```And right below that line add the following line:
```
map to guest = Bad User
```And restart samba again.

The user secutity + Bad user combo is the modern equivalent of share level security and may do nothing by itself it's just that no one currently living remembers exactly how share level security worked ;)

---

### Post by undeadmechanic on 2012-09-18
Ugh... all this time, the only thing I needed was to add the line "force user = david" and it would have taken care of it... ](*,)

I didn't understand why it was requiring a login either, since I know it was *supposed* to be a guest share...

Oh well, it's working the way it should now! Thanks a million!

---

