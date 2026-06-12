---
title: "Segmentation Fault"
date: 2011-03-27
forum: General Help
---

### Post by throese on 2011-03-27
Well, when I ran the ```
skype
``` command I got a "Segmentation Fault" message. Well, I just did some research and I found some intriguing answers:

[http://www.cyberciti.biz/tips/segmentation-fault-on-linux-unix.html](http://www.cyberciti.biz/tips/segmentation-fault-on-linux-unix.html)

"e) Maintain suggested environment for all computer equipment (overheating can also generate this problem)."

My laptop has been overheating a lot so maybe this is what happened.

Possible explanation on how to fix the code-sided issues:

[http://www.cprogramming.com/debugging/segfaults.html](http://www.cprogramming.com/debugging/segfaults.html)

Seeing as my problem is more than likely the overheating part, I probably can't use Skype anymore, or at least until I buy a new laptop. =(

---

### Post by 3rdalbum on 2011-03-27
I wouldn't read too much into the "segmentation fault" message. Segmentation Fault just means "the program crashed". Sometimes this can be the symptom of bad RAM or overheating, but it's just as likely to be the symptom of a buggy program or a corrupted file.

---

### Post by throese on 2011-03-27
So, what can I do to get a better diagnostic of what the problem really is?

---

### Post by DeMus on 2011-03-27
To see if it is the RAM, boot the computer and in Grub choose memory test. Let it run for several hours, maybe overnight, to see if your RAM is okay or not.

---

### Post by throese on 2011-03-27
DeMus: How would I get to the Grub2 Options? I don't remember how.

---

### Post by fela on 2011-03-27
Press esc on startup (straight after the BIOS screen), should get you to a menu.

If not you can always use a memtest86 livecd.

---

### Post by throese on 2011-03-27
ty fela

---

### Post by Lateralis on 2011-03-27
I had some problems with Skype last year.  I have no idea if my problem is related to yours, but I solved mine simply by clearing out the .Skype directory located in ~/home.  Skype is a little buggy in Linux and sometimes gets itself in a bit of a tangle.  Clearing out that directory helped Skype untangle itself for me.

---

### Post by throese on 2011-03-27
Lateralis: I don't have the .Skype folder even though Skype is installed...why is that?

Update: I used a link provided by gordintoronto in my other topic ([http://ubuntuforums.org/showthread.php?t=1714664](http://ubuntuforums.org/showthread.php?t=1714664)) and now the Skype works again...but why does the static version work while the dynamic one does not.?

---

