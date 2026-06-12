---
title: "Nautilus Issue with hidden folders"
date: 2010-06-05
forum: General Help
---

### Post by lin73 on 2010-06-05
Hi all,

I'm not sure if this issue is a bug. Actually, Nautilus allows two instances of the same folder, or two folders with the same name in the same directory, as long as one is hidden (with the .prefix) and the other is shown. It happens that, if during a download (through a download manager or a torrent client) the user adds the . prefix to the download folder, another will be automatically created by the application (let's say Transmission for example) and the download would continue to that new folder. If any renaming happens (or if the original folder is restored), the download will resume to the folder with whichever initial name. Eventually, the user will be left with an unusable/corrupt complete download.

---

### Post by ibuclaw on 2010-06-05
> **lin73 said:**
> Hi all,

I'm not sure if this issue is a bug. Actually, Nautilus allows two instances of the same folder, or two folders with the same name in the same directory, as long as one is hidden (with the .prefix) and the other is shown. It happens that, if during a download (through a download manager or a torrent client) the user adds the . prefix to the download folder, another will be automatically created by the application (let's say Transmission for example) and the download would continue to that new folder. If any renaming happens (or if the original folder is restored), the download will resume to the folder with whichever initial name. Eventually, the user will be left with an unusable/corrupt complete download.

If one folder was named.
```
Directory
```
and the other was named
```
.Directory
```
You would not have two folders with the same name.

---

### Post by Bradj47 on 2010-06-05
> **ibuclaw said:**
> If one folder was named.
```
Directory
```
and the other was named
```
.Directory
```
You would not have two folders with the same name.

Yes, the dot before directories mean it's a hidden directory. If Transmission or other torrent/download software is creating hidden files and directories, try checking the folder hierarchy preferences within that application.

---

### Post by lin73 on 2010-06-05
[QUOTE=ibuclaw]If one folder was named.
```
Directory
```
and the other was named
```
.Directory
```
You would not have two folders with the same name.[/QUOTE]

I see.

[QUOTE=Bradj47]Yes, the dot before directories mean it's a hidden directory. If Transmission or other torrent/download software is creating hidden files and directories, try checking the folder hierarchy preferences within that application.[/QUOTE]

Actually, I did hide and un-hide the download folder during the download process. But unlike the "hide file" in windows, adding a dot is practically renaming a directory, not just changing its visibility. I made the assumption that nautilus would not allow a ".directory" and a "directory" in the same path, and would continue downloading to ".directory".

---

### Post by dino99 on 2010-06-05
unhide files and dirs with the menu

---

### Post by geirha on 2010-06-05
Techincally, linux doesn't have hidden files. It's just a common thing for programs to treat files starting with . as hidden files. In windows on the other hand, the filesystem has a special flag/attribute you can set on files to make them hidden; linux doesn't have such a flag/attribute.

---

### Post by lin73 on 2010-06-05
[QUOTE=dino99]unhide files and dirs with the menu[/QUOTE]

That was not the point. I just made the assumption that .directory and directory are treated as one; They aren't.

---

### Post by lin73 on 2010-06-05
[QUOTE=geirha]Techincally, linux doesn't have hidden files. It's just a common thing for programs to treat files starting with . as hidden files. In windows on the other hand, the filesystem has a special hidden flag/attribute you can set on files to make them hidden; linux doesn't have such a flag/attribute.[/QUOTE]

Thank you. That answered my question well.

---

### Post by Bradj47 on 2010-06-05
> **geirha said:**
> Techincally, linux doesn't have hidden files. It's just a common thing for programs to treat files starting with . as hidden files. In windows on the other hand, the filesystem has a special flag/attribute you can set on files to make them hidden; linux doesn't have such a flag/attribute.

Sorry if I'm reviving a dead thread, but I'd like to point out that Windows does hide .files from explorer, though that's not the default way Windows hides files as far as I know.

---

### Post by ibuclaw on 2010-06-05
> **Bradj47 said:**
> Sorry if I'm reviving a dead thread, but I'd like to point out that Windows does hide .files from explorer, though that's not the default way Windows hides files as far as I know.

No, 

**In Windows**:
It hides $files from file browser iirc.

There is also filesystem support for hiding files too. Firstly through that thingy interface when you right-click->options on a file. Secondly when you open a terminal and run:
```
attrib +h file
```
My memory on this is vague though. And I'm probably far too drowned with fatigue anyway. :)

**In Linux**:
It hides .files from file browser.

There is no file system support, however GNOME has support for ".hidden" files. These are files named ".hidden" within a directory with a list of files inside.

ie:
```

foo.txt
bar.ogg
Private

```
And then any files that share the same names as the above will be hidden in nautilus for that one particular directory.

---

