---
title: "No space left on partition to install updates"
date: 2010-11-29
forum: General Help
---

### Post by TheDarkSix on 2010-11-29
So i am using xubuntu from wubi and i need more space to instal all the important security updates, How do i free up space? i think i made a mistake and did not allow it much space when i made the partition for it

---

### Post by mikewhatever on 2010-11-29
You can free some space by deleting or moving files from your home folder or by uninstalling programs, unneeded kernels, etc. The following command will clean the cached installation packages.
```
sudo apt-get clean
```

That said, if the allocated space is too small, you'd have to reinstall, as you can't reallocate it. Consider doing a proper non-wubi installation if you plan on using Ubuntu.

---

### Post by TheDarkSix on 2010-11-29
I have entered that command before and still there is not enough space, So i must uninstall my install of xubuntu and reinstall it again? 

I really don't use too much space on my harddrive, it's 160gb and my install of windows does not use anything i just play some games, so i have enough space to hold both, i just was not thinking when i was allocating space

---

### Post by holycow131415 on 2010-11-29
He means to dual boot instead of installing ubuntu as a program under windows. So yes, you should back up your files, uninstall ubuntu in the control panel, boot off ubuntu disc and select side by side.

---

### Post by TheDarkSix on 2010-12-03
QUick question, Since i was very lazy to reinstall i've been surfing without security updates, is this a bad idea or what?

---

