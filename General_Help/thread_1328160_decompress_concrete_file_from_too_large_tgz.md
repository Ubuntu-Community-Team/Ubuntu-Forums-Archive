---
title: "decompress concrete file from too large tgz"
date: 2009-11-16
forum: General Help
---

### Post by parrimin on 2009-11-16
Hi, I have some data backup in an external (usb) hdd drive.
I have lost one concrete file from my server, and im trying to find this file in my external driver, but the backed up file is a 400GB tgz. The problem is that i am actually running decompress from a window machine with winrar (windows machine) in another hdd drive, and it says it will end tomorrow! Theoretically in winrar i can navigate for the file, but after 30 mins trying to open the tgz file, it says it has read 2%, so i cant navigate to the concrete file and extract it.
In linux i saw i can open a tgz with ```
tar -tz fichero.tgz
``` to see the contents, but can i decompress a concrete file only?

---

### Post by parrimin on 2009-11-16
Oh, i forgot to say i have a command line install without interface, i mean, no gnome, no kde or similars

---

### Post by my_key on 2009-11-16
After "-x" you can specify a filename or directory argument, then after that you specify the filename of the tarfile to extract.

Check "man tar".

So something like:
tar -[otheroptions]x filetoextract largetarfile.tgz

---

### Post by parrimin on 2009-11-16
thanks my_key, im trying:
tar -xzf home/repos largetarfile.tgz and it says:
tar: home/repositorio/CVC: Can't open: The file or folder doesn't exist
tar: The error is not recuperable: Going out now.
tar: Child returned status 2
tar: largetarfile.tgz: Can't find the file

---

### Post by parrimin on 2009-11-17
I have solved googling. The right syntax is:
tar -xvf mylargeBckp.tgz /home/repos/myknownfolder

---

### Post by parrimin on 2010-03-05
Hey, there was an error on my last solution. The right syntax is:
```
tar -x home/repos/myFolder -zf myFile.tgz 
```

or

```
tar -x home/repos/mySingleFile -zf myFile.tgz 
```

Of course home/repos can be another folder like usr/myUser , or something like *.html. What is important is to ommit the first "/". So is myFolder/otherFolder/ and not /myFolder/otherFolder

---

