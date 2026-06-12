---
title: "Anyone know where Mplayer stores buffered videos?"
date: 2009-11-22
forum: General Help
---

### Post by djm227 on 2009-11-22
While watching DivX movies on windows, the player stores the temporary files to videos/divx/temporary.  It is a nice feature so that one can view them at a later time, or if you lose Internet connection.  Does anyone know where Mplayer stores the same files on Ubuntu?  

Thanks for the help

---

### Post by djm227 on 2009-11-23
can anyone help me with this?  I hate having to switch back to wndows to watch DivX stuff.

---

### Post by Vaphell on 2009-11-23
if i am not mistaken temporary files are kept in /tmp, at least they are there when you watch youtube clips and such.

---

### Post by lisati on 2009-11-23
> **Vaphell said:**
> if i am not mistaken temporary files are kept in /tmp, at least they are there when you watch youtube clips and such.

I'm not sure but would have thought /tmp as well.

---

### Post by t0p on 2009-11-23
I've had a cursory look at this subject before.  When you're watching a flash video (eg a YouTube video) the .flv file is saved to /tmp, usually with a name like /tmp/Flashabc1234.  But when watching a different file format, like DivX, you will see files created in /tmp that are not actually DivX.  It appears that the temporary files are not written in DivX, or in any format that can be saved and viewed later like the temporaty flash files.

But like I said, I've looked at this only cursorily. One thing's for sure: /tmp is the place to look for temporary files of all kinds.

---

### Post by kswenson on 2009-11-23
I've been looking for this too and haven't been able to find the answer.

---

### Post by djm227 on 2009-11-23
For those interested, I think I figured it out.

Mplayer stores the buffered files directly in /tmp, and no sub-folders.  The ones I have seen have a filename like "mplaycac2S6" or something similar.  When the video is done buffering, the file will be complete and you can watch it on your desktop.  It is in AVI format.

A good way to test if it is done buffering is to play the file with VLC.  If a "repair" message pops up, the video isn't done buffering.  But when no error message pops up, the file is complete and you can rename it and copy paste it at will.

---

