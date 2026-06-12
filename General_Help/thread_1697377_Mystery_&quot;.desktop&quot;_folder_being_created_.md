---
title: "Mystery &quot;.desktop&quot; folder being created under shared folder"
date: 2011-02-28
forum: General Help
---

### Post by jfollmann on 2011-02-28
I'll try to make this as concise as possible. On my Ubuntu 10.04 server, I have a folder which is /mirror. It is shared out to the network through several protocols, mainly NFS and Samba (a sub-folder, /mirror/backup/mac, is shared as an Apple Time Machine backup volume using netatalk).

A few hours ago, I noticed that when viewing /mirror in Nautilus, there is a folder under /mirror which is also named mirror (meaning this mystery folder appears to be /mirror/mirror). It looks that way locally on the server's screen, or from one of the other Ubuntu machines through NFS. The first unusual thing I noticed was that I can't open it with a double-click. If I view the folder properties, it shows that /mirror and /mirror/mirror both contain the same number of files, with the same total size. Almost as if /mirror is appearing again within itself (yes, I checked /etc/fstab to make sure it didn't get mounted within itself, if that's even possible).

Doing an ls from within /mirror gets me this:

```
total 36
drwxrwxr-x  5 root josh   4096 2011-02-28 15:55 .
drwxr-xr-x 25 root root   4096 2011-02-28 15:10 ..
drwxrwxrwx  9 josh josh   4096 2011-02-26 23:19 backup
drwx------  2 root root  16384 2009-05-23 18:21 lost+found
-rwxr-xr-x  1 josh josh    230 2009-09-17 20:41 mirror.desktop
drwxrwxr-x  2 josh users  4096 2011-02-28 11:55 software
```

I think this "mirror.desktop" might be the mystery folder. However, web searches (including this forum) have not revealed what software creates ".desktop" files.

Does anyone know what might be causing this folder-that's-not-a-folder to show up?

My first thought was that one of the network sharing protocols is creating it. Netatalk, for example, creates quite a few strange entries inside folders it shares (to store the extra data Apple's AFP file system uses) - however netatalk is sharing /mirror/backup/mac, I don't think it should be doing anything with the /mirror folder itself.

---

### Post by Smart Viking on 2011-02-28
"mirror.desktop" is not a directory. It is a file. Open it with a text editor to see the contents. It's like a shortcut to a program.

---

### Post by jfollmann on 2011-02-28
Yeah, you're right. The contents are fairly simple, and appear to be nothing more than a file that's designed to show up in Nautilus as a folder.

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Name=mirror
Comment=Open '/mirror'
Icon=inode-directory
Name[en_US]=mirror
Comment[en_US]=Open '/mirror'
Icon[en_US]=inode-directory
URL=file:///mirror
Type=Link
```

I guess it's not so much that I can't open it, as that opening it just directs Nautilus to where I was at already.

I'm still wondering if it needs to be there for some reason. Something created it after all. I guess I will rename and/or move it and see if anything breaks. :)

---

### Post by grahammechanical on 2011-02-28
Does the folder icon have an curved arrow pointing upwards on it? If so, then it is what is called a symlink. (I think). I believe this is a way that the OS uses to duplicate files without actually duplicating them.

Regards.

---

### Post by jfollmann on 2012-03-06
> **jfollmann said:**
> Yeah, you're right. The contents are fairly simple, and appear to be nothing more than a file that's designed to show up in Nautilus as a folder.

Update: It's been a long time, but I happened to find this thread again and thought I'd post what I learned in case it's ever useful to someone.

I've since learned that the .desktop files are a sort of shortcut that point Nautilus to a directory. Nautilus seems to interact with them as if they are their target directory. Right-clicking them and choosing properties will show you the properties of the target directory, for instance.

Basically, the behavior seems similar to a symlink. But it's specific to Nautilus (maybe other graphical file managers, too? I'm not sure on that).

My case just appeared confusing because the .desktop file was inside its target directory, which made some of its behaviour seem odd.

I did get rid of it (first moved, and then later deleted) with no adverse effects. To this day I have no idea what put it there to start with, and it's never shown up again. Might have been something I mis-clicked or mis-typed, for all I know.

---

