---
title: "Cannot access ReadyNas Duo network shares"
date: 2012-01-19
forum: General Help
---

### Post by n00b_1234 on 2012-01-19
I just installed ubuntu 11.10 and I am unable to access my Readynas duo  shares on the network.  Can anyone help me troubleshoot this? 

The readynas duo does not appear when I attempt to  browse the network.  (note: i have no issue seeing the WDLiveTVhub on my  network)

I am able to access the Readynas through  numerous windows 7 machines on my network. Raidar, software design to detect the device, is installed on the  ubuntu machine and it detects the readynas duo.  I am able to log into  the admin console by inputting the IP address in Firefox.

I have tried inputting the following into the location field on the directory browser:
network:///192.168.1.19/media
192.168.1.19/media
192.168.1.19

Where do I go from here?

---

### Post by n01champion on 2012-01-31
bump!

---

### Post by Khayyam on 2012-02-03
noob_1234 ...

I assume you access the ReadyNAS Duo via Samba on the Win7 machines? You simply need to state the protocol in the filebrowser (Nautilus).

```
smb://user@192.168.1.19/media
```If your ReadyNAS Duo has ftp services running you can likewise connect using 'ftp://'

Also see the [Samba Client Guide]("https://help.ubuntu.com/community/Samba/SambaClientGuide") for alternate methods of connecting using 'sambaclient' and 'sambamount'.

HTH ..

---

