---
title: "Network/Printer Issues 10.04 Dell620"
date: 2010-11-21
forum: General Help
---

### Post by w2ge on 2010-11-21
Newbie here.  10.04LTS on Dell620 wireless.
2 issues and I believe related.  I want to install my printers onto this laptop.  Both (2 laserjets-named "hplj2200" and "BrotherHL3040color")are "locally connected" via USB to a PC in another room (winxp pro) windows network is "workgroup" PC with printers attached is "philmainpc".

1.) Places>Network instantly sees WINDOWS NETWORK, click > WORKGROUP click> opening network> Unable to mount location Failed to retrieve share list.

2.)System>Admni>Printing>ADD>Network Printer>Windows Printer via Samba>Browse> workgroup philmainpc Doubleclick, wait for awhile and then nothing.  I have tried manually typing in smb box "workgroup/philmainpc/"shared name of printer" and again nothing.

In synaptic manager I added smbfs etc..

HELP, TIA

---

### Post by Morbius1 on 2010-11-21
Assuming you shared the printer in WinXP I would do the following:

[1] Turn off - at least temporarily - any firewalls you have set up on both machines just to see if they are getting in the way.

[2] Modify smb.conf on the laptop:

Edit smb.conf as root:```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section:
```
name resolve order = bcast host lmhost wins
```Save the smb.conf file and back in the terminal restart samba:
```
sudo service smbd restart
```

---

### Post by w2ge on 2010-11-21
Morbius, little confused... in smb.conf  I found the global section and there is already this line:

;   name resolve order = lmhosts host wins bcast

Do I want to replace that and/or add your command:

name resolve order = bcast host lmhost wins
  (with the ; and spaces like the other lines?)

Told you I was a newb!

BTW, yes printers are shared, found on all windows PC in my network and all firewalls are off

---

### Post by Morbius1 on 2010-11-21
Just add my line under the existing line without the leading ";" and restart smbd.

[COLOR=Blue]EDIT: SO that it looks like this:[/COLOR]
```
;name resolve order = lmhosts host wins bcast
name resolve order = bcast host lmhost wins
```

---

### Post by w2ge on 2010-11-21
Morbius you are Da' MAN!!  TU!

 (?  What in my post led you to know the answer?  Is it a common problem or something you thought "might" be the issue?)


Instantly all shared folders and PC's appeared as well as available shared printers.  Still having trouble adding the Brother HL3040CN as this model does not appear as a choice in drivers....  I looked at Brother driver downloads for linux and will try that.

---

### Post by w2ge on 2010-11-21
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-3040CN](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-3040CN)

rpm and deb drivers...  lpr and cupswrapper?  Which do I need?  I think the deb drivers.

TU again, Phil

---

### Post by Morbius1 on 2010-11-21
Sorry, I know nothing of Brother printers.

If I had to guess though you'd want the *.deb files and probably both lpr and cupswrapper.

---

### Post by w2ge on 2010-11-21
All solved..  Would change header to RESOLVED (if I knew how!)

Downloaded 2 drivers lpr and cupswrapper.deb files, had to follow a few "pre-requisites in terminal, then Ijust dbl clicked on both the .deb files.  Went to add printer and Viola!  Brother HL3040cups appeared as a choice in drivers.. tested, all is well in the world!

TU Morbius!!

---

