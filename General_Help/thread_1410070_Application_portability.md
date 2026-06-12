---
title: "Application portability"
date: 2010-02-18
forum: General Help
---

### Post by GamePad64 on 2010-02-18
I have a binary [ I have lost the source code :( ] ELF file (with some scripts and files, which are deps of this binary). The dependencies are in /usr/share/<appname>, /usr/bin, /etc. Is there any way to make this application portable (put all the deps in the application directory) WITHOUT changing the binary?

I think there is only one way to do it:
1. Install all dependencies to one directory.
2. mount --bind the system directories ( /bin, /dev, /proc )
3. Use unionfs-fuse to mount /etc ( and, maybe, /usr ) to union application files and files from root fs.
4. Fakechroot to application directory.
5. Run.

So, my way is the application virtualization. Wouldn't my application slow my system? (Application uses gtk and some other libraries)

---

