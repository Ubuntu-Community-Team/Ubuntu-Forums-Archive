---
title: "Gedit does not read greek - Plz Help me..."
date: 2010-06-20
forum: General Help
---

### Post by hakermania on 2010-06-20
Hello, When I download a file that a Window user has uploaded and contains a .txt file with greek inside it, I cannot read it (the words look like chinese) . Is there any command out there or something I can do for this? Thx in advance!

---

### Post by NCLI on 2010-06-20
Well, you could install Greek language support. Just go to System->Administration->Language Support.

---

### Post by hakermania on 2010-06-20
Nothing seem to happen

[IMG]http://i49.tinypic.com/358tpmp.png[/IMG]

---

### Post by hakermania on 2012-11-11
Am I a bad person if I decide to bump this?

I stopped having this problem because all my friends switched to Linux, but now, in university, there are plenty of persons using Windows and I have to co-operate with them.

I cannot read the txt files they generate in Notepad containing Greek characters. I have installed the Greek Language Support and I've set the Gedit's language to Greek. 

The problem persists.

---

### Post by UAdnan on 2012-11-11
Have you tried installing [Wine](http://www.psychocats.net/ubuntu/wine) and then opening the .txt file with its [Notepad](http://www.winehq.org/docs/wineusr-guide/introduction) ?

---

### Post by hakermania on 2012-11-11
No difference at all:

[IMG]http://i.imgur.com/fYI0i.png[/IMG]

Thanks for trying to help !

---

### Post by Vaphell on 2012-11-11
most likely encoding issue
utf8 (linux) vs windows-1253 (windows)

Open file via File->Open... and set win-1253 as the encoding to be used.

---

### Post by hakermania on 2012-11-11
> **Vaphell said:**
> most likely encoding issue
utf8 (linux) vs windows-1253 (windows)

Open file via File->Open... and set win-1253 as the encoding to be used.

That's all folks!

---

