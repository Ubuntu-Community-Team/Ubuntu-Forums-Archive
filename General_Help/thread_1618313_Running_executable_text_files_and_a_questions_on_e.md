---
title: "Running executable text files and a questions on execute permissions and file types!"
date: 2010-11-10
forum: General Help
---

### Post by Rytron on 2010-11-10
Hi.

I checked the 'Run executable text files when they are opened' option in Nautilus preferences. I have noticed that files such as **.sh** and **.bin** launch by simply clicking on then (which is great). However I have also noticed that an ordinary **.txt** and **.html** file must not be marked as executable in order to launch it in Gedit and Firefox respectively via clicking. Otherwise you must right click and open with every time.

What file types need to have execute permissions?

What file types never need to have execute permissions?

Do text files ever need to be executable?

Thanks.

---

### Post by TeoBigusGeekus on 2010-11-10
Someone correct me if I'm wrong, but file extensions do not matter in linux. As far as I know, you could name a script myscript.jpg and still be able to run it if you give it the right permissions. 
File extensions just serve as an **indication** of the type of file, therefore guiding the wm to open the appropriate software, but are not binding in any way.

---

### Post by efflandt on 2010-11-10
**ONLY** files that you want to **execute** should have execute permission (binaries, scripts, launchers).  Normal text files or html files should **never** have the execute bit set (except for specific script or dynamic configurations when on a web server).

However, if you copy files from a FAT or FAT32 file system (which has no concept of permissions) text files may inadvertently end up with execute permissions.  So you should chmod -x such files so nautilus does not ask if you want to run or open them in an editor.

Note that the **x** bit means something different for directories (it means **access** instead of execute).  If someone does not have x permission for a directory, they cannot do a directory listing (ls).  That is why directories typically have 755 permission drwxr-xr-x, or 700 drwx------ if only for the user.

---

