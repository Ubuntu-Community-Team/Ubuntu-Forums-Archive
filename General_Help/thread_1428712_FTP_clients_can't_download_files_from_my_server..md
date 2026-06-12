---
title: "FTP clients can't download files from my server."
date: 2010-03-13
forum: General Help
---

### Post by KanineN on 2010-03-13
I can't download files from my server that I have. 

Filezilla - connect but I cant se the files
BareFTP - connect and see the files but the download stops
gFTP - connect and see the files but the download stops
FireFTP - connect and see the files but the download stops

it have worked before when the server used port 21 but now when they changed it to 4700 it doesn't work. I have emailed them and they get it to work with FLASHFXP but that is a freeware and it is for windows.

in filezilla I get "Error: Failed to retrieve directory listing"

---

### Post by byStanderone on 2010-03-13
...may i know who changed it to port 4700, cause the default ftp port is 21.

---

### Post by KanineN on 2010-03-13
> **byStanderone said:**
> ...may i know who changed it to port 4700, cause the default ftp port is 21.

The company that owns the server changed it.

---

### Post by gmargo on 2010-03-13
How are you telling your tools that the port changed?  Are you specifying the correct URL?  Add the port to the URL with something like [ftp://server.name.here.com:4700/](ftp://server.name.here.com:4700/)

---

### Post by KanineN on 2010-03-13
> **gmargo said:**
> How are you telling your tools that the port changed?  Are you specifying the correct URL?  Add the port to the URL with something like [ftp://server.name.here.com:4700/](ftp://server.name.here.com:4700/)

Yes, The URL is ok and all. I emailed the company and they said that the problem is. 

"by the way the problem is not the port you have some ISP or router problems ask your friend to try download file from your ftp and check this out,
the problems not from our side."

And my friend that I am sharing the server with can't download a file... We have different routers and different ISP...

---

