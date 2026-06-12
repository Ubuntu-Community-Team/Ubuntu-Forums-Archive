---
title: "Customizing LiveCD - adding other things"
date: 2009-08-06
forum: General Help
---

### Post by Muscovy on 2009-08-06
I'm trying to add a chunk of files like icons to the CD. I tried adding them by using zip -r ./folder_of_stuff ./live/edit/
  It places... most of them. It all seems to before it's compiled. For example, overwritting one icon with another works, overwritting background defaults doesn't, and adding a new theme locks it to all but root.
  Am I doing it wrong?

---

### Post by Mike_IronFist on 2009-08-06
> **Muscovy said:**
> I'm trying to add a chunk of files like icons to the CD. I tried adding them by using zip -r ./folder_of_stuff ./live/edit/
  It places... most of them. It all seems to before it's compiled. For example, overwritting one icon with another works, overwritting background defaults doesn't, and adding a new theme locks it to all but root.
  Am I doing it wrong?

Try to explain things more clearly please.

---

### Post by Muscovy on 2009-08-06
Things go wrong when I add in other files. I can use vim/emacs to edit text-based files, and I can play around with packages, but when I try and do something like copying in a new file, it normally isn't on the CD.
  I've been following the tutorial on the wiki, [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) . I put my files in ~/live/edit, and do it just after the steps of [https://help.ubuntu.com/community/LiveCDCustomization#Prepare%20and%20chroot](https://help.ubuntu.com/community/LiveCDCustomization#Prepare%20and%20chroot) .


  Oh, and another weird problem, the filesystem gains about 1 Gb that it can't find every time I edit a CD.

---

