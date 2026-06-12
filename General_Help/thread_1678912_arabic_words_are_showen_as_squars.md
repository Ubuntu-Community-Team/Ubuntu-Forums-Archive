---
title: "arabic words are showen as squars"
date: 2011-01-31
forum: General Help
---

### Post by THE-FOX on 2011-01-31
[IMG]http://img262.imageshack.us/img262/6673/screenshotde.jpg[/IMG]
the browser i'm using is opera
and this is the only site that looks like this but it's a very important one
there should be arabic words there 
i tried to change the language encoding to arabic windows-1256 
tried to install arabic in language support
i'm still new to ubuntu :)

---

### Post by [Snc] on 2011-01-31
Try with this encoding UTF-8

If that fails, press Ctrl+U, there in the start, find this
```
<meta http-equiv="Content-type" content="text/html; charset=XXXXXXX" >
```where the XXXX is, is the exact encoding info, try to set it to that encoding.

If yet still all fails, try to install an arabic font pack. Go to Ubuntu Software Center, select fonts and type 'arab' in the search, I have 7 hits, install them all, then it should work.

ps. maybe you have to logout+login or restart opera for the changes to take effect, i dont know :)

---

