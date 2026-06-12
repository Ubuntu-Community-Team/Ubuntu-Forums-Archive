---
title: "Moving downloaded files to correct folder"
date: 2011-08-23
forum: General Help
---

### Post by instant on 2011-08-23
Hi!

I'm looking for a script or a bittorrent client which is able to move a file after downloading and placing it in a specific folder depending on the file type. E.g. moving a newly downloaded movie to "Videos" and an ISO-file to "Files". 

I feel as if i have used a client with this functionality before but can't remember the name.

Since I at the moment use Transmission as my bittorrent client a script would also work since Transmission can run it after finishing the download.

Any ideas? Tried google but didn't really find anything useful, don't really know what to search for either.

/instant

EDIT: Typo

---

### Post by sanderd17 on 2011-08-23
Making a script is very easy. I think you would need something like

```

#! /bin/bash

mv ~/Downloads/*.mp3 ~/Music
mv ~/Downloads/*.odt ~/Documents

```

you do need to make it executable afterwards (can be done with right-clicking and go to file properties).

---

### Post by raja.genupula on 2011-08-23
```
mv folder1 folder2 
``` moves folder1 to folder2 . in torrent applications while adding the torrent you can choose the location to store .

---

### Post by sanderd17 on 2011-08-23
> **raja.genupula said:**
> ```
mv folder1 folder2 
``` moves folder1 to folder2 . in torrent applications while adding the torrent you can choose the location to store .

yep, it works the same with files, a * is a wildcard, and ~ is your home directory.

---

### Post by raja.genupula on 2011-08-23
> **sanderd17 said:**
> yep, it works the same with files, a * is a wildcard, and ~ is your home directory.

Hi Thank you very much .I do remember this .

---

### Post by instant on 2011-08-23
Thanks for the replies!

I'm familiar with scripting to some degree and know that what you guys are suggesting is a solution. Just one thing, is there also a way to move a folder depending on its contents?

Like checking a folders contents, finding an AVI or MKV-file, and moving it to "Videos"? Mostly so that SFV-files, SRT-files and such are kept together with the AVI-file.

---

### Post by raja.genupula on 2011-08-23
> **instant said:**
> Thanks for the replies!

I'm familiar with scripting to some degree and know that what you guys are suggesting is a solution. Just one thing, is there also a way to move a folder depending on its contents?

Like checking a folders contents, finding an AVI or MKV-file, and moving it to "Videos"? Mostly so that SFV-files, SRT-files and such are kept together with the AVI-file.
replace .mp3(format) with what ever the format you want with the same script . suppose do for mkv 
 ```
mv ~/Downloads/*.mkv ~/Video
```

---

### Post by oldos2er on 2011-08-23
Both ktorrent and qbittorent have this function built in.

---

