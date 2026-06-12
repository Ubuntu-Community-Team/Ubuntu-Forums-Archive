---
title: "No Permission to Save to External Hard Drive"
date: 2010-10-14
forum: General Help
---

### Post by Transmutable on 2010-10-14
I have a hard drive with 10.04 that won't boot. It also will not boot from a CD. In a rather elaborate workaround, I can boot a second computer from a LiveCD and connect the hard drive as an external hard drive. I want to copy my documents and stuff from the laptop hard drive to the actual external hard drive (so I can reformat), but half of the things are "protected" and I don't have permission to copy them. What's weird is that not everything is protected, but I can't discern any pattern to it.

How can I copy protected files from one drive to another?

---

### Post by andrewthomas on 2010-10-14
If you mount the drive, then open nautilus with 

```
gksu nautilus
```then you should be able to navigate to the mounted drive and copy from it.  

It may help to right-click on whatever you want to copy them to and 'open in new window' from within the privileged nautilus window so you can drag-and-drop the files.

---

### Post by Transmutable on 2010-10-14
Nope, doesn't work. This is the error I get:

```
The folder "School" cannot be handled because you do not have permissions to read it.
```

I have been able to c&p or click&drag some things, like a small folder of word documents.

ETA: Huh. There seems to be some correlation between filetypes I can open (.jpg, .doc, .pdf) and files I can copy. But if I can't open the file (like an .mp3) I can't copy it.

---

### Post by andrewthomas on 2010-10-15
When you mount the drive, it should be mounted under /media

What is the error if you ?

```
sudo cp /media/path/to/file /path/to/directory
```

---

