---
title: "Where does Tomboy Notes store it's data?"
date: 2010-01-30
forum: General Help
---

### Post by jhigz on 2010-01-30
After a prolonged absence, version 4.10, I have started dabbling with Ubuntu again. It was a HDD crashing that sent me down this path. Needless to say, the ability to backup my user data to a second HDD is an important task to me. I'm currently using Back in Time to accomplish this and all is well.



However, there is one thing missing. I can't locate my Tomboy Notes data within the file system. I expected to see a "hidden" folder in my /home, but do not.



Can someone shed some light for me as to where this information is stored so I can back it up as well?



Thanks...

---

### Post by howefield on 2010-01-30
~/.tomboy as .note files.

---

### Post by jhigz on 2010-01-30
Thanks for the reply. That's where I had expected it to be, but I have no .tomboy folder in my home.

---

### Post by wojox on 2010-01-30
Look in /.local/share/tomboy

---

### Post by jhigz on 2010-01-30
That's it! Thank you both...

---

### Post by Halfwalker on 2010-09-11
Strange problem here ...  Tomboy is missing some of the notes.

Ubuntu Karmic x64, up to date.  I noticed that some notes were missing, and went searching.  Lo, the files are in ~/.local/shared/tomboy, but some of them are not being seen or read by Tomboy.

I've removed and added it back to the panel, to no avail.  How does Tomboy index or read the notes files ?  I have edited some of them manually now and then, when I was away from the box and ssh'd in.

D.

---

### Post by corrytonapple on 2010-09-11
> **Halfwalker said:**
> Strange problem here ...  Tomboy is missing some of the notes.

Ubuntu Karmic x64, up to date.  I noticed that some notes were missing, and went searching.  Lo, the files are in ~/.local/shared/tomboy, but some of them are not being seen or read by Tomboy.

I've removed and added it back to the panel, to no avail.  How does Tomboy index or read the notes files ?  I have edited some of them manually now and then, when I was away from the box and ssh'd in.

D.
Start a new thread please.

---

