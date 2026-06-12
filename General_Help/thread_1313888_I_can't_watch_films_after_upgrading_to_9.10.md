---
title: "I can't watch films after upgrading to 9.10"
date: 2009-11-04
forum: General Help
---

### Post by j_arquimbau on 2009-11-04
Hello,
Something related to XVID - MP4 codecs. Totem tries to find the codecs but is unable to. VLC says there is no way to fix it. I've installed libdvdcss2, libdvdread4, w32codecs and non-free-codecs. I could watch those films perfectly before the upgrade. They are .avi files.

Any help so far?

Thank you!

---

### Post by soapBAR2 on 2009-11-04
Are you sure you don't mean to install w64codecs?

At any rate, try (in a terminal)

mplayer /path/to/file.avi > ~/logfile

Then send us the output of /home/yourname/logfile. Mplayer is a bit more verbose, which is useful when there's a problem.

---

### Post by j_arquimbau on 2009-11-04
Once again I find the solution just after posting. The problem was the libavcodec52 package. I installed it and everythin solved. I found it in the "Lost recommendations" filter in synaptic. Thank you anyway

---

### Post by j_arquimbau on 2009-11-04
Thank you! I just solved it!

---

### Post by pootan on 2009-11-04
[U]Edit:Already solved so no need for this reply
[/U]

---

### Post by j_arquimbau on 2009-11-04
what is so irrelevant? I had a problem, tried to find a solution, didn't feel able to, posted a thread, then, by chance, found the solution, so then I posted it here so it can help anyone with the same problem.

---

### Post by pootan on 2009-11-04
Sorry I had a reply typed up but you already solved your problem so I edited it out. So my reply was irrelevant not your post.  :p

---

