---
title: "FTP under Kubuntu 5.10 problem"
date: 2006-03-28
forum: General Help
---

### Post by elder68 on 2006-03-28
When I was using Kubuntu 5.04 "gFTP" was there for file transfering. Now I have updated to Kubuntu 5.10 and "gFTP" is nowhere to be found. I downloaded and installed it using "Automatix" but I can't find it anywhere. When I repeat the process with Automatix it tells me that all files are installed. I updated the file system with "sudo updatedb" and then tried "locate gftp" and what came up did not look like much. Can anyone help with this or point me to a file transfer agent for Kubuntu?
Thank you.

---

### Post by GeneralZod on 2006-03-28
Not much help, but I've just checked and it should just be called gftp and be located in your path at

/usr/bin/gftp

I didn't install using Automatix, though, so perhaps that's the problem?

---

### Post by Adrian on 2006-03-28
[QUOTE=elder68]Can anyone help with this or point me to a file transfer agent for Kubuntu?[/QUOTE]

I'm using Konqueror. In the location bar, just type:

[ftp://elder68@ftp.ubuntu.com](ftp://elder68@ftp.ubuntu.com)

(if you want to connect to **ftp.ubuntu.com** using the name **elder68** :) )

---

### Post by Randomskk on 2006-03-28
Try typing gftp into a terminal to open it, but as Adrian said, Konqueror is KDE's main FTP agent.
Type remote:/ into your browser to configure an FTP for constant use, as well. That way, any KDE app can also save to FTP using the default KDE "Save to.." kinda thing.

---

### Post by elder68 on 2006-03-28
Thank you for all of the replies. I am used to using gFTP and use it a lot. This time I used "Adept" and it installed "gFTP" properly so now I am up and OK.

All the best.

---

