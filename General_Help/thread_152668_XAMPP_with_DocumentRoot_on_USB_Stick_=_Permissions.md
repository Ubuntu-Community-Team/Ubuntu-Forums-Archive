---
title: "XAMPP with DocumentRoot on USB Stick = Permissions Problem"
date: 2006-03-30
forum: General Help
---

### Post by TomG on 2006-03-30
Hi

I have a permissions problem with combination XAMPP + USB Stick.

I have my website development in a directory on an USB Stick (FAT). It is auto mounted normally on plugin but permissions are set to 700 for user:group tom:tom. There are numerous topics on forums with this and no real/easy solution.

I installed XAMPP (set DocumentRoot to USB directory) but it must be ran as root. As you can guess I cant browse my DocumentRoot as there is no permissions (700 for tom only).

I dont want or I cant :
 o Fill a new line in fstab for USB key
 o Format my USB key to ext*

I wonder :
 o if there is a way to run XAMPP as another user than root (does not work for me) ?
 o is there some linux tricks that I miss to workaround such permissions problem (link...) ?
 o Other solutions ?

Thanks for your suggestions,
Tom

---

