---
title: "Deleting Files WILL NOT free up disk space!"
date: 2010-01-01
forum: General Help
---

### Post by LukeLinux on 2010-01-01
anyone else here done much with photorec? A while back I used it to retrieve some pictures from my camera's SD card, and it loaded nearly 3GB of files into directories in my Documents folder. It worked great and everything, but then when I deleted the folders via a [FONT=Courier New][SIZE=2]gksudo nautlius[/SIZE][/FONT] window, it didn't actually free up any disk space!

I don't have a huge linux partition, so losing 3 GB is a big deal for me. Is there some way I can get it back? Rebooting did nothing, and the files aren't just hidden...

I'm using 9.10 Karmic

---

### Post by linuxonbute on 2010-01-01
> **LukeLinux said:**
> anyone else here done much with photorec? A while back I used it to retrieve some pictures from my camera's SD card, and it loaded nearly 3GB of files into directories in my Documents folder. It worked great and everything, but then when I deleted the folders via a [FONT=Courier New][SIZE=2]gksudo nautlius[/SIZE][/FONT] window, it didn't actually free up any disk space!

I don't have a huge linux partition, so losing 3 GB is a big deal for me. Is there some way I can get it back? Rebooting did nothing, and the files aren't just hidden...

I'm using 9.10 Karmic

They might just be in the trash folder.
Maybe it just needs emptying.

---

### Post by SuperSonic4 on 2010-01-01
My guess would also be trash but in this case it will be the root trash.

Next time press **shift + delete** or use the **rm** command to remove them instead of sending to trash

---

### Post by 73ckn797 on 2010-01-01
Ignore

---

### Post by 73ckn797 on 2010-01-01
In Nautilus/Edit/Preferences/Behavior you can add the option to "Include a Delete command that bypasses Trash". When you right click on a file you will see the option enabled.

---

### Post by LukeLinux on 2010-01-01
Oh! I didn't even think about the root trash being a separate place...just one more problem, though: when I try to access the root trash, it brings up an error message:

"Sorry, could not display all the contents of "trash": Operation not supported"

And then it will neither load the files nor let me just empty it by right-clicking or anything...can I just use a terminal to empty the root trash?

---

### Post by dcstar on 2010-01-01
> **LukeLinux said:**
> anyone else here done much with photorec? A while back I used it to retrieve some pictures from my camera's SD card, and it loaded nearly 3GB of files into directories in my Documents folder. It worked great and everything, but then when I deleted the folders via a [FONT=Courier New][SIZE=2]**gksudo** nautlius[/SIZE][/FONT] window, it didn't actually free up any disk space!


Why do things as root?

---

### Post by ssulaco on 2010-01-01
Go to Applications>Accessories>Disk Usage Analyzer,and "scan home" to make sure they are still not in there.

---

### Post by drs305 on 2010-01-01
[Trash Problems and Solutions]("http://ubuntuforums.org/showthread.php?t=898573")

It explains some of the Ubuntu/Linux concepts concerning trash, and how to find it all and permanently delete it.

---

### Post by LukeLinux on 2010-01-01
> **dcstar said:**
> Why do things as root?

Because photorec locks the recovered folders so that only root can modify them. Normal users have read access, of course, but nothing more.

> **ssulaco said:**
> Go to Applications>Accessories>Disk Usage Analyzer,and "scan home" to make sure they are still not in there.

I did that, and though the folders aren't there, I found something really weird happening. First the DUA reported 4.6 GB free, which is what it should be right now. But then I checked at the bottom of a nautilus window, and it said there were only 418MB free. Within moments, it dropped down to 0 bytes free! I rebooted, and DUA now reports only 1.6GB free, while nautilus tells me there's 1.75MB. What's going on here??

---

### Post by ssulaco on 2010-01-01
run this in the terminal
```
df -h
```
to see if its the same reading as System Monitor

---

### Post by LukeLinux on 2010-01-02
> **drs305 said:**
> [Trash Problems and Solutions]("http://ubuntuforums.org/showthread.php?t=898573")

It explains some of the Ubuntu/Linux concepts concerning trash, and how to find it all and permanently delete it.

This must have been posted while I was typing up my last reply...I didn't see it until now! That link cleared everything up; it turns out that almost 10GB of files are just sitting in the root trash! I can actually delete them now with shift + delete or 73ckn797's little tip :-D

Thanks a lot, guys! This thread is now SOLVED =D>

---

