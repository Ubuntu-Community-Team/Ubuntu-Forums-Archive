---
title: "Print from windows 7 to server"
date: 2011-11-13
forum: General Help
---

### Post by henryplumb on 2011-11-13
Hi. I have a server running Xubuntu 10.04 LTS sharing files over samba and sharing a printer through CUPS. All of my computers in the house are Mac OS or Linux machines apart from one windows 7 machine. All of the Mac and Linux machines can print to the xubuntu server fine but, when I try to add the printer to windows 7 it can't find it using:
ipp://192.168.1.3:631/printers/Stylus-CX6400     or
[http://192.168.1.3:631/printers/Stylus-CX6400](http://192.168.1.3:631/printers/Stylus-CX6400)

Thanks.

---

### Post by BillyBoa on 2011-11-13
I don't know if you already installed Samba

```
sudo apt-get install samba
```

then you have to open it from dash and tweak it.

After that you search from printers, window printers installed through samba.

---

### Post by henryplumb on 2011-11-13
Yeah. I have already got samba for the file sharing but, there is nothing in my smb.conf about printing? I assumed I could just print to windows through CUPS without using samba. What do I have to put into my smb.conf to get it to share the printer over samba?
Thanks.

---

