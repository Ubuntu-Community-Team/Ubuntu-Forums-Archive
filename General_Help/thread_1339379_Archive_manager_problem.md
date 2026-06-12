---
title: "Archive manager problem"
date: 2009-11-27
forum: General Help
---

### Post by hakermania on 2009-11-27
i downloaded a rar file from a site and I tried to unrar it with the Ubuntu archive manager (File Roller 2.28.1). The program could see the file (a MP3 file) but when I go to Extract----> I choose the Desktop folder----->Extract---->View Files there is nothing! It opens the Desktop folder and there is no MP3 file. I go to the console, go to the desktop folder and i type 

ls -al 



but there is no hidden file! Plz help......I don't want to download Izarc...;)

---

### Post by zvacet on 2009-11-27
Type in terminal

```
sudo apt-get install p7zp p7zip-full p7zip-rar
```

After that right click on rar file and select** extract here**.

---

### Post by NFblaze on 2009-11-27
If you double click the mp3 from within the archive does it play?

---

