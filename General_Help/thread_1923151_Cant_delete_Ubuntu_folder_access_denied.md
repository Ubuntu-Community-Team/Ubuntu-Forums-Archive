---
title: "Cant delete Ubuntu folder access denied?"
date: 2012-02-10
forum: General Help
---

### Post by bbno3 on 2012-02-10
I am trying to delete a folder named "backup" which i made, i made it to put on my external hard drive but the hard drive isnt the right format for ubuntu so its all failed.... and when i try to delete it, it says access denied.
It has a padlock on the folder icon as well.
Im using Ubuntu 11.10 and the backup program is called lucky backup.

When i look at properties it says the owner of it  is Root.

---

### Post by pr3zident on 2012-02-10
> **bbno3 said:**
> I am trying to delete a folder named "backup" which i made, i made it to put on my external hard drive but the hard drive isnt the right format for ubuntu so its all failed.... and when i try to delete it, it says access denied.
It has a padlock on the folder icon as well.
Im using Ubuntu 11.10 and the backup program is called lucky backup.

When i look at properties it says the owner of it  is Root.


use sudo rm -vr backup
type in your password and it should delete

---

### Post by bbno3 on 2012-02-10
It says there is no such file called "backup"? But i can see it on my desktop >.<

---

### Post by pr3zident on 2012-02-10
> **bbno3 said:**
> It says there is no such file called "backup"? But i can see it on my desktop >.<

cd Desktop ; rm -vr "backup"

---

### Post by bbno3 on 2012-02-10
rm: descend into write protected directory 'backup'? *i pressed enter*
~/Desktop$

---

### Post by Elaztic on 2012-02-10
If you are new to Linux/Ubuntu or the command line (CLI) then you might want to consider familiarizing yourself with some of the common commands.

So if your 'backup' folder is on your desktop you could do this from the command line:
cd Desktop   <-- cd = change directory (to Desktop)
rm backup   <-- rm = remove

If your backup directory contains files you have to specify 'recursive' so it deletes the contents and then the directory.
If your directory has the owner 'root' then you have to have administator rights to delete it. So your remove command might look something like this:

sudo rm -r backup   <-- sudo = admin rights, -r = recursive

For a full list of options for a command you can use --help e.g.
rm --help

---

### Post by lolpenguin on 2012-02-10
> **Elaztic said:**
> If you are new to Linux/Ubuntu or the command line (CLI) then you might want to consider familiarizing yourself with some of the common commands.

[http://www.gnu.org/software/coreutils/manual/coreutils.html]("http://www.gnu.org/software/coreutils/manual/coreutils.html")

---

