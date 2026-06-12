---
title: "unRAR?"
date: 2009-08-09
forum: General Help
---

### Post by audiologic on 2009-08-09
hello all, and thanks ahead of time for the help.

I got an installation of a program dragged out over 21 .rar files, but when I try to extract [have both rar and unrar installed already] it comes out 21 individual folders, and none of the installs work...already did some research and know how to get the program running once I have the actual installation, but instead of extracting to just one point, it actually extracts each individual rar file to its own folder.

brand new to this, what do I do?

thanks again. just switched from windows vista [bleck] and already love this thing, I just gotta poke around a bit...but yeah I'm just trying to extract them all into ONE file, or however the heck it works in windows.

---

### Post by P4man on 2009-08-09
Normally you can just open any of those rar archives, and extract the file(s), and it will use all 21 rar files to rebuild the original. If it doesn't do that, i fear the rar archive is corrupted or not made the right way. It works the same on linux as on windows afaik.

---

### Post by nikhilbhardwaj on 2009-08-09
you can try
```

unrar x nameOfFirstRarFileInTheSequence
```

for example if the files are named abc.00 abc.01 and so on
then you could do 
unrar x abc.00

change into the directory where you have these files first

---

### Post by jocko on 2009-08-09
Must be something wrong with the archive. You should  be able to just right click ONE of the files and select &quot;extract here&quot;, and all the files in the archive would be extracted and merged properly.
But, just to try another way, try from a terminal:
```
cd [COLOR=Blue]/path/to/files[/COLOR]
unrar x [COLOR=Blue]filename.rar[/COLOR]
```Change [COLOR=Blue]/path/to/files[/COLOR] to the actual path to the folder that contains the archive, and [COLOR=Blue]filename[/COLOR] to the actual filename of one of the .rar files.

---

### Post by audiologic on 2009-08-09
got it. i was selecting all of them, and unzipping them. when i did just the one it worked.

lol @ me well thankks guys

---

