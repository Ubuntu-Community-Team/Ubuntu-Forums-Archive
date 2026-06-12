---
title: "Epiphany is fast! Need help with Flash"
date: 2010-05-25
forum: General Help
---

### Post by shane2peru on 2010-05-25
Ok, I have been using Epiphany for about 2 weeks now, and am still impressed with it, very very fast.  I'm on Lucid Lynx, 64 bit.  I ran the script to install 64bit flash from here:  [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

However I'm not convinced that Epiphany is using it.  When I run a flash video in Epiphany and then check htop, I get this process running ```

/usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /user/lib/flashplugin-installer/libflash 
```

I don't have any clue how to check in Epiphany what plugin it is using for flash.  I tried ```
about:plugins
```  which leaves me with a blank page.  Any ideas or thoughts would be greatly appreciated.  Thanks!!! 

You really do need to check out Epiphany it is fast!

Shane

---

### Post by shane2peru on 2010-05-26
Ok, got this fixed.  I installed 64bit flash and then did ```
locate libflashplugin.so
``` which showed me a few that had been hidden in a few different locations.  After removing them, and replacing them with the 64bit Flash plugin, all is well, no more npviewer.bin showing up, and processor is less stressed. :)

Shane

---

