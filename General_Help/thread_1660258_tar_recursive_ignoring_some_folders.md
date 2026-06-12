---
title: "tar recursive ignoring some folders?"
date: 2011-01-05
forum: General Help
---

### Post by sohlinux on 2011-01-05
I have 200 folders I would like to tar them but ignore 20 of the folders

I have folders001 up to folder200 and I would like to ignore folder060 to folder080

the following code works ok but I would have to type all the folders in and there are 180 of them

```
tar cvzf /home/allfolders.tgz folder001 folder002 folder003 
```

---

### Post by Chris Seelig on 2011-01-05
If you type '**man tar**' you will get the manual page for the tar command. the option you are looking for is probably** -X**, although there are other options you might use, most of them start **--exclude**.....

Chris

---

### Post by sohlinux on 2011-01-05
> **Chris Seelig said:**
> If you type '**man tar**' you will get the manual page for the tar command. the option you are looking for is probably** -X**, although there are other options you might use, most of them start **--exclude**.....

Chris


Thanks, 

I did spend quite a while reading the man page but it isn't too clear, anyway it turns out it needs full paths for excluding directories

the following will tar all files and folders inside /home/001 excluding folders 004 and 005 to /home/002/tar_name.tgz

```
tar -cvzf /home/002/all_folders_less_004_and_005.tgz /home/001 --exclude "/home/001/004" --exclude "/home/001/005"

```

---

