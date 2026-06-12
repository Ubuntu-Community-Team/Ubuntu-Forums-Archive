---
title: "Samba and write permissions"
date: 2006-05-23
forum: General Help
---

### Post by Irony on 2006-05-23
I've set-up Samba on my Ubuntu Desktop computer and can now access my Windows Laptop computer where I can see;

[PHP]smb://littlecomputer/SharedDocs[/PHP]

I can read the files in there and open them but I cannot write to them - how do I make them write accessible?

---

### Post by mjm115 on 2006-05-23
Is the folder on your Windows PC set up to allow write access?  Right click on the folder in Windows, click on Sharing and Security, and click on the permissions button.  It is probably set to read-only.

---

### Post by Irony on 2006-05-23
Sorry that was a dumb question - I've just remembered that being XP I would not be able to write to the window XP partition.

---

### Post by Seb71 on 2006-05-24
[quote=Irony]Sorry that was a dumb question - I've just remembered that being XP I would not be able to write to the window XP partition.[/quote] 

This is not your situation. You are not trying to write on an NTFS partition from an hard disk drive **inside** your Ubuntu PC.

Try **mjm115**'s suggestion. It should work.

---

### Post by Irony on 2006-05-24
Of course you are right! As XP would actually be doing the writing - the folder was read only so I've unticked that and it works.

---

