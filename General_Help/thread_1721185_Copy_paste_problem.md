---
title: "Copy paste problem"
date: 2011-04-04
forum: General Help
---

### Post by chand.sethi77 on 2011-04-04
I have some files in my G: (g drive) . I want to copy them to filesystem" /var/www/dav " to this direcotry. 
I also have some files in home folder > documents. I wanna also copy them to /var/www/dav 
I can't simply copy paste becuase paste option is disabled I don't know why. How to do it using terminal

---

### Post by domu on 2011-04-04
Probably you don't have sufficient permissions for the /var/www/dav directory (and indeed you probably shouldn't have!)

Did you use 'sudo' when you did it from the terminal?

---

### Post by chand.sethi77 on 2011-04-04
i know I don't have but i want to know the command after sudo in detail ie. sudo cp /???? /var/www/dav

Please just tell me what to write in place of ?????? I want to copy from G:/dav and also from Home Folder

---

### Post by domu on 2011-04-04
well for things in Documents:
```
sudo cp Documents/my_file /var/www/dav/
```

when you say you have drive G: this is a Windows description. I'm guessing this is a plug-in USB drive, in which case you are likely to find it at:

```
ls /media/[some_weird_name]/
```

to find the name look in Places and open the drive, the window will have the drive name.

---

### Post by martinlall on 2011-04-19
For what I've understand is that ubuntu has problems with copy-paste. Since 8.10 or so.
For example - 

I open firefox, select random text and copy it (i keep FF opened)
(for confirming it's in the mem I open gedit and confirm I can paste)
Now when I close firefox and try to paste again, it's not possible.

(For, again, corfirming it's not FF problem I try to do the same but with folders)

I open Folder1 and copy File1 (i keep Folder1 opened).
(For confirming that the file1 is in menory, I'll open Folder2 and try to pase - I can)
I now close folder1 and try to paste file1 to folder2 - not possible since the file isn't in memory any more.

This has been so in many different servers, pc-s, different (ubuntu) builds.

---

