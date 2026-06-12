---
title: "Missing Disk Space"
date: 2009-11-03
forum: General Help
---

### Post by pistos on 2009-11-03
I deleted a very large file (18GB) from my system using the File Browser, opened as root (using gksudo). The file was located in the usr/lib/ directory.

Here is my problem: The disk space was not given back to me as free space available on the disk following the deletion. The file is no longer there, but the space it took up was not freed. So, I have about 18 GB floating around somewhere, but I can't find it, and don't know how to get it back.

When I run the "Disk Usage Analyser" it tells me I have a total filesystem capacity of 69.0GB, used = 40.4GB, available = 28.6GB. But, the usage details show that at "/" the total used is 21.7GB, and within in that "/home" uses 17.2GB, and the rest of the system uses the remaining 4-odd GB. So, as you can see there is something wrong. There is about 40.4GB - 21.7GB = 18.7GB unaccounted for.  :(

I am using Ubuntu 9.10, the disk uses file system ext3

---

### Post by drs305 on 2009-11-03
Open a root file browser and remove the deleted file from root's trash. As you have discovered, deleted trash continues to take up space until it is removed from the owner's (in this case root's) Trash bin:
```

gksu nautilus /root/.local/share

```
Use SHIFT-DEL to delete the Trash folder. If you use DEL instead of SHIFT-DEL, it will simply be moved back to ... Trash!

You can learn about the Ubuntu trash system here:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by pastalavista on 2009-11-03
Try booting from the live CD and run fsck on the disk.

---

### Post by Bunnybugs on 2009-11-03
Right, even bothered to empty the trashcan? it stays on your disk untill you empty the trash;) it could be there even when it says that it&#347; removed passing the trash;)

---

### Post by John Bean on 2009-11-03
> **drs305 said:**
> Use SHIFT-DEL to delete the Trash folder. If you use DEL instead of SHIFT-DEL, it will simply be moved back to ... Trash!
No it won't, it'll warn you that it can't be moved to Trash and will be permanently deleted.

But in general it's a good idea to get into the habit of Shift/Del when you really want to delete something permanently. If nothing else it avoids the OP's current problem happening in the first place.

---

### Post by John Bean on 2009-11-03
> **pistos said:**
> Here is my problem: The disk space was not given back to me as free space available on the disk following the deletion. The file is no longer there, but the space it took up was not freed. So, I have about 18 GB floating around somewhere, but I can't find it, and don't know how to get it back
Go back into a root Nautilus window and empty the trash. That'll do the trick.

---

### Post by pistos on 2009-11-03
Thanks for suggestions.

I did empty the trash. And, I did go into Root's trash and empty it. But, disk space was still not returned. Root's trash folder was empty (and I had show hidden checked).

---

### Post by wildweathel on 2009-11-03
> **pistos said:**
> I deleted a very large file (18GB) from my system using the File Browser, opened as root (using gksudo). The file was located in the usr/lib/ directory.

Why?  That's important stuff there!  I think it's more important to ask **why there was an unusually large file** (there's nothing that should be that big) in /usr/lib than to just nuke it.


> 
Here is my problem: The disk space was not given back to me as free space available on the disk following the deletion. The file is no longer there, but the space it took up was not freed. So, I have about 18 GB floating around somewhere, but I can't find it, and don't know how to get it back.

EDIT:  Guess it's not in trash... [COLOR=Silver]I hope that file's in roots trash.  Because, you should restore it and tell us what it is before deleting it.  Don't delete system files unless you're really sure what you're doing.[/COLOR]

---

### Post by pistos on 2009-11-03
> **wildweathel said:**
> Why?  That's important stuff there!  I think it's more important to ask **why there was an unusually large file** (there's nothing that should be that big) in /usr/lib than to just nuke it.

LOL.  Thanks for the concern.

The file was a vmware winxp virtual disk. I tried to get vmware to delete the virtual disk itself, but it refused. So, I uninstalled vmware. That did not remove the virtual disk either. So, I manually deleted it, after vmware was uninstalled from the system.

---

### Post by drs305 on 2009-11-03
> **John Bean said:**
> No it won't, it'll warn you that it can't be moved to Trash and will be permanently deleted.


That's the behavior I get on other file managers I use. On my current Karmic (and previous installs), with the default settings, when nautilus is opened with "gksu nautilus", viewing the contents of the Trash/files folder: hitting "DEL" causes the file to disappear and then reappear about a second later. There are settings you can alter to change this behavior, but I believe this is the default.

---

### Post by alphaniner on 2009-11-03
If it is really just one file, open a terminal and enter

```
sudo find / -size +15G 2> /dev/null
```

This will find any files greater than 15GB, which should be few and far between.

Then just remove the file through the terminal

```
sudo rm -i /path/to/file
```

---

### Post by pistos on 2009-11-03
Ok, problem solved. I feel like an idiot. :oops:

I had gone into directory "/root/.Trash" and was looking for the files there. I then noticed the very different location that drs305 spec'ed, which was "/root/.local/share/Trash". When I went into the correct trash folder, the file was there. Geez!

Thank you so much for the help and sorry for the trouble.

---

### Post by drs305 on 2009-11-03
> **pistos said:**
> Ok, problem solved. I feel like an idiot. :oops:

I had gone into directory "/root/.Trash" and was looking for the files there. I then noticed the very different location that drs305 spec'ed, which was "/root/.local/share/Trash". When I went into the correct trash folder, the file was there. Geez!

Thank you so much for the help and sorry for the trouble.

That *was* the location of the Trash folders several releases ago. There are probably many posts from that *era* that are still around. That's one reason it's good to look at recent posts when searching the forum archives.

Glad you got your problem resolved.

---

### Post by wildweathel on 2009-11-03
I still have the sinking suspicion that we only fixed a symptom and not a cause...

/me stays subscribed to thread.

---

### Post by pistos on 2009-11-03
> **wildweathel said:**
> I still have the sinking suspicion that we only fixed a symptom and not a cause...

/me stays subscribed to thread.

:D Well, I defer to your superior knowledge of Ubuntu, but think you can move along from this thread now. The deleting of the virtual machine hard disk file would not have been a big deal except for me losing track of where it went following the delete operation. :D

---

### Post by wildweathel on 2009-11-03
Whew.  Glad it wasn't some kinda broken library.  Thanks.

---

