---
title: "How to access Windows Shadow Copy from Linux CIFS clients"
date: 2010-06-10
forum: General Help
---

### Post by latzke on 2010-06-10
Trying to access "previous versions" of a file on a Windows server with Shadow Copy enabled.  

In Windows file explorer you get a nifty "previous versions" tab.  I see nothing equivilant in Nautilus (well, I've found similar, but it seems to apply only to [TimeVault]("https://wiki.ubuntu.com/TimeVault") snapshots on Linux...not CIFS to Windows).

At command line in windows you can successfully access a previous version if you know the @GMT path (i.e. "dir \\server\share\folder\@GMT-2010.06.10-18.00.04" returns a successful directory listing).  Trying similar in smbclient fails (i.e. "cd @GMT-2010.06.10-18.00.04" returns "NT_STATUS_OBJECT_NAME_NOT_FOUND".

From Linux, how do I (1) get a listing of available previous versions on a CIFS share and (2) access such?

---

