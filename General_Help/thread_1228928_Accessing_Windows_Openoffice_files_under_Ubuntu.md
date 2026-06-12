---
title: "Accessing Windows Openoffice files under Ubuntu"
date: 2009-08-01
forum: General Help
---

### Post by rlhoman on 2009-08-01
I have installed Ubuntu under Windows Vista.  I have a number of Open Office data files still on my Vista system.  Can I access them from Ubuntu or do i need to make duplicate copies under the Ubuntu system?  I would like to update them under both systems without having to worry about keeping them in synch if this is possible.

---

### Post by kestrel1 on 2009-08-01
> **rlhoman said:**
> I have installed Ubuntu under Windows Vista.  I have a number of Open Office data files still on my Vista system.  Can I access them from Ubuntu or do i need to make duplicate copies under the Ubuntu system?  I would like to update them under both systems without having to worry about keeping them in synch if this is possible.

Yes you should be able to use openoffice docs & access them from Ubuntu. Ubuntu can read NTFS formatted drives.
If you look under places you should see your Vista drive listed. If you go to Users -> yourusername -> Documents on that drive you should then see your openoffice docs

---

### Post by hetx on 2009-08-01
I assume from your description you used the Wubi installer. In that case you can find the Windows drive in /host in the root directory. Just keep clicking "up" til it greys out, then find Host. Good luck!

---

### Post by chessnerd on 2009-08-01
You should be able to access files on your Vista partition while in Linux (assuming that said partition is not encrypted or anything like that). Open up Nautilus and find your Vista partition. Open that (you may have to enter your admin password at this point) and then search around in your C: drive for the files. They are likely under C:/Users/[yourname]/Documents, unless you saved them somewhere else.

---

### Post by rlhoman on 2009-08-01
Thanks everyone.  It works like a charm and saves me a lot of work moving files.

---

