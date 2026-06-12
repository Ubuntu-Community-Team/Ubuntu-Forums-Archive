---
title: "Trash will not delete (not a permissions problem)"
date: 2010-09-21
forum: General Help
---

### Post by Tubbs on 2010-09-21
I recently tried to delete some files off of my USB drive and it was being glitchy and really slow so I pulled the drive out and put it back in so it would read normally again. I now have an "untitled folder" in my trash that can't be deleted, and the error says "no such file or directory". Unlike a lot of the other problems I've read with not being able to delete the trash files, I don't think this is a permissions problem.

I probably made a stupid mistake and went into the .Trash-1000 folder for the USB drive itself and tried to delete the files, but each time I did that it just duplicated the original folder and renamed it, and now I can't delete those files either! I need some serious help, here.

---

### Post by WorMzy on 2010-09-21
Either use the command line to "rm" the folder, or press Shift+Delete to permanently delete (skip the wastebasket) the folder from within Nautilus.

---

### Post by tgm4883 on 2010-09-21
I'd just delete the .Trash-1000 folder. It should get recreated when you delete something again

---

### Post by garvinrick4 on 2010-09-21
You can open anything in nautilus and go to Edit/preferences to behavior tab and check the and delete button. On right click you can then bypass trash and delete. Hope that helps.

---

### Post by Tubbs on 2010-09-21
> **tgm4883 said:**
> I'd just delete the .Trash-1000 folder. It should get recreated when you delete something againI don't know why I didn't think of this before, but it worked. Thanks a bunch. :popcorn:

---

