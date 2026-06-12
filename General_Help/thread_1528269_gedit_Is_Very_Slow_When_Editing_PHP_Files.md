---
title: "gedit Is Very Slow When Editing PHP Files"
date: 2010-07-10
forum: General Help
---

### Post by Garetty on 2010-07-10
This started a while back... but I'm not sure when. Whenever I'm editing one of my PHP files it takes 1+ seconds for it to write the letter I type. I tried it on HTML and it's perfectly fine. I tried going to .gconf/apps and deleting the gedit-2 file, but it didn't help. And I tried disabling the File Browser Pane plugin and it did nothing. And one more thing, it might just be some PHP files, because about half of mine are really slow like that, but the other half is perfectly fine.

---

### Post by Steve603z on 2010-07-10
Try turning off PHP Highlight Mode (View > Highlight Mode > Plain Text), see if that makes the problem go away.

I would consider submitting a bug report with a sample PHP file that is causing the error to: [https://bugzilla.gnome.org/](https://bugzilla.gnome.org/)

Also, are you running any gedit plugins that may be causing problems, and are these files being stored on your local hard drive, or are they on a mounted SFTP/SSH location?

Although I occasionally edit PHP files with gedit, most of my PHP development is done using NetBeans, Geany is also a pretty good PHP editor.

---

