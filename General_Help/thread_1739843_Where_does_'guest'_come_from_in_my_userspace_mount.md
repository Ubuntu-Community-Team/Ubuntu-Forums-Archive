---
title: "Where does 'guest' come from in my userspace mounts? FreeFileSync permission problem."
date: 2011-04-26
forum: General Help
---

### Post by Redsandro on 2011-04-26
Please help me understand what's happening.

I am mounting a **Cygwin** (Windows) tree in my home directory with **sshfs**. The ssh user has full control over all files on the Windows machine. In this directory, most files owners are like **544:513**, whatever that means. I have full control over these files. I can create, remove, *rm -r*, etc. When I create something, it has mode 644 for files and 755 for dirs.

But when I create new directories from within Ubuntu, they are owned by **guest:513**. I use this setup to synchronize using [Free File Sync]("http://sourceforge.net/projects/freefilesync/") [SIZE="1"](which is awesome btw!)[/SIZE]. There are also no problems with FFS.

BUT - when FFS creates a folder on the sshfs directory filled with subdirectories and files (guest:513), it cannot be removed by FFS or Nautilus!

The big problem is, on every sync FFS also creates a temporary directory for removing files, to remove at the end of the sync. And this one cannot be removed:

```
Error moving to Recycle Bin:
"/home/user/sshfs/c/somepath/FFS 2011-04-26 181800"

(Glib Error Code 15, g-io-error-quark: Unable to find or create trash directory)
```

It seems like FFS does not know how to move something to trash. But then when I shift+delete the directory in Nautilus, it sais **Permission Denied**.

Then when I go to the terminal to **rm -r**, there is no error, but afterwards the dir is not removed either.

What I CAN do is traverse trough the entire tree, remove all files first, remove empty directories and then remove the base directory. This works.

What is going on? My user has full control here, and my user on the remote machine has full control too. Yet these permission issues are nasty.

Any idea?

---

