---
title: "Can Linux view images with unicode?"
date: 2012-07-07
forum: General Help
---

### Post by ChaosChris2009 on 2012-07-07
I haven't used a distro in a long while, but I'm wondering.

Can distro(s) and the image viewer(s) view images with unicode? Like special characters and the like.

I ask because thousands of images with Japanese special characters in the filenames and the native image viewer I currently use on Windows doesn't support viewing images with unicode yet.

---

### Post by sudodus on 2012-07-07
1. I think often images have the text (if any) hardcoded into pixels, so it is not possible to change according to locale (language, unicode etc).

2. But it is different with the file names of the images. The image file names obey the same rules as other file names, and can be sensitive to locale. As long as there are no special characters (with a special meaning to the shell), it should work. I don't know about the Japanese special character, but I suggest that you try.

Download a [KLX]ubuntu iso file. Make a CD or USB boot drive and test it running a live session. If that looks good, you can consider installing to your hard drive.

---

### Post by diesch on 2012-07-07
Ubuntu uses UTF-8 as encoding for file names in most language environments. So as long as your file names are encoded in UTF-8 you should be fine.

If your file names use another encoding you can convert the file names on the command line using *convmv* - you just have to know the current encoding.

---

