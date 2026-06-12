---
title: "Downloads folder has disappeared"
date: 2012-01-28
forum: General Help
---

### Post by N00b-un-2 on 2012-01-28
I just did a fresh install of Lucid 64bit a few days ago on a new computer.  I booted the computer up today and my Downloads folder has disappeared.  I didn't delete it, I didn't accidentally move it, it's just plain missing.  And unlike what happens when you delete one of the default folders in home, when I recreate the folder it does not automatically take on the folder-download icon from the theme.  Checking the file /home/user/.config/user-dirs.dirs confirms that the entry for the downloads folder was missing.

Re-adding the line that reads 

```
XDG_DOWNLOAD_DIR="$HOME/Downloads"
```

and then recreating the Downloads folder fixes the issue, but the files within the Downloads folder have mysteriously vanished.  This isn't the first time I've heard of this problem.  Any clue what happened there or how to prevent it from happening again?

---

### Post by raja.genupula on 2012-01-28
> but the files within the Downloads folder have mysteriously vanished

Hi man , problems sounds really different . but i think we have chances for recovery that data .
please look at here 

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by N00b-un-2 on 2012-02-01
The files later appeared in the "lost+found" folder in /home (I have "/home" on a separate partition from "/").  Unfortunately, they were not anything usable so I just deleted them.  It's not as though I lost anything terribly important, mostly just a few packages I'd compiled from source and a handful of downloads.

For anyone who experiences this, it turned out in my case that the error was caused by Windows.  I have my /home which mounts in Windows as "Z:>" using ext2fsd 0.51 EXT3 driver. My /home partition is formatted EXT3 specifically so that Windows can access it (ext2fsd does not have an EXT4 driver).

The loss of data is unfortunate but the problem with my "Downloads" folder disappearing was fixed by creating a new folder in /home/user/ and then fixing the ~/.config/user-dirs.dirs file as mentioned in my first post.  After that, Downloads showed back up in my sidebar again using the proper icon.

---

### Post by Rebelli0us on 2012-02-01
If you run Windows in VM and "share" your home folder in Ubuntu, then you can use both OSes simultaneously and **Windows will be able to read & write your home folder**.

---

### Post by N00b-un-2 on 2012-02-01
This computer doesn't have the guts for virtualization really. It's a spare rig that I've put together on a shoestring budget that does only basic tasks; word processing, email, surfing, light photo editing, etc.   Not only that but it's my wife's computer and she has a hard enough time just switching between Windows and Ubuntu at boot >> even using BURG with big shiny buttons for GRUB menu entries.  Going through the hassle of setting up two separate hardware profiles, a dummy MBR, emulating grub and virtualizing Windows on Ubuntu and then selecting the other profile when booting natively is just asking for trouble in her case.  She doesn't want to deal with that, nor does she know how.  Nor is she interested in taking time to learn it.  The mere fact that I have her using Ubuntu as her OS of choice is in my eyes a huge victory in and of itself. so why push it?
I have her directories in C:\Users\username (eg; "My Documents", "My Pictures", "My Music",etc.) symlinked (or I suppose the correct Windows terminology would be "targeted" or "junctioned") to the /home/user directories on the /home partition.  This is so that I don't have to deal with telling her EVERY time she's looking for a file that she was working on in Windows that it's under "/mnt/701723904629-017368302/Users/user/My Documents/file.doc".  There is no way she'd understand that.  Now all of her documents are in one place and accessible from either OS she gets.
My personal computer doesn't have Windows, but for her since she is a school teacher Windows tends to be a necessary evil (which sucks because apparently teaching resource web sites tend to be fraught with viruses and malware... go figure).  Lots of web sites require IE and sorry but Office just doesn't run well enough on Wine.  She always ends up needing to use the ONE odd function on Publisher or Excel that somehow locks up the computer because the visual basic runtime doesn't work 100% correctly on Wine.

---

