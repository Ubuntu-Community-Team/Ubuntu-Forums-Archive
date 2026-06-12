---
title: "Network shares not available..."
date: 2010-04-23
forum: General Help
---

### Post by peteb2010 on 2010-04-23
Hi

I am giving 10.04RC a try instead of Windows 7, so far so good. I can connect to my network shares fine using "Connect to a Server" & bookmark with the file browser, however when I use OpenOffice writer or Spreadsheet to open/save files the shares disappear in the "Open/Places". Is this a bug in Ubuntu or Open Office? Is there an update/fix?

Thanks:guitar:
Pete

---

### Post by kanikilu on 2010-04-23
I use that "Connect to Server" function a lot as well, and have noticed the same behavior. When you use that, you'll see sub-directories for each connection show up in ~/.gvfs/ and can open/save-to/etc. from there. That's a "dot" file, so hidden by default, so you'll need to be able to view hidden files.

I don't necessarily think it's a bug, but it is confusing...

---

