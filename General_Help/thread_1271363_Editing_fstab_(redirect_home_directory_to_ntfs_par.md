---
title: "Editing fstab (redirect home directory to ntfs partition)"
date: 2009-09-20
forum: General Help
---

### Post by Alan502 on 2009-09-20
Hi, finally i got ubuntu running today (after some very weird problems in my disk partitioning)

Well, im happy with it. But now, i want to combine my /home and My Documents directories so i can have all my data in one place. Apparently i can redirect the /home directory editing fstab. Looked for it but all i have found are tutorials for ubuntu 8.10 when we are currently in 9.04. Help will be appreciated, thanks :D

---

### Post by tgeer43 on 2009-09-21
I don't think you want to do that because Windows does not handle file attributes in the same way as Linux. Stuff like file ownerships, permissions, sticky bits, etc.

You could use links/shortcuts to the folders on each system to create an illusion of the same thing.

tgeer

---

### Post by hydrotemplar on 2009-09-21
not a good idea if it's even doable, but what you can look into is consolidating it all into your /home and using Ext2 IFS ([http://www.fs-driver.org/](http://www.fs-driver.org/)) you can just access that from Windows.

---

### Post by hydrotemplar on 2009-09-21
besides, if you just mounted the ntfs partition as your home, you'd have the nightmare of having the Entire windows file system merged with your home folder, not just your documents...

---

### Post by CatKiller on 2009-09-21
I agree with everyone else; using NTFS for your Home folder is a Bad Plan.

Probably the simplest way is to mount your NTFS partition somewhere else and symlink your My Documents folder to ~/Documents. That way you get the behaviour that you're after without breaking anything.

---

### Post by beastrace91 on 2009-09-21
> **CatKiller said:**
> Probably the simplest way is to mount your NTFS partition somewhere else and symlink your My Documents folder to ~/Documents. That way you get the behaviour that you're after without breaking anything.

I'd like to second this one - this is how I configured my roomate's dual boot laptop and it works quiet well. Just create a static point to mount your Windows drive to (Typically I just create a folder in /mnt/Winblows) and then replace your Ubuntu documents with a symlink to your Windows My Docs.

And just as an FYI many things such as editing fstab and creating symlinks are the same between Ubuntu 8.10 and 9.04 so what ever guide you found for Ibex should still apply to Jaunty for fstab

~Jeff

---

