---
title: "USB drive duplicated after upgrade"
date: 2010-06-07
forum: General Help
---

### Post by barroy on 2010-06-07
I have a USB hard drive that is called "My Book", which was listed in the Media folder whenever it was connected. Since I upgraded to Lucid, I now have a permanent folder/drive called "My Book" with an X over the folder icon, and whenever I connect the hard drive, it is given the name "My Book_". I can't change anything about the new, permanent folder; apparently I don't have permission. This has meant that all the applications that linked to files on the hard drive - Banshee etc - can no longer find the files because the hard drive now has a different name.

Does anyone know why this has happened and what I can do to fix it - ie. get rid of this new 'drive'. I'm guessing that the reason the underscore is added when I plug the drive in is due to the existing, redundant but unmoveable, drive icon. Thanks for any help.

---

### Post by dcstar on 2010-06-08
> **barroy said:**
> I have a USB hard drive that is called "My Book", which was listed in the Media folder whenever it was connected. Since I upgraded to Lucid, I now have a permanent folder/drive called "My Book" with an X over the folder icon, and whenever I connect the hard drive, it is given the name "My Book_". I can't change anything about the new, permanent folder; apparently I don't have permission. This has meant that all the applications that linked to files on the hard drive - Banshee etc - can no longer find the files because the hard drive now has a different name.

Does anyone know why this has happened and what I can do to fix it - ie. get rid of this new 'drive'. I'm guessing that the reason the underscore is added when I plug the drive in is due to the existing, redundant but unmoveable, drive icon. Thanks for any help.

```
gksudo nautilus
```

Go to the /media folder and delete the old name.

---

### Post by barroy on 2010-06-08
perfect, nice one

---

