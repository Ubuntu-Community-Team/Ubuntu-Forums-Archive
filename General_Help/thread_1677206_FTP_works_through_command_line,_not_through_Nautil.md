---
title: "FTP works through command line, not through Nautilus"
date: 2011-01-28
forum: General Help
---

### Post by altonbr on 2011-01-28
Does anyone know why Nautilus would allow me to login to a server but not display any files, but when I log in via the 'ftp' command-line binary, it works and allows me to display all the files, make directories, etc.?

I was able to login via FileZilla too. Here's part of the log:

```
Response:	220 Microsoft FTP Service
Command:	USER ----
Response:	331 Password required for ----.
Command:	PASS ***********
Response:	230-Welcome to the Alentus FTP server.
Response:	230 User ---- logged in.
Command:	SYST
Response:	215 Windows_NT
Command:	FEAT
Response:	211-FEAT
Response:	    SIZE
Response:	    MDTM
Response:	211 END
Status:	Connected
Status:	Retrieving directory listing...
```

---

### Post by HermanAB on 2011-01-28
Well, the Nautilus code is not as mature as the command line tools and may have some bugs.  Try Dolphin, Konqueror, Gftp or Filezilla.

---

