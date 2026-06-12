---
title: "Questing for a lost file folder"
date: 2010-08-04
forum: General Help
---

### Post by OxentroT on 2010-08-04
I am really worried that I may have deleted this massive collection of audio files. I KNOW I stashed it somewhere safe, however I cannot seem to find it. I remember in earlier versions of Ubuntu there was a file search app similar to windows' file finder that allows you to search for files by key word. I cannot seem to find  that one either..  Getting down to brass tacks I am wondering if there is an app that I can install to allow me to search for this folder by keyword. I'm not sure why Ubuntu would have gotten rid of this feature.  

Thank You for any info!):P

---

### Post by WorMzy on 2010-08-04
Can you remember what the folder's name was, or the name of one of the files? If so, open a terminal and run:
```
sudo updatedb && locate [COLOR="Red"]<FILE/FOLDERNAME>[/COLOR] | less
``` If the name is distinctive, then you'll probably find it right away, but if it's a more common name, then you may get a huge list of results that you'll need to look through.

Or you could run
```
sudo updatedb && locate .mp3 | less
``` to get a list of all mp3 tracks and their locations, that Ubuntu can find.

Oh, and you can press "q" to exit the results.

---

### Post by celldweller1591 on 2010-08-04
there is a default search option in Ubuntu top panel of "Computer" just in left of refresh button. It is denoted by a magnifying glass icon. Click it and search whatever you want. i always use it and it wirks perfectly.

---

### Post by OxentroT on 2010-08-07
Thankyou!

---

