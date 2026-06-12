---
title: "Zip makes files bigger?"
date: 2011-12-13
forum: General Help
---

### Post by NoBugs! on 2011-12-13
A strange thing happens when I try to zip a certain directory... The right click - compress fails with an error, and the command line "zip -r output.zip foldername" successfully makes a zip, but in properties box, it appears to be about 16mb bigger than the original zip?!

---

### Post by hwttdz on 2011-12-14
There are certain cases in which this can happen. You can try some other compression options, tar+gzip being the sort of linux standard.  tar+xz being a newer version that's gaining a lot of popularity.  I'm personally fond of tar+lrzip, but that's sort of uncommon.  It's likely that either 
1) zip does not handle a large number of small files well, and that's what you have in the directory, or 
2) the files are nearly incompressible, in which case you wouldn't expect to have much better luck using another method. 
3) I suppose it's also possible zip is dereferencing symbolic links, replacing one copy of a file with two copies.  
4) Any of the multidunious things I haven't thought of.

---

### Post by mcduck on 2011-12-14
If you are trying to compress files that are already compressed data (most image files, MP3's, video files etc.) then it's quite normal that the resulting archive is larger than originals. The lossless compression method can't compress the data any smaller than it already is, and the archive contains some metadata of it's own so you end with larger file than the originals.

---

### Post by seawolf167 on 2011-12-14
> **mcduck said:**
> If you are trying to compress files that are already compressed data (most image files, MP3's, video files etc.) then it's quite normal that the resulting archive is larger than originals. The lossless compression method can't compress the data any smaller than it already is, and the archive contains some metadata of it's own so you end with larger file than the originals.

Aye - came here to say this.

The only reason (IMO) to zip (among other things) compressed images (like .jpg) or music (like .mp3) is so that all the files are contained in one convenient-to-download or archive .zip file. In this case, you'll want to select a no compression option and simply store the files in the archive rather than attempting to re-compress them.

---

