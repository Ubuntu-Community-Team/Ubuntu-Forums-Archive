---
title: "Wrong language settings in Opera...?!"
date: 2012-04-09
forum: General Help
---

### Post by Chip88 on 2012-04-09
Hey there!

Looked here in the forum for anything useful and searched also in Google, but didn't find anything.

I am using Kubuntu 11.10 with KDE 4.8.2.

My standard web browser is Opera. If I want to save a file, then there popups a window in Opera.

But although all my language settings are in German (for Kubuntu and for Opera!), that window appears totally in English, i.e., all the buttons, the labels etc. are in English (see attached file!).

How can I fix this problem and have it in German again?

Thanks in advance for your help!

Regards,
Chipy

---

### Post by whatthefunk on 2012-04-09
In the Opera Preferences Menu in Language Details, is everything listed as being in German?

---

### Post by Chip88 on 2012-04-09
@ whatthefunk:
Thanks for your fast answer.

The preferred language is **German [de]**.

Under details I see the *Order of the preferred languages shown on websites*:
1. German, [de]
2. German (DE), [de-DE]
3. English, [en]

Any further ideas?!

Thanks in advance!

Chipy

---

### Post by lovinglinux on 2012-04-09
I think it is a KDE bug or configuration issue.

I just made a test, changed my system to Portuguese and the dialog is still displayed in English. However, if I change the File Selector Dialog toolkit in Opera preferences to use GTK, it loads properly in Portuguese. So, it is probably not an Opera issue.

Unfortunately, since I am not using KDE, I cannot log in and change the language settings inside KDE to see if it will have any effect. I am using Ubuntu with Gnome Shell and some KDE applications like Dolphin.

---

### Post by whatthefunk on 2012-04-09
Im using KDE and have set the system language to Japanese...have the same problem.  Its probably an issue with Dolphin, the file manager.  Ill dink around with it and see if I can get it.

---

### Post by Chip88 on 2012-04-09
@ lovinglinux:
How can you change the File Selector Dialog toolkit in Opera?!
Where is that option?

@ whatthefunk:
I already wrote a mail to Peter Penz, the main developer of Dolphin, and he told me that it is NOT a Dolphin bug...

---

### Post by whatthefunk on 2012-04-09
I tried to changeing the File Selector Dialog box....the only one that worked is the x11 option (4) but thats a pretty ugly dialog box.

If you want to try yourself, type "opera:config" in a browser address bar and search for File Selector.
[http://www.opera.com/support/usingopera/operaini/#file_selector](http://www.opera.com/support/usingopera/operaini/#file_selector)

Its a weird bug indeed.  I tried the same thing in other browsers and programs and the save dialog box was properly translated.  It only seems to happen in Opera...is this an Opera bug then?

---

### Post by Chip88 on 2012-04-09
@ whatthefunk: Thanks for your advice!

@ whatthefunk & lovinglinux:
If I change the File Selector Dialog toolkit in Opera preferences to use GTK, it also loads properly in German.

But I want Opera to use the "normal" KDE toolkit. :mad:

So, it's an Opera, a Dolphin or a KDE bug?!

---

### Post by Chip88 on 2012-04-09
Are there any more answers how to solve the bug?!?!

---

### Post by lovinglinux on 2012-04-09
> **Chip88 said:**
> Are there any more answers how to solve the bug?!?!

Unfortunately no, but I also tested X 11 file picker and it has proper language. Must be a KDE/Dolphin issue.

---

### Post by Chip88 on 2012-04-10
@ lovinglinux:
Well, so where do we have to report it so someone can change it?!

---

### Post by lovinglinux on 2012-04-10
> **Chip88 said:**
> @ lovinglinux:
Well, so where do we have to report it so someone can change it?!

Ubuntu [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)
Opera [https://bugs.opera.com/wizarddesktop/](https://bugs.opera.com/wizarddesktop/)

---

### Post by whatthefunk on 2012-04-10
KDE: [https://bugs.kde.org/enter_bug.cgi?format=guided](https://bugs.kde.org/enter_bug.cgi?format=guided)

---

### Post by Chip88 on 2012-04-13
Someone reported the bug already?!

---

### Post by lovinglinux on 2012-04-13
> **Chip88 said:**
> Someone reported the bug already?!

I didn't.

---

