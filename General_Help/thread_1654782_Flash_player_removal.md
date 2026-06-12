---
title: "Flash player removal"
date: 2010-12-28
forum: General Help
---

### Post by bdemers on 2010-12-28
Using firefox 3.6.13 on 8.04.  Doing about:plugins shows Flash 9.xxx installed.  So, natch, does the drop down.  I can disable Flash from the drop down, but can't remove it!  I've been cursed!!!!

Using terminal I type in ```
sudo apt-get remove --purge flashplugin-nonfree
``` and get message back saying that the plugin doesn't exist.
Certainly can't remove something if it isn't there, now can we?


Great!!  50 how-tos all have same command line, and it fails me.  What next?  I am more than happy to remove firefox, but I know that when that happens, all the plugin in info will say behind.

I really want this plug in gone, any suggestions?

---

### Post by mikewhatever on 2010-12-28
Try running **locate libflashplayer.so** to see where the plugin is located. You may have installed it into the .mozilla folder, and if so, removing it with apt-get makes no sense.

---

### Post by bdemers on 2010-12-28
Doesn't exist.  Here's a list of flashplayer files on my box:

barry@barry-laptop:~$ sudo locate blibflashplayer.so
barry@barry-laptop:~$ sudo locate flashplayer
/home/barry/.macromedia/Flash_Player/macromedia.com/support/flashplayer
/home/barry/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys
/home/barry/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#mail.google.com
/home/barry/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#s.ytimg.com
/home/barry/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.liveleak.com](www.liveleak.com)
/home/barry/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/settings.sol
/home/barry/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#mail.google.com/settings.sol
/home/barry/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#s.ytimg.com/settings.sol
/home/barry/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.liveleak.com/settings.sol](www.liveleak.com/settings.sol)
/opt/google/chrome/libgcflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so
barry@barry-laptop:~$ 


I did update the database (I don't type well,so I tend to recall a line and replace only what I need to, that's why the sudo)
You can see that the search term you gave me doesn't exist.  I did a copy and paste from your post, so I didn't do a typo.


Here's a snippet from about:plugins:


Shockwave Flash

    File: libswfdecmozilla.so
    Version: 
    Shockwave Flash 9.0 r100

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes


Here I searched for libswf......:

barry@barry-laptop:~$ locate libswfdecmozilla.so
/usr/lib/swfdec-mozilla/libswfdecmozilla.so
barry@barry-laptop:~$ 

I renamed the directory (swfdec-mozilla) to an alternate,removed the original, and restarted ff. Flash player is now gone.  

Thanks for the guidance:guitar:

---

### Post by mikewhatever on 2010-12-28
Here is the command you have to use to uninstall that version of flash.
```
sudo apt-get purge swfdec-mozilla
```

---

### Post by bdemers on 2010-12-29
Thanks it restored position and then removed.

---

