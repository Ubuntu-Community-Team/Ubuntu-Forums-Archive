---
title: "SAMBA shares working, but not fully?"
date: 2012-10-11
forum: General Help
---

### Post by Colo2 on 2012-10-11
Hi all

I set up an ubuntu machine, and put all my music on it wanting to share it with the network.

I set up a SAMBA share for the folder where the music is, and on other pcs, I can browse that folder and get a dir listing of all my music. When I try and play it on another pc however, I get: **Windows media player cannot access the file. Maybe it's in use or I dont have access to that computer?**

I've tried changing the permissions on the folder, but it doesnt seem to help

can anyone help me?

Thanks

Tom

---

### Post by Colo2 on 2012-10-11
does no one know what the issue is here? :S

---

### Post by asmoore82 on 2012-10-11
> **Colo2 said:**
> I've tried changing the permissions on the folder, but it doesnt seem to help

sounds like its the permissions on the files themselves.

---

### Post by Colo2 on 2012-10-11
true!

how would I go about setting the permissions of all files in a folder?

Tom

---

### Post by critin on 2012-10-11
> **Colo2 said:**
> true!

how would I go about setting the permissions of all files in a folder?

Tom

open the folder and set permissions to allow files to share inside the folder.  I'd share with 'everyone' if the option is there.  

Samba should have asked if you wanted to share files too, and you would have said yes.  It should add all shares.
On 'folder access, be sure to add read/write permissions for yourself if you actually want to work with the files across the lan.

---

