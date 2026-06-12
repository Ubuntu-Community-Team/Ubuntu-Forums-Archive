---
title: "Tomboy notes - sync to ubuntu one with 10.04?"
date: 2010-11-09
forum: General Help
---

### Post by Roasted on 2010-11-09
At home I run 10.10 and set it up last night to sync to Ubuntu one. I figured this would be handy since I often work in the evenings on work projects while at home. My work laptop is 10.04, and I'd prefer to keep it that way with it being an LTS and all, as stable as 10.10 seems to be.

Problem is within the Tomboy preference menu I don't see a way to sync my notes to Ubuntu One. I even got the latest PPA, but no dice.

Any ideas?

---

### Post by ajgreeny on 2010-11-09
You may need to sync the files:-
```
/home/<user>/.local/share/tomboy/585e460d-78e9-49a6-a7b6-05735660c619.note
/home/<user>/.local/share/tomboy/5b7f8776-ec36-4e04-b042-e8fe39445c1f.note
/home/<user>/.local/share/tomboy/bba2dc9b-8488-4752-8dcb-807f318db48b.note
```which is where the actual notes are backed up.
Note- yours will have different alpha-numeric IDs to mine.

If that does not work, I have no idea.

---

### Post by Roasted on 2010-11-09
> **ajgreeny said:**
> You may need to sync the files:-
```
/home/<user>/.local/share/tomboy/585e460d-78e9-49a6-a7b6-05735660c619.note
/home/<user>/.local/share/tomboy/5b7f8776-ec36-4e04-b042-e8fe39445c1f.note
/home/<user>/.local/share/tomboy/bba2dc9b-8488-4752-8dcb-807f318db48b.note
```which is where the actual notes are backed up.
Note- yours will have different alpha-numeric IDs to mine.

If that does not work, I have no idea.

Not sure I follow... you say you may need to sync those files... but to where exactly?

---

### Post by ajgreeny on 2010-11-09
> **Roasted said:**
> Not sure I follow... you say you may need to sync those files... but to where exactly?
To ubuntu-one, which is what I thought you were asking about.

Don't ask me how to do that as I have never used ubuntu-one, but I assumed you had as you were talking about syncing your tomboy notes.  All I did was point you to the path of your notes, just in case you had not found them.

---

### Post by Roasted on 2010-11-09
> **ajgreeny said:**
> To ubuntu-one, which is what I thought you were asking about.

Don't ask me how to do that as I have never used ubuntu-one, but I assumed you had as you were talking about syncing your tomboy notes.  All I did was point you to the path of your notes, just in case you had not found them.

Yeah I want them to go to Ubuntu One. The confusing part is in Tomboy notes in 10.10, there's an option right in the preferences for that. In 10.04, even latest PPA, not so much... :(

---

### Post by wojox on 2010-11-09
Have you looked here [UbuntuOne/Tutorials/Notes]("https://wiki.ubuntu.com/UbuntuOne/Tutorials/Notes")

---

### Post by pmibal on 2011-01-06
Same issue here.  Hoping they will update Tomboy on 10.04

---

