---
title: "Cannot write into certain parts of NTFS drive"
date: 2006-04-29
forum: General Help
---

### Post by HeirenChen on 2006-04-29
Recently, I've encountered a strange problem when trying to move files into a folder in a Windows NTFS drive from the desktop. I've installed fuse and all that stuff and everything else works fine.

However when I try to do this:

```
$sudo mv cityfight7-1024.jpg /media/hdf1/My\ Pictures/

```

I get this error:

```
mv: cannot move `cityfight7-1024.jpg' to `/media/hdf1/My Pictures/cityfight7-1024.jpg': Operation not supported

```

I'm very, very confused and can't seem to find an answer on Google. This problem only occurs for My Pictures and all sub-directories. Help?

---

### Post by minhaz4u on 2006-04-29
I guess you can't modify the files of a NTFS filesystem...im not sure..just a GUESS :rolleyes:

---

### Post by Almighty on 2006-04-29
Last time I checked there was no captive NTFS support for Ubuntu. So you won't be able to write to a NTFS drive.

---

### Post by HeirenChen on 2006-04-29
I can write to the NTFS drive fine using fuse. The only problem is this specific folder /My Pictures/

---

### Post by ZylGadis on 2006-04-29
No, you can't. Problems will show up at some point and it seems you have hit the first one.

---

### Post by HeirenChen on 2006-04-29
I can write to the rest of the drive that folder's in without any problems. I can write to all my other drives without any problems. Why would the problems show up specifically in one folder?

---

### Post by ZylGadis on 2006-04-29
If you are really curious, you could look at all the relevant sources, and possibly provide the functionality to write to NTFS without problems. Until then, don't complain about something that does not always work, when it is not guaranteed to work at all.

---

### Post by HeirenChen on 2006-04-30
Not complaining, just asking for help.

The problem seems to shift between My Pictures/ and the sub directory Wallpaper. So sometimes I'm able to put stuff in My Pictures and sometimes not. Wierd.

Anyways, if nobody has answers, I'll be off.

---

### Post by Ramses de Norre on 2006-04-30
Maybe when the problem can't get solved you can sent a detailed bug report to the fuse developers. 
I hope they'll be able to provide stable ntfs write support sometimes..

---

