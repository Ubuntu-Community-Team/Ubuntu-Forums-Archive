---
title: "Upload file and delete file"
date: 2011-07-21
forum: General Help
---

### Post by dollar1 on 2011-07-21
How can I upload and delete a file? :(:(:

---

### Post by sectshun8 on 2011-07-21
In what context.. can you be more specific?

---

### Post by haqking on 2011-07-21
> **dollar1 said:**
> How can I upload and delete a file? :(:(:


upload to where ?

delete from where ?

---

### Post by Grenage on 2011-07-21
> **sectshun8 said:**
> In what context.. can you be more specific?

Quite so.

> **dollar1 said:**
> How can I upload and delete a file? :(:(:

If you're talking about FTP access to a server, then you'd use either a GUI FTP client (e.g: filezilla) or a CLI FTP client (e.g: lftp).

If you're talking about Linux to Linux transfers, then you can move a file using SCP and delete/create files with an SCP connection.  You can also use Samba shares to manage data on other machines, and that works in a similar fashion to Windows shares.  You'll need to provide more information if you want a more apropos solution.

---

