---
title: "READ ONLY not letting me edit"
date: 2009-12-30
forum: General Help
---

### Post by dzwestwindsor on 2009-12-30
Um.. I'm developing in Ruby on Rails. One of my files, I need to edit using bluefish. HOwever, once I edit it, it says that I can't save, its read only. Is there a way for me to take over this file so I can save? Thanks

---

### Post by scragar on 2009-12-30
```
sud chmod +w "**Full path and file name**"
```
sudo = Super user do
chmod = Change permissions mode
+w = Give write access
"BLAH" = filename so it knows what it's changing.

---

### Post by dzwestwindsor on 2009-12-30
can I do it to an entire folder?

---

### Post by taurus on 2009-12-30
Which directory/folder do you have in mind?  Be really careful with permissions especially about the directories/files outside your $HOME.

---

### Post by scragar on 2009-12-30
> **dzwestwindsor said:**
> can I do it to an entire folder?

-R

add that flag for recursive.
```
sudo chmod -R +w "Path To Folder"
```

As was mentioned though, what exactly are you trying to gain write perms for? There's usually a good reason why you aren't given write perms on most of the system, those files simply aren't for normal users to go editing.

---

### Post by dzwestwindsor on 2009-12-30
ok Dont worry i put the folder there myself

---

### Post by dzwestwindsor on 2009-12-30
its not working. it says that I didn't create the file so I can't edit it.

---

