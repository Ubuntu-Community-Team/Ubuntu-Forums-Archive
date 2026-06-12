---
title: "Lost file after dragging onto desktop"
date: 2009-07-29
forum: General Help
---

### Post by scrambledarthur on 2009-07-29
Hmm.

I'm sorry if I'm posting too much, but I just made a bit of a blunder. Switching over from windows, I like to have a few basic folder available to me on my desktop, like the folder where I keep my most recent school notes.

I'm used to whenever I drag and drop, at least on to the desktop, having just the a link to the program be there, not the actual program. Well, I moved what I wanted to on the desktop, deleted, recovered it from the trash, dragged it onto the desktop again (don't ask why, it just happened) and then it straight-up disappeared! 

I tried to open up a file from the folder under "recent documents" but to no avail! I had an error message that read /home/arthur/documents/COLLEGE/DAT Business/Thermochemistry.odt does not exist".

I'd like to know if it's possible to recover the file, and how to prevent things like this happening in the future (is it possible to set it up that when I drag something onto the desktop, it simply places a launcher/link in lieu of the actual file?)

Thanks a bunch in advance! Without the help of this forum, I'd be lost!

---

### Post by credobyte on 2009-07-29
Open your terminal and execute this command:
```
cd $HOME/Desktop && ls -al

```

If your file can't be found ( you don't see it in output ), sorry .. it'll be quite hard to recover it ( I'll let others to post their suggestions .. haven't done any recovering yet ).

---

### Post by michy99 on 2009-07-29
Open a terminal and enter this command:```
sudo find / -name Thermochemistry.odt
```

---

### Post by scrambledarthur on 2009-07-29
Okay, it looks hopeful. It spit this out:

arthur@STEBBEDTOP:~$ cd $HOME/Desktop && ls -al
total 1548440
drwxr-xr-x  6 arthur arthur       4096 2009-07-29 16:42 .
drwxr-xr-x 50 arthur arthur       4096 2009-07-29 16:26 ..
-rw-------  1 arthur arthur          0 2009-07-29 16:12 7100.0.090421-1700_x86fre_client_en-us_retail_ultimate-grc1culfrer_en_dvd.iso
-rw-------  1 arthur arthur 1584025325 2009-07-29 16:45 7100.0.090421-1700_x86fre_client_en-us_retail_ultimate-grc1culfrer_en_dvd.iso.part
lrwxrwxrwx  1 arthur arthur         28 2009-07-29 16:19 Another link to COLLEGE -> /home/arthur/Desktop/COLLEGE
drwxr-xr-x  4 arthur arthur       4096 2009-07-08 18:33 COLLEGE
drwxr-xr-x  5 arthur arthur       4096 2009-07-21 16:08 Documents
lrwxrwxrwx  1 arthur arthur         28 2009-07-29 16:19 Link to COLLEGE -> /home/arthur/Desktop/COLLEGE
drwxr-xr-x  2 arthur arthur       4096 2009-07-29 16:42 untitled folder
drwxr-xr-x  2 arthur arthur       4096 2009-07-29 16:42 untitled folder 2
arthur@STEBBEDTOP:~/Desktop$ 
arthur@STEBBEDTOP:~/Desktop$

---

### Post by scrambledarthur on 2009-07-29
Phew, okay I found it.

Does anyone have any ideas how to organize my files in such a way that they're available but not prone to accidental deletion/modification en masse?

---

### Post by credobyte on 2009-07-29
Oh, glad to hear that .. About organizing your files - I always try to keep my sensitive files somewhere, where I can't accidentally hit DEL key ( eg. by hiding them ).

---

### Post by scrambledarthur on 2009-07-29
Why does ubuntu have a "hidden" kind of desktop? It looks like it's lost, but it just sends it to the desktop that I have to click on under places to open up. I guess it works...but it's kinda dumb imo.

---

### Post by credobyte on 2009-07-29
Ubuntu does not have a hidden desktop - it's a bug in Gnome/Nautilus ( have been experiencing it by myself ) :)

---

### Post by gypsumwolf on 2009-07-29
> **scrambledarthur said:**
> Phew, okay I found it.

Does anyone have any ideas how to organize my files in such a way that they're available but not prone to accidental deletion/modification en masse?

I always have one original folder (That all my important stuff goes in) and one back-up on an external drive. This makes it so easy to backup because everything is in one folder and if I accidentally delete it (or if it gets destroyed by some other way) I can retrieve it from the other source simply by dragging and dropping 1 folder.

---

