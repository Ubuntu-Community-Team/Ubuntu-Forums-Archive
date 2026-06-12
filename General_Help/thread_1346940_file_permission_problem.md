---
title: "file permission problem"
date: 2009-12-05
forum: General Help
---

### Post by GradaL on 2009-12-05
Hi,

I am using 9.10. I changed the file permission of  all filesystem to 755 and ownership to root for some stupid reason. The code was


sudo chown -R root /
sudo chmod -R 755 /


I didn't backup, and now, i need to reset the file permissions. Is there any short way to do this exept to fix all file one by one?

Thanks..

---

### Post by Tim Sharitt on 2009-12-06
I'm afraid that your best bet is probably to back up any personal files and start over with a fresh install. 


I can imagine that it might be possible to write up a little script to check the permissions on a clean system (maybe a LiveCD squashfs image?) and reset yours accordingly. However, you would probably need to really know what you doing and it would still likely lead to more pain and suffering than it's worth. Just an idea though, I really don't even if it would/could work (probably not, or not the best way even if it did work).

---

