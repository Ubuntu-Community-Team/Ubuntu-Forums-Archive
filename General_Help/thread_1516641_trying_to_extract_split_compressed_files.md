---
title: "trying to extract split compressed files"
date: 2010-06-24
forum: General Help
---

### Post by mastercho on 2010-06-24
hello all, im trying to reconstruct / extract a file that was too large to fit onto a floppy, used 7zip to create and split the file into multiple parts in tar.bzip format. this was done in windows.

Then moved all the parts of the file to tiny linux on a really old laptop. no cd drive, no usb or network. so have to rely on floppy drive.

i do know that reconstruction while extracting using commands is possible. but not working.

tried tar -xMf file.tar.001 but nothing.

any and all help appreciated.

---

### Post by nexes128 on 2010-06-24
Did you compress the files in tar format or in 7z format?
Someone correct me if I'm wrong but i do not believe tar can extract something that was compressed with the 7z algorithm

-----
If tar can't extract 7z(which i beleive) you will have to install the 7z decompressor via the following command

```
sudo apt-get install p7zip-full
```

---

### Post by mastercho on 2010-06-24
yeah, would try that but have no internet access on that particular machine. currently trying plip to transfer the files.

---

