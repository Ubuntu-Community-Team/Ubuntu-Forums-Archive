---
title: "Copy &amp; Paste not working between apps"
date: 2010-08-17
forum: General Help
---

### Post by calelettus on 2010-08-17
I can copy and paste text within a document but can't seem to do so between applications. It just doesn't work.

Any idea what could be causing that? This problem did not exist on earlier versions of Ubuntu.

Running:
10.04 dual boot on a Dell Latitude D510 with 2gig RAM.

Thanks!

---

### Post by TheWeakSleep on 2010-08-17
Does the problem persist even if the application that you copied the text/image/etc. from is still open?

---

### Post by calelettus on 2010-08-17
> **TheWeakSleep said:**
> Does the problem persist even if the application that you copied the text/image/etc. from is still open?

Sometimes but it doesn't seem consistent. For example, I can copy & paste between two text docs in testing but cannot copy from an email in Evolution to a text doc.

If I copy some text, then close the source app, the copied material is not held in memory.

---

### Post by AlphaLexman on 2010-08-17
Are you using a clipboard manager, like 'xclipboard'?
It would most likely be in your 'system tray'.

---

### Post by calelettus on 2010-08-17
> **AlphaLexman said:**
> Are you using a clipboard manager, like 'xclipboard'?
It would most likely be in your 'system tray'.


No, I'm not.

---

### Post by ubuntu27 on 2010-08-17
The solution is to install a clip-board manager.

I recommend you to install [Parcellite]("http://parcellite.sourceforge.net/"). Click the link to install

```
[sudo apt-get install parcellite]("apt://parcellite")
```


That will take care of Copy&Paste problem

---

### Post by calelettus on 2010-08-18
> **ubuntu27 said:**
> The solution is to install a clip-board manager.

I recommend you to install [Parcellite]("http://parcellite.sourceforge.net/"). Click the link to install

```
[sudo apt-get install parcellite]("apt://parcellite")
```


That will take care of Copy&Paste problem

Hey, thanks for that! It works just fine.

---

