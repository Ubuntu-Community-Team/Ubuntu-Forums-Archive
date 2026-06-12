---
title: "How to EDIT .iso contents?"
date: 2011-06-30
forum: General Help
---

### Post by Lexus45 on 2011-06-30
Hello all.

I have a question - what's the best way to *edit* the contents of an .iso image ?
Yes, I know how to mount it and navigate through files and folders. But it's read-only. Mounting with "rw" option also doesn't help.

I've heard about 1) mounting, 2) coping everything to a separate directory 3) editing some files, 4) making a new .iso image.

Are there any other variants?

---

### Post by blueridgedog on 2011-06-30
Assuming you have the iso file on your local hard disk, then the method here: [http://www.linuxquestions.org/questions/fedora-35/mounting-an-iso-image-and-editing-it-463906/](http://www.linuxquestions.org/questions/fedora-35/mounting-an-iso-image-and-editing-it-463906/) is about as simple as I think you are going to get in Linux.

---

### Post by yetiman64 on 2011-06-30
"ISO Master" from the repos. Easy to open an existing iso, add/remove contents, then save as an iso again.

Edit: not sure if it will save bootable images though.[s] A test here with a distro image suggests it may not.[/s] Retested, it appears ok. Test carefully with bootable images. What sort of images do you need to edit OP ?

---

### Post by Lexus45 on 2011-07-05
The problem was solved. I used the "mkisofs" command. But in the first time I haven't added the dot at the end of the command. But it is necessary. That's why it didn't work :-D

> **blueridgedog said:**
> Assuming you have the iso file on your local hard disk, then the method here: [http://www.linuxquestions.org/questions/fedora-35/mounting-an-iso-image-and-editing-it-463906/](http://www.linuxquestions.org/questions/fedora-35/mounting-an-iso-image-and-editing-it-463906/) is about as simple as I think you are going to get in Linux.
Thank you, but I know how to mount isos ;-) I wondered how to edit files inside it. And mounting iso makes it read-only, because the "iso9660" filesystem doesn't support write options ;)
> **yetiman64 said:**
> "ISO Master" from the repos. Easy to open an existing iso, add/remove contents, then save as an iso again.

Edit: not sure if it will save bootable images though.[s] A test here with a distro image suggests it may not.[/s] Retested, it appears ok. Test carefully with bootable images. What sort of images do you need to edit OP ?
Thank you for an advice.

---

### Post by blueridgedog on 2011-07-05
> **Lexus45 said:**
> 
Thank you, but I know how to mount isos ;-)

Further in the thread the go over overcoming the read only issue...mostly by copying the directory tree.  What method did you end up using?

---

