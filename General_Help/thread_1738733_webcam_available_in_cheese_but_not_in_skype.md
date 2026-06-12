---
title: "webcam available in cheese but not in skype"
date: 2011-04-25
forum: General Help
---

### Post by DrScum on 2011-04-25
using ubuntu 10.04.02 trying to use webcam with skype 2.2.0.25 doesn't work i.e. the webcam is available under video devices but neither with the test button nor in a test call I get a picture.

The webcam works perfectly with cheese webcam booth.

Does anyone have any ideas on how to further diagnose or solve the problem?

---

### Post by TeoBigusGeekus on 2011-04-25
See [this]("http://ubuntuforums.org/showthread.php?t=1731392").

---

### Post by DrScum on 2011-04-25
thx Teo, I tried what was suggested in the link, but without success.

I checked in synaptic and found that xserver-xorg-video-v4l version 1:0.2.0-4 is installed on my system.

---

### Post by coldraven on 2011-04-25
In Skype do you just have a black rectangle?
If so, Skype may just be too dark to see an image.
Run guvcview (in the Software Centre) and adjust the brightness, then quit and run Skype.

---

### Post by DrScum on 2011-04-25
Yes, I do have a black rectangle and no brightness is not the problem, there just isn't any picture.
By the way, if the brightness settings are ok in Cheese, shouldn't they be ok for Skype too?

---

### Post by plucky on 2011-04-25
Try this from a terminal ```
env LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
``` note the env command at the start.

Good Luck

---

### Post by DrScum on 2011-04-25
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

is what I get when following the last suggestion.

---

### Post by plucky on 2011-04-25
> **DrScum said:**
> ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

is what I get when following the last suggestion.

Does the v4l1compat.so file exist?

```
ls -l /usr/lib32/libv4l/
```

---

### Post by DrScum on 2011-04-26
ls -l /usr/lib32/libv4l/ produces the following:

ls: cannot access /usr/lib32/libv4l/: No such file or directory

a search reveals though that libv4l is located under /usr/lib/lib4vl and it does contain the v4l1compat.so file.

---

### Post by plucky on 2011-04-26
> **DrScum said:**
> ls -l /usr/lib32/libv4l/ produces the following:

ls: cannot access /usr/lib32/libv4l/: No such file or directory

a search reveals though that libv4l is located under /usr/lib/lib4vl and it does contain the v4l1compat.so file.
Sorry I was on my 64-bit system and didn't notice the difference.

What happens if you change the command to ```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

Good Luck

---

### Post by Tanjerine on 2011-04-26
What worked for me (just now) wasn't the LD_PRELOAD stuff, but I had downloaded and installed v4l2ucp and I ran it while running skype. I was playing with the various settings, but what finally got the screen brighter was when I disabled the Power Line Frequency. I'm not sure why, though.

Hope this helps.

---

### Post by DrScum on 2011-04-26
to plucky: when I enter the command env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

skype opens and the camera works in test mode (i.e. I get a picture).
However, the terminal gets flooded with the following:

libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff

I could live with that but it looks like something is wrong. Doesn't it?

Thanks a lot for your help by the way

---

### Post by coldraven on 2011-04-26
> **DrScum said:**
> Yes, I do have a black rectangle and no brightness is not the problem, there just isn't any picture.
By the way, if the brightness settings are ok in Cheese, shouldn't they be ok for Skype too?
No, on my friends Asus Cheese was fine but upside down. The PRELOAD command solved that but Skype was just black. We thought it was broken until we shone a bright light at the webcam and saw an image.
guvcview seems to alter some system settings so that after using it the brightness stays up, no saving needed.
It's easier than doing trial and error command line adjustments.

---

### Post by DrScum on 2011-04-26
At this point, regarding the information exchanged above, the brightness settings are not the problem. But thanks for your input anyway. If I don't get a solution regarding the error messages I'll try your suggestion.

---

