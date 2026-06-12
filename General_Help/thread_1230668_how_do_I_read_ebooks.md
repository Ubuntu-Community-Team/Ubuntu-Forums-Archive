---
title: "how do I read ebooks"
date: 2009-08-03
forum: General Help
---

### Post by huntis619 on 2009-08-03
what program do I use for reading ebooks, chm files comic books and any other form of reading material files?

---

### Post by llamabr on 2009-08-03
Most ebooks come as pdf's right?  I like xpdf.

I'm not familiar with chm files,  but here's some hints:

[http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=vOk&q=chm+files+ubuntu&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=vOk&q=chm+files+ubuntu&aq=f&oq=&aqi=)

Looks like they want you to convert them to pdf, too.

---

### Post by wojox on 2009-08-03
Look for chm viewer in Synaptic.
.pdf's load with evince already installed.

---

### Post by llamabr on 2009-08-03
```
brock@hops:~$ apt-cache search chm viewer
x11-apps - X applications
chmsee - A chm file viewer written in GTK+
claws-mail-html2-viewer - HTML mail/attachment viewer for Claws Mail mailer
gnochm - CHM file viewer for GNOME
kchmviewer - CHM viewer for KDE
kchmviewer-nokde - CHM viewer for KDE
libchm-bin - library for dealing with Microsoft CHM files (test programs)
libchm-dev - library for dealing with Microsoft CHM files (development)
libchm1 - library for dealing with Microsoft CHM files
xchm - Compiled HTML Help (CHM) file viewer for X
ktnef - KDE TNEF viewer
brock@hops:~$ 

```

I don't know anything about chm files, but you can either view them, or convert them, as wojox mentioned.

---

### Post by jmszr on 2009-08-03
huntis619,

"fbreader" is available in the repositories and looks like it would suit your needs.

---

### Post by nah40 on 2009-08-03
Tom's etext reader.
it works in Wine

---

### Post by huntis619 on 2009-08-03
thank you. I used xchm and it works, but what about cbr files? Is there a universal program to convert these files or a universal reader?

---

### Post by nah40 on 2009-08-03
Tom's Etext Reader is like reading a book.
It looks like a book.
It displays many different formats.
As I said, it works in Wine.
Try it or not, up to you.

---

### Post by huntis619 on 2009-08-03
Is Tom's Etext reader available in synaptic?

---

### Post by nah40 on 2009-08-03
no, it  is a windows application.
Google for it.
I am now trying fbreader which i was not aware of.

---

### Post by y-lee on 2009-08-03
> **huntis619 said:**
> thank you. I used xchm and it works, but what about cbr files? Is there a universal program to convert these files or a universal reader?

you should be able to open cbr files in evince document viewer in gnome. Also you may be interested in [Comix]("http://comix.sourceforge.net/") :D

Good luck.

---

### Post by finch127 on 2009-08-03
chmsee will let you read chm's, its the only one i have found that works. in fact i think its even in the repos

---

### Post by Bonster on 2009-08-03
cbr/cbz are actually rar/zip files (just rename if u like). Is just the comic book world use it to store images inside. U can use 'Comix' to read these without extracting them which means u save space also.

---

### Post by scouser73 on 2009-08-04
If you don't like using Evince to read PDF's then you can install [[COLOR="Red"]**Adobe Reader**[/COLOR]]("http://get.adobe.com/uk/reader/otherversions/"), once you're on the site you have to select which operating system you're on, usethe drop-down menu and scroll to **Linux -x86 (.deb)**, then select your language then press continue.

---

### Post by psablo on 2009-08-04
FBReader is okay, but I'd like to get Calibre running: [http://calibre.kovidgoyal.net](http://calibre.kovidgoyal.net)

Has Anyone been through this install that can help.
I seem to have some dependency issues, perhaps with podofo-0.7.0.

---

