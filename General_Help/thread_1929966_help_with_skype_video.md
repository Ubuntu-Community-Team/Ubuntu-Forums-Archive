---
title: "help with skype video"
date: 2012-02-22
forum: General Help
---

### Post by Gatorade on 2012-02-22
I was just trying out skype for the first time , but I have a problem. 

When I turn the video on , its showing me upside down to the person I'm chatting with. Can anyone tell me how to fix this?

---

### Post by Gremlinzzz on 2012-02-22
You might find your answer here
[http://community.skype.com/t5/Windows/Video-Upside-Down/td-p/111100](http://community.skype.com/t5/Windows/Video-Upside-Down/td-p/111100)
:popcorn:

---

### Post by Gatorade on 2012-02-22
its saying Tools-Options-Video , but I don't have that tools button.

I went into the options settings while I was in skype but there was no option for me to fix it. the only thing I saw was a test button. which , when I tested it was still showing me upside down.

I'm using the camera built into my laptop , so I can't mess around with software for an external cam.

does anyone know how I can update the drivers for it, as I was reading that might be the problem.

---

### Post by Script Warlock on 2012-02-22
> **Gatorade said:**
> its saying Tools-Options-Video , but I don't have that tools button.

I went into the options settings while I was in skype but there was no option for me to fix it. the only thing I saw was a test button. which , when I tested it was still showing me upside down.

I'm using the camera built into my laptop , so I can't mess around with software for an external cam.

does anyone know how I can update the drivers for it, as I was reading that might be the problem. this is how i invert my video in skype using a4tech cam:
> export LIBV4LCONTROL_FLAGS=3
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.bin

---

### Post by Gatorade on 2012-02-22
is that going to work with my laptop cam , though?

---

### Post by Script Warlock on 2012-02-23
> **Gatorade said:**
> is that going to work with my laptop cam , though? try it first.

---

### Post by Script Warlock on 2012-02-23
i forgot to tell you this is working on ubuntu 10.04 on my shop.

---

### Post by Gatorade on 2012-02-26
ok, that didn't work.
I'm supposed to enter that into terminal, right?

---

### Post by Script Warlock on 2012-03-04
> **Gatorade said:**
> ok, that didn't work.
I'm supposed to enter that into terminal, right? yes but i think this is the new location of libv4l if you are working with the latest ubuntu release. /usr/lib/i386-linux-gnu/libv4l.

> LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so.0 /usr/bin/skype or v4l1compat.so.0

---

### Post by Ycanti on 2012-04-25
> **Gatorade said:**
> 
When I turn the video on , its showing me upside down to the person I'm chatting with. Can anyone tell me how to fix this?

A simple method i use is to stand upside down. Then i look like i am the right way up.

i hope this helps.

---

### Post by Gatorade on 2012-04-25
> **Ycanti said:**
> A simple method i use is to stand upside down. Then i look like i am the right way up.

i hope this helps.

oh, that's hilarious, did you think of that all by yourself?

---

### Post by elcalamar on 2012-04-30
I have been using the workaround for a while. When I tried to correct my Skype launcher to the new location, I would get an error message in the terminal "could not start 4vl1compat.so". I had to:
1)search for 4vl1compat.so (it was located in the i386 folder as another user already said)
2)Open a terminal and:
gksudo nautilus (I am on gnome-shell)
3)Copy lib4v1compat to usr/lib32 (I created the folder libv4l first and then copied in there the 4vl1compat.so)
And then it worked. Not sure why I had to do that, but my camera is back to normal. 
Audio, well that'a another story (and bug, and thread).

---

### Post by Chegirow on 2012-05-05
Hello,
I had a similar problem using Skype on Ubuntu 12.04 Precise 64 bits. The video would be displayed upside down.

First, I followed instructions we can find on Skype/Ubuntu forums and google :

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

```Skype starts but the video is still upside down. The output on the console was :

```
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```I checked that my libv4l libs are correctly installed but it appears that the file cannot be preloaded for some reasons.
For me, the problem was a wrong path in the above command.
 
To solve this problem, I followed the steps below :

1) Open Synaptic Manager (easy to install if you don't have it)
2) Type "libv4l" in the search field.
3) Locate "libv4l-0:i386", right click and select Properties.
4) Make sure you are on "Installed Files" tab (it should be the default tab).
5) Locate the line with "libv4l/v4l1compat.so" at the end.
6) Copy the complete path "/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so" (it might be something else for you).
7) Open a terminal and run : LD_PRELOAD=[paste the path you copied on step 6] skype.

The command should look like this : 

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```8) After skype login, go to Option and check if your video is displayed correclty.


I hope this can help.

---

