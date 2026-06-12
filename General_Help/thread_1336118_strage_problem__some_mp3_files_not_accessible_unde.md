---
title: "strage problem:  some mp3 files not accessible under windows"
date: 2009-11-24
forum: General Help
---

### Post by eli_12345 on 2009-11-24
hi,
i encoded an audio cd under ubuntu 9.10 with audio juicer to mp3. the folder with the files is located in an ntfs partition. 
in ubuntu i can play all files in my audio player, copy&paste the files etc. 
when i boot windows 7, all files are visible in the windows explorer, but two of them cannot be played or copy&pasted. 
they should have the same rights so i really don't know why windows is not able to handle exact these two files. 
i even tried to decode them under ubuntu in audacity to wave, but the resulting wav-files are still not accessible under win7.
best,
eli

---

### Post by kircher on 2009-11-24
Is it possible the filenames of those particular files have characters in them that are 'illegal' in Windows? I had the same problem when I transferred a heap of my data to a friend of mine onto his external hard drive with ntfs, and he couldn't open the files, or move them at all. He uses Windows. Check if there are any "funny' characters in the file names. I forget which ones are bad, so I can't give you any specifics

---

### Post by Julita on 2009-11-24
It appears that the number of characters allowed in the name of CD in Linux is longer than in Windows (at least k3b told me so :) ). Maybe you should have renamed it?

---

### Post by eli_12345 on 2009-11-24
Thank you both for your quick helping - you were right, both files had an : in it (the filenames were generated automatically by audio juicer) which i learned now is not valid for filenames in Windows. 
Best

---

