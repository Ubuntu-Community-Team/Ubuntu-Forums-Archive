---
title: "Tomboy notes stored outside home directory"
date: 2010-07-03
forum: General Help
---

### Post by gusanto on 2010-07-03
Dear all,
I want to store all my Tomboy notes not on the default directory but I want to put them on a shared partition (I'm dual booting Vista and Ubuntu 10.04). The scenario is that I want to keep the same notes accessible from both Vista and Ubuntu 10.04). So I created a directory on the shared partition (FAT32 partition): /media/STORAGE/Tomboy_notes and store the notes there.
On its website, it says "On any operating system, you can override the location of the note directory by setting the TOMBOY_PATH environment variable" but unfortunately I don't know how to do it (I'm blind on this thing).
Any guide to solve the problem is much appreciated.

(Tomboy 1.2.1 running on Ubuntu 10.04)

---

### Post by sgosnell on 2010-07-03
The way I do it is to open the Tomboy preferences, click on the Synchronization tab, and select Local folder.  Browse to the folder you want and select it, and your notes will be synched there.  I use my Dropbox folder, so I can access the notes from any computer that has Dropbox installed, Windows or Linux.

---

### Post by gusanto on 2010-07-13
The solution is published here [http://gusantov.blogspot.com/2010/07/storing-notes-of-tomboy-on-different.html](http://gusantov.blogspot.com/2010/07/storing-notes-of-tomboy-on-different.html)

---

### Post by sgosnell on 2010-07-13
What font are you using on that page?  It's not readable in Firefox.  I can copy it, paste it into gedit, and read it, but the page itself is can't be read at all, at least on my system.  I have preferences set to use the font the page uses, so I should be able to read it, but I just get random ASCII characters for most of it.

---

### Post by dcstar on 2010-07-14
> **sgosnell said:**
> What font are you using on that page?  It's not readable in Firefox.  I can copy it, paste it into gedit, and read it, but the page itself is can't be read at all, at least on my system.  I have preferences set to use the font the page uses, so I should be able to read it, but I just get random ASCII characters for most of it.

That's what happens when fools use HTML code like this:

```
<span style="font-family: webdings;">
```

---

