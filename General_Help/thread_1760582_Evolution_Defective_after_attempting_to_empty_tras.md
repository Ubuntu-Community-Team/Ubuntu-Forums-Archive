---
title: "Evolution Defective after attempting to empty trash"
date: 2011-05-17
forum: General Help
---

### Post by TygerTung on 2011-05-17
I tried to empty the trash on evolution, but it hung for a while then crashed and disappeared

Then when I try to go back into it the window opens for a split second and disappears again.

How can I repair this? I am in a bit of a panic as it has all my emails in it!

Any help would be great!

Cheers,

Sam

---

### Post by claracc on 2011-05-17
You have to look for the file folders.db in ./evolution (I think the complete path is ./evolution/local/mail/ but I am not sure, I am not now in my ubuntu os) and delete  the file folder.db(after closing evolution), then restart evolution and try again to empty trash, I think it has to work now.

---

### Post by TygerTung on 2011-05-17
Thanks, it turns out I had to remove the folders.db file.

It was very difficult to find as you have to go into the .evolution folder from your home folder, but it is hidden, but I found out you can push Ctrl-h and the hidden folders appear.

Removed the file and it works well.

---

