---
title: "I need some flash player help"
date: 2009-06-30
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2009-06-30
It is acting like... idk something very stupid.
[http://i39.tinypic.com/2lwq35t.png](http://i39.tinypic.com/2lwq35t.png) - screenshot
I have tried installing flash 10 from adobe it says it was successful but I'm not so sure as indicated by the screenshot
(I don't have a .mozilla/plugins directory) so if I know were the required files were I could bypass this issue.
**No I'm NOT using wine.** It is installed but it is not running also it is set to Windows 2.0
Sorry if this belongs in the multimedia forum.

---

### Post by lovinglinux on 2009-06-30
The solution to your problem is in the Troubleshooting section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

> **lovinglinux said:**
> 
Some video issues are caused by conflicting plug-ins. It's not a good idea to have multiple plug-ins for the same type of content.

To remove conflicting flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```



---

### Post by pqwoerituytrueiwoq on 2009-06-30
thanks the terminal said noting was removed but now it works as it should

---

### Post by pqwoerituytrueiwoq on 2009-06-30
is there a way i can get flash 10 I cant change the quality to low with flash 9 on a certain memory hog flash game

---

