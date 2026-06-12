---
title: "rar joining doubts"
date: 2010-03-28
forum: General Help
---

### Post by jsriz on 2010-03-28
I download many movies from Internet which are split into 
part01.rar part02.rar................
In old days of windows n winrar I used to get these crc errors  which kept me from joining a corrupted(or is it broken...?)part in the download but 
In ubuntu i noticed that it directly joins the files and i get asynchronous audio-video in the extracted file........
How do I detect these not - so - properly downloaded files so that i can redownload them....
And also winrar had this " keep broken files " option which I dearly miss In ubuntu ......
please tell me what are my options????

---

### Post by kngofbuntu on 2010-03-29
do the same files showing no crc error in ubuntu show errors in windows

---

### Post by jsriz on 2010-03-29
As I told you windows is a thing of past for me 
Can't test it.............

---

### Post by jsriz on 2010-03-30
atleast which is the archiver which can effectively show crc errors

---

### Post by jsriz on 2010-04-04
bump

---

### Post by smokineasy on 2012-12-12
well for the " keep broken files " 
this can be done using terminal (Ctrl+Alt+t) 
cd to folder were file is kept.
in my case (cd Downloads)
then type in (unrar x -kb NameOfFile.part1.rar) and it will unrar in same folder , then open using VLC

---

