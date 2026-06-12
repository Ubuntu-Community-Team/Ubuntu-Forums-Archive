---
title: "Promblem with sharing files from external drive"
date: 2011-07-04
forum: General Help
---

### Post by GaBe- on 2011-07-04
Hi.

I have a problem with sharing files from external harddrive. If I create a share from my ubuntu home folder, I can access to it from my Windows 7 laptop. I also see shares created from external drive, but windows says I dont have permission to access in there. I have googled for solution but haven't found any so I might need some help.

Thanks.

---

### Post by Morbius1 on 2011-07-04
I'm guessing that the external hard drive is formatted in ntfs or fat32. If so it's going to automatically mount with permissions that allow only you to access it. The remote user isn't you so access is denied.

The way out of this is to edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```And add the following line to the [global] section:
```
force user = morbius
```[COLOR=Blue]*Change morbius to your own login user name*[/COLOR]
Then save smb.conf, exit gedit, and run the following command to restart samba:
```
sudo service smbd restart
```After a samba restart you need to give the network a few minutes to settle down before you attempt to access the share.

The remote user will be converted to you so he will have access to the usb share.

---

### Post by GaBe- on 2011-07-04
That solves the problem! Thanks!

---

