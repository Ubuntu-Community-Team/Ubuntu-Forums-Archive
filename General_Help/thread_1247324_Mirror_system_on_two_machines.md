---
title: "Mirror system on two machines"
date: 2009-08-22
forum: General Help
---

### Post by huertas on 2009-08-22
I have two ubuntu systems -- one laptop that is big and fast and stays at home and a netbook which is easy to carry around.

Here's my question -- Is there a way to have both systems mirror each other so that when I am home, I can use the big laptop and then when I leave, I can use the netbook, but the systems have the same information/settings/files, etc...

would running UBUNTU off of a usb drive work -- figure it would be a little slow.

This would be way cool!! Anything anyone can help with would be awesome.

Thanks :)

---

### Post by nhanquy on 2009-08-22
write a script to backup/restore your home directory to/from lap/desk via an USB stick every time you login/out the machines.

---

### Post by majed on 2009-08-22
If you don't make many changes to the system itself, all you need to sync is your home directory and any other partition where u keep "data"...

To sync specific file systems or directories search for some sync scripts.. rsync is a popular option.

Good luck!

---

