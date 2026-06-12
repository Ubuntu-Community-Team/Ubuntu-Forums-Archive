---
title: "How to make a proper shortcut on desktop"
date: 2010-01-26
forum: General Help
---

### Post by ant080808 on 2010-01-26
Hi,

I have been trying to make a shortcut to my downloads folder on my desktop but I only seem to be able to create "link to downloads" folder. I thought this was just the same thing as a shortcut but when I run some programs from the folder they do not work correctly. They only work from the real 'downloads' folder and not the 'link to' folder.

How do I create a proper shortcut that just opens my real 'downloads' folder and not some nasty impostor. :)

Thanks

---

### Post by ajgreeny on 2010-01-26
If you right click on the desktop, choose "Create Launcher" and in the top box dropdown choose Location.  Now in the second box type in the **/home/username/Downloads** pathway for your own system.

If you try to use the browse button it will not work, for some reason, a bug? I don't know, but it just keeps opening deeper and deeper into the file-system, and does not produce the launcher you want.

---

### Post by jamesisin on 2010-01-26
Drag and drop whatever you want linked while holding shift-ctrl.  You will note that the move-arrow and the copy-plus become an infinity-loop on the icon when you do this--this is the symbol for link creation.

It sounds like what you want is a hard link (and not symbolic as I describe above):

[http://www.cyberciti.biz/faq/creating-hard-links-with-ln-command/](http://www.cyberciti.biz/faq/creating-hard-links-with-ln-command/)

One command line operation:

```
ln /path/to/dir LinkName
```

---

### Post by ajgreeny on 2010-01-26
Yes, I should have added that option, silly me!  In fact if you have a wheel mouse, you can drag and drop when holding the wheel (middle) button down, and you will get the choice of move/copy/link after releasing the mouse.  A very useful file management option I didn't think about at the time.

---

### Post by ant080808 on 2010-01-26
thank you. I tried the drag and drop method and it worked.

---

### Post by jamesisin on 2010-01-26
Don't bother trying the hard link method.  Systemically disallowed for directories.

Glad the soft link worked.  Hope it works with your application as well.

---

### Post by jamesisin on 2010-01-26
ajgreeny - Yeah, I just discovered that middle-click and drag bit.

---

