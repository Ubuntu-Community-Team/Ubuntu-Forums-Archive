---
title: "Ownership and Group Permissions not correct?"
date: 2010-01-08
forum: General Help
---

### Post by Dan1317 on 2010-01-08
Hello, I hope you can help.  I have a samba server for windows clients that runs everything creating masks for 777.

My problem is that I need to update a file (Quickbooks file getting more data added to it)  I can rename the file or do everything but update from another file.  I can even save the same file, like if I entered data by hand in QuickBooks.

The owner of the file is not the user I am at the workstation, but when I chown the file, I can update it from another file (Again, the file permissions were 777 all along)

The owner of the files are another user.  I am wondering if I should chown everything as root?  I don't see how chown would help if the group permissions are 7 just as owner  permissions are

Hope I was concise, I can provide info if I left anything out.  Thanks a bunch

---

