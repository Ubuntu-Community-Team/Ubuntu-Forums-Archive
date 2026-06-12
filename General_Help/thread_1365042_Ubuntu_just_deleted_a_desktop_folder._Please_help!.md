---
title: "Ubuntu just deleted a desktop folder. Please help!"
date: 2009-12-26
forum: General Help
---

### Post by TheAlien on 2009-12-26
Hello everyone.

A really strange thing has just happened, and I needed to join this board to get some feedback on the issue.

I've had a desktop folder on my desktop for a while now. It's a folder that I put some random and temporary stuff into.

Path: $home/Desktop/temp-folder/

Today my Ubuntu machine was staying idle for several hours, and when I got back, an error message was visible on the screen: "$home/Desktop/temp-folder could not be read", or something like that. After that, the folder never came back and it seems to have been permanently deleted.

I'm the only one who uses this machine and I've definitely not deleted it.

The folder did contain some important files, so I'd like to have it back. If anyone could help me out, I'd be very grateful.

Here's some system info:

Ubuntu 9.10 64-bit
LVM encryption
All latest updates installed
Pretty default and base system with not much installed

Please ask any questions if further info is needed.

---

### Post by taurus on 2009-12-26
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

---

### Post by TheAlien on 2009-12-26
> **taurus said:**
> What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

This is the output:

```

total 8
drwxr-xr-x  2 admin admin 4096 2009-12-26 23:41 .
drwxr-xr-x 43 admin admin 4096 2009-12-27 00:51 ..

```

---

### Post by TheAlien on 2009-12-26
Okay, I just discovered that the folder is in the Trash.

But before anyone laughs, I did not put it there. This happened while the computer was idle and no one had physical access to it during that time.

Are there any logs I could view to solve this mystery?

At least my files are back. :)

---

