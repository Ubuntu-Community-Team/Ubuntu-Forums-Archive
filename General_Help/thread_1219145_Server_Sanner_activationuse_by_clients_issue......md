---
title: "Server Sanner activation/use by clients issue....."
date: 2009-07-21
forum: General Help
---

### Post by bishoptf on 2009-07-21
Not sure where to post so I thought I would start here:

Running 8.04 and finally with the epson 64bit release I can now run my scanner..whoo hooo, I have everything up and running and working and wanted to server the scanner out for other folks.  I have this running also but I have one issue that remains and that is in order for someone else to use it scanimage -L needs to be run on the host/server before they can see it.  If you issue scanimage -L on the client it comes back with nothing found.  Now what we are doing is turing the scanner on/off when we need it, and as soon as you do the scanimage -L on the server the client can then see it and use it just fine...hoping someone may have some suggestions...Thanks.

Update, actually found out that all I need to do on the server side is lsusb and then it works for the client....

---

