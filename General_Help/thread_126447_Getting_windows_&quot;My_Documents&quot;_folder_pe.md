---
title: "Getting windows &quot;My Documents&quot; folder permissions working properly."
date: 2006-02-06
forum: General Help
---

### Post by orangedoor on 2006-02-06
This is both a how-to as well as a request for a better solution, I had done a lot of searching for the solution to my problem as well as chatting in IRC to no avail.

**The setup**: Windows is setup with the "My Documents" folder on a seperate FAT32 partition (different physical disk as well). My computer dual boots XP and Ubuntu 5.10. I do a lot with music and have a very large library in XP under "My documents"/"My Music" . I wanted to be able to add to that library under Linux, and am not ready to abandon windows yet and I have many programs setup for existing directories in windows.

**The problem**: No matter how I configured the FAT32 partition (hdb1) in fstab, I could not create folders in "My Documents" on it as a regular user (id 1000), only as root. The problem was specific to the "My Documents" folder and certain sub folders.
[B]
The cause[/B]: I am *almost* positive that the cause is "system" files that Windows XP automatically creates. These include "desktop.ini" "thumbs.db" "folder.jpg" and albumart files. Why it messes with permissions in Linux is beyond me, maybe somebody could explain. My linux guru friend couldn't get to the root of the problem and resolve it under linux (except with a chmod script at start, but that was too much of a hack to stick with).

**My solution**: Changing the attributes of the files and folders in the "My Documents" tree under windows. In a command prompt I went to my "My Documents" folder and ran:
> ATTRIB /S /D -R -H -A -S
I also went to Tools -> Folder Options -> View and selected "Do not cache thumbnails" in hopes that any albums or other folders that I add in windows won't have the same problem.

How the syntax works:
> ATTRIB [+R | -R] [+A | -A ] [+S | -S] [+H | -H] [[drive:] [path] filename] [/S [/D]]
+  	Sets an attribute.
- 	Clears an attribute.
R 	Read-only file attribute.
A 	Archive file attribute.
S 	System file attribute.
H 	Hidden file attribute.
/S  	Processes files in all directories in the specified path.
/D 	Process folders as well.

From: [http://www.computerhope.com/attribhl.htm](http://www.computerhope.com/attribhl.htm)


It is possible to run scripts in windows on shutdown, but I will only do that if the problem repeats itself.

If somebody has more information on the problem or a better solution, would be great.

---

### Post by aysiu on 2006-02-06
The first seven months I dual-booted I had a huge FAT32 for sharing music and files between Ubuntu and Windows XP, and I never ran into that problem. I could create folders in Ubuntu, create them in XP, and had no problems with permissions.

This /etc/fstab entry worked just fine for me: ```
/dev/hda5 /windows vfat iocharset=utf8,umask=000 0 0
```

Now that I use Windows for only VPN-ing into work, I made my huge music/files partition Ext3.

---

