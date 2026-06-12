---
title: "copied cd files not modifiable"
date: 2010-03-16
forum: General Help
---

### Post by MatadorMac on 2010-03-16
Good day.

I am fairly new to Ubuntu (running away from XP) and really like Karmic and have had few issues since setting up a dual boot machine a month ago.

Recently, I coped a cd's worth of images to my documents folder for editing.  All the copied files were shown with a "locked" icon.  I tried to set permissions for the master folder and checked "apply permissions to folders within" but many files were not successfully updated to unlocked status.  In fact I seem to have to do everything (permission changing) by hand for any nested layer deeper than 2 layers of folders deep.

Many times the permission changing was unsuccessful and had to be redone one file at a time.

This hasn't happened before although I don't remember copying files from a CD either before.

My login gives me administrator rights and I am the only user on the machine (other than root of course).

Advice? Guidance?

Thank you

Matadormac
Alcalde, NM

---

### Post by BbUiDgZ on 2010-03-16
> **MatadorMac said:**
> Good day.

I am fairly new to Ubuntu (running away from XP) and really like Karmic and have had few issues since setting up a dual boot machine a month ago.

Recently, I coped a cd's worth of images to my documents folder for editing.  All the copied files were shown with a "locked" icon.  I tried to set permissions for the master folder and checked "apply permissions to folders within" but many files were not successfully updated to unlocked status.  In fact I seem to have to do everything (permission changing) by hand for any nested layer deeper than 2 layers of folders deep.

Many times the permission changing was unsuccessful and had to be redone one file at a time.

This hasn't happened before although I don't remember copying files from a CD either before.

My login gives me administrator rights and I am the only user on the machine (other than root of course).

Advice? Guidance?

Thank you

Matadormac
Alcalde, NM

open terminal and change to the location of your files:
```
cd /path/to/your/files
```
and type: (replace username with your username)
```
sudo chown -R username:users *
```
now in the same folder do:
```
chmod -R 755 *
```

---

### Post by ajgreeny on 2010-03-16
On the main folder that you have copied the files to, you may need to change file ownership and permissions. This is much easier in the terminal than with a gui.

Assuming the files are not owned by yourself, you will need to do the first part with root permissions with ```
sudo chown -R username:username /home/username/Documents
```changing where I have put *username* to the username you use, and the Documents folder to whatever yours is called (don't forget it's case sensitive).

You may then need to make sure everything is read/write enabled for you, which you can do with ```
chmod -R 755 /home/username/Documents
```sudo should not be needed here as all the files and folders will now belong to you already.

---

### Post by BbUiDgZ on 2010-03-18
> **ajgreeny said:**
> On the main folder that you have copied the files to, you may need to change file ownership and permissions. This is much easier in the terminal than with a gui.

Assuming the files are not owned by yourself, you will need to do the first part with root permissions with ```
sudo chown -R username:username /home/username/Documents
```changing where I have put *username* to the username you use, and the Documents folder to whatever yours is called (don't forget it's case sensitive).

You may then need to make sure everything is read/write enabled for you, which you can do with ```
chmod -R 755 /home/username/Documents
```sudo should not be needed here as all the files and folders will now belong to you already.

what i said only said better :oops:

---

### Post by MatadorMac on 2010-03-18
Than you all.  I will do so with the next batch of copied files.

It is so nice to get such community support!!

Matadormac
Alcalde, NM

---

