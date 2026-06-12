---
title: "File Could not delete"
date: 2010-12-23
forum: General Help
---

### Post by chitragurung on 2010-12-23
Hello,

I used external hard drive to keep my back up and my machine stored same file in media folder of my machine which occupies all my hard disk space. Now I wanted to delete it but I could not delete it. How can I delete it to free up the space

---

### Post by TeoBigusGeekus on 2010-12-23
```
sudo rm /path/to/file/filename.extension
```

---

### Post by chitragurung on 2010-12-23
Folder is located in file system folder so I try your command but out put is as follows.


ul
[sudo] password for chitra: 
rm: cannot remove `/home/media/CHIRAGO/2010-11-30_00.00.03.469052.chitra.ful': No such file or directory
chitra@chitra:~$ 2010-11-30_00.00.03.469052.chitra.ful
bash: 2010-11-30_00.00.03.469052.chitra.ful: command not found
chitra@chitra:~$ 2010-11-30_00.00.03.469052.chitra.ful sudo rm /home/media/CHIRAGO/2010-11-30_00.00.03.469052.chitra.ful
bash: 2010-11-30_00.00.03.469052.chitra.ful: command not found
chitra@chitra:~$ sudo rm /home/media/CHIRAGO/ sudo rm /home/media/CHIRAGO/2010-11-30_00.00.03.469052.chitra.ful
rm: cannot remove `/home/media/CHIRAGO/': No such file or directory
rm: cannot remove `sudo': No such file or directory
rm: cannot remove `rm': No such file or directory
rm: cannot remove `/home/media/CHIRAGO/2010-11-30_00.00.03.469052.chitra.ful': No such file or directory
chitra@chitra:~$

---

### Post by Spyderkid on 2010-12-23
go to the directory above the hard drive and run...

```
shred --remove -n 1 --zero -v [HARD DRIVE'S NAME] 
```

---

### Post by chitragurung on 2010-12-23
how to go to file system directory ?

---

### Post by WorMzy on 2010-12-23
The file does not exist at that location, are you sure you've got the right address? Normally, partitions are mounted in /media, not /home/media. Try:

```
sudo rm /media/CHIRAGO/2010-11-30_00.00.03.469052.chitra.ful
```

---

### Post by chitragurung on 2010-12-23
It works ! Thank you. I made some syntex error. Now I want to remove empty directory as well.

---

### Post by WorMzy on 2010-12-23
No luck there either, huh?

Are you sure that the partition containing the file is even mounted? What is the output of
```
mount
```?

---

### Post by chitragurung on 2010-12-23
Yes it worked. Thanks. I made some syntex error.

But now I want to remove those folders as well how can I do ?

---

### Post by WorMzy on 2010-12-24
```
sudo rm -r /path/to/folder
```

will remove folders (and their contents). Be careful this command though; if you accidentally delete the wrong folder, then it cannot be easily recovered.

---

### Post by Sidewinder1 on 2010-12-24
If you wish to avoid syntax issues and directory navigation, the GUI method may be easier:
```
gksudo nautilus
```
Provided you are using Nautilus as your file-manager.
**Caution:** Anything you do will be permanent as you will be using it with root privileges and could, therefore "hose" your entire system.

HTH,
Side

---

