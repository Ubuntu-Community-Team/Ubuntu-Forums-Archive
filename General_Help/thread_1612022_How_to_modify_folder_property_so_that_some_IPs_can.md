---
title: "How to modify folder property so that some IPs can access while others dont"
date: 2010-11-02
forum: General Help
---

### Post by ray510 on 2010-11-02
Hi,
I am new to Ubuntu. I try to set up a Ubuntu server that links 4 PC/Mac machines. How can I modify a folder property so that my linked PC can access (Create and delete) while the Mac can't or the other way around? Now, I have created a folder from Ubuntu, It lets all or none linked computers to have the same right. Thank you for your advice[IMG]http://ubuntuforums.org/images/icons/icon3.gif[/IMG]. 
[IMG]http://www.qtl.co.il/img/copy.png[/IMG][[IMG]http://www.google.com/favicon.ico[/IMG]]("http://www.google.com/search?q=assistance")[IMG]http://www.qtl.co.il/img/trans.png[/IMG]

---

### Post by sohlinux on 2010-11-02
what type of file sharing are you using?

---

### Post by ray510 on 2010-11-03
File system is ext3 and I use samba (NFS?) via a local network. I can access the folders from PCs and an Mac. 

I also tried to use "shares-admin" to limit access to only those specified. But it seems no effect.

---

### Post by sohlinux on 2010-11-03
sounds like you are using a single samba user? if so then you need to create different samba users then set each user permissions for read/write individually

---

### Post by ray510 on 2010-11-03
Thank you very much for your replies. 
I did not purposely create any samba user (maybe I am using a default?). How can I tell whether I am using single samba user or not? There is no share section (other than Printer) in the /etc/samba/smb.conf. SECURITY = USER is commented out. 

How can I create more Samba users?

---

### Post by sohlinux on 2010-11-03
> **ray510 said:**
> Thank you very much for your replies. 
I did not purposely create any samba user (maybe I am using a default?). How can I tell whether I am using single samba user or not? There is no share section (other than Printer) in the /etc/samba/smb.conf. SECURITY = USER is commented out. 

How can I create more Samba users?

are you trying to do this from the terminal? or on the desktop samba app?

I would suggest using samba in webmin its so easy.

if you dont want to install webmin we can look at getting those users created

---

### Post by Morbius1 on 2010-11-03
I'm getting lost:
> I also tried to use "shares-admin" to limit access to only those specified
I didn't think shares-admin worked anymore. You need:
```
system-config-samba
```

If I understand the title of your question correctly you want to allow guest access but limit by ip address who can access and who cannot. If that is correct then you can do that by adding a line in the share definition that looks something like this:

```
allow hosts = 192.168.0.100, 192.168.0.101
```This will allow users on those two ip addresses to access the share and no others.

You could also use machine names but samba sometimes has problems with machine names:
```
allow hosts = mach1, mach2
```

---

### Post by ray510 on 2010-11-03
I had webmin (1.520) installed but never used. Configure Server/Samba Windows File Sharing? Will this Webmin be supported with future Ubuntu? Will this work with Mac or Linux? Thank again for your help.

---

### Post by sohlinux on 2010-11-03
> **ray510 said:**
> I had webmin (1.520) installed but never used. Configure Server/Samba Windows File Sharing? Will this Webmin be supported with future Ubuntu? Will this work with Mac or Linux? Thank again for your help.

you can access webmin from any pc because its web based normally on 192.168.x.x:10000, this way you can easily configure your samba and many other things from any pc on the network or over the internet. you may need to open up port 10000 in your router and in the firewall, I use webmin with ubuntu 10.10 and so far have no problems at all. 

try webmin or follow Morbius1 suggestions

---

### Post by ray510 on 2010-11-04
Thank you both and I will try.

---

