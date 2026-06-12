---
title: "Folder wont delete."
date: 2010-05-09
forum: General Help
---

### Post by BadlyNeedHelp on 2010-05-09
SO after using Testdisk to recover some images, the folders recup_dir.1 & 2 have saved in my FIle System area, when ever I try to press delete noting happens. I have also tried 

rm -f -r 

rm -f -f

It still dont delete, I have also deleted my user account and made a new one, but the files are still there.

How do i delete them?

---

### Post by howefield on 2010-05-09
If the folders aren't in your /home folder, you may need to use sudo to remove them, eg

```
sudo rm -r /path_to_folder
```

---

### Post by BadlyNeedHelp on 2010-05-09
COuld you write the code out for me, its confusing. Sorry I am a noob.

The folders i need to delete are

recup_dir.1

recup_dir.2

---

### Post by quadproc on 2010-05-09
> **BadlyNeedHelp said:**
> 
recup_dir.1

recup_dir.2
If these two files are not owned by you then you will need to use sudo.  In any event, you may need to set up the permissions on the directory which contains them to allow write and perhaps also execute for the world.

Assuming that these files are in a directory called /home/yourusername/here, you would do
```
sudo cd /home/yourusername/here
sudo rm recup_dir.[12]
```If the system complains about no access rights then you'll need to chmod the appropriate directory(s) to allow such access.

One other consideration: you might want to destroy the data rather than just removing it.  Removed files can usually be recovered by someone who knows how.  To avoid this problem you can use the shred command.

quadproc

---

### Post by howefield on 2010-05-09
> **BadlyNeedHelp said:**
> COuld you write the code out for me

If it is too difficult to work out, you could open Nautilus with elevated rights, navigate to the folders and delete.

Open a terminal and type

```
gksudo nautilus
```

Then close nautilus, you don't want to be doing damage...

---

