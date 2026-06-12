---
title: "Firefox crashing"
date: 2010-01-25
forum: General Help
---

### Post by kevindubrow on 2010-01-25
Hey, Firefox crashes every time I run it. I ran Firefox through the terminal and I got this:

stephen@stephen-laptop:~$ sudo firefox
[sudo] password for stephen: 

(firefox:7122): GLib-WARNING **: g_set_prgname() called multiple times
Segmentation fault

I tried reinstalling the program, but the same thing keeps happening. I think this started after I ran the last set of updates.

Could someone help me fix this? Thanks!

---

### Post by carlosgs91 on 2010-01-25
.

---

### Post by kevindubrow on 2010-01-25
Awesome! I had no clue that Chrome got put together for Ubuntu. Last time I tried, I had to run it through crossover or something...it didn't work too well.

Still, I would also like to have Firefox working. I did what you said but the program is still crashing the same way. Whats weird is that even after I purged all of the files, Firefox still had my internet history. I wonder if Firefox still didn't get completely removed.

In the mean time though, I'm installing Chrome.

---

### Post by carlosgs91 on 2010-01-25
.

---

### Post by ajgreeny on 2010-01-25
This is possibly a problem with the hidden folder ~/.mozilla in your home, so try renaming that.  Don't remove it as it contains all your bookmarks, and your history which is why that was still in place, plus cookies, etc etc.

Now try restarting Firefox and it may well run OK.  If so start copying the parts of the old profile that you need to the new one, bit by bit, restarting FF after each transfer.  There will probably be a point when the segmentation fault appears again, so remove that subfolder/file again.  It's trial and error I'm afraid, but with luck you may get FF back.

---

