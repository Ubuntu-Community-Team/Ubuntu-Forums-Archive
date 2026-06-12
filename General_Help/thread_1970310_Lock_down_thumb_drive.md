---
title: "Lock down thumb drive"
date: 2012-05-01
forum: General Help
---

### Post by jpdeaton on 2012-05-01
I want to lock down a thumb drive for storing data on. I would like to learn how to set permissions for folders (and the enclosed files) so that only I can view the files and no one can modify them including me. I have had problems with files being remotely deleted in the past. 

Any tips?

How do I get started in partition tabling; that seems like a good place to start

---

### Post by HermanAB on 2012-05-01
Use encypted zip files, PGP, LUKS or EncFS...

---

### Post by kurt18947 on 2012-05-01
> **jpdeaton said:**
> I want to lock down a thumb drive for storing data on. I would like to learn how to set permissions for folders (and the enclosed files) so that only I can view the files and no one can modify them including me. I have had problems with files being remotely deleted in the past. 

Any tips?

How do I get started in partition tabling; that seems like a good place to start

Non-expert here.  I'm not sure how you could make it so someone with SUDO authority couldn't modify them.  For normal accounts, couldn't you just reset permissions to make them read only? Perhaps assign ownership to an account that is not used?  If you normally work in a non-privileged account - and you should IMO, you would not be able to modify a file that has read-only permission.  This can be done in Nautilus started with the "gksudo nautilus" command, right-click the  the file, properties,  then click on the "permissions" tab or via the command line.  I'm not sure if this would help with remote deletions though.

---

