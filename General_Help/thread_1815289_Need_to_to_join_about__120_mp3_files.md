---
title: "Need to to join about  120 mp3 files"
date: 2011-07-31
forum: General Help
---

### Post by p3aul on 2011-07-31
Is there a joining utility, preferably with a GUI that will allow me to join a hugh number(over 100) small mp3 files without having to list or open each file?
Thanks,
Paul

---

### Post by dim_hyder on 2011-07-31
Copy all MP3s that you want to join into a directory. Open terminal and cd to this directory.

to merge:

cat *.mp3 > output.mp3

not sure what order they will be joined in - alphabetical??

---

### Post by dim_hyder on 2011-07-31
Tested - yes alphabetical (to answer my own question).

---

### Post by decrepit on 2011-07-31
If you want to join them so the sound is continuous.
"audacity" will do it, but it'll be 1 join at a time, and a bit of stuffing around getting them to line up.

---

### Post by vanadium on 2011-07-31
Better use mp3wrap instead of cat. While the file produced with "cat" will generally be playable, it is essentially a corrupt mp3 file.

---

### Post by zero2xiii on 2011-07-31
> **decrepit said:**
> If you want to join them so the sound is continuous.
"audacity" will do it, but it'll be 1 join at a time, and a bit of stuffing around getting them to line up.

This will yield best results,

Google "audacity chains". This can be applied to a folder of files, should be able to envoke it to combine a serious number of audio files to a single file.

---

### Post by p3aul on 2011-07-31
Thanks everyone!
I did try cat using cat *.mp3 > myfile.mp3 and it seemed to work although since the resulting file was about 10 hours long I didn't test it fully.

The edit chains command in audacity was a little too obtuse and I couldn't figure it out.

the mp3wrap command worked smoothly, once I figured it out. 

I'll go with that one since it was designed for mp3 s and would have the least, if any errors.

Thanks, all for replying!:P
Paul

---

