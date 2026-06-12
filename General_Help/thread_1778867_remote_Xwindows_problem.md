---
title: "remote Xwindows problem"
date: 2011-06-09
forum: General Help
---

### Post by meburke on 2011-06-09
I've use Xming and PuTTY occasionally to conect to my UNIX and Linux systems. since I've upgraded to 10.10 I cannot get an Xwindows session to work.

typically, I connect and set
 DISPLAY=192.168.1.100:0.0

then
export DISPLAY

It still works with Apple, Solaris10 and an old SCO OpenDesktop, but when I try to open an Xwindows app on my Ubuntu system I get:

No protocol specified
Cannot open display 192.168.1.100:0.0

I have the right IP address and w says I'm connected on pts/0 so I'm not sure where to look to fix this problem.

Any suggestions?

Thanks,

Mike

---

### Post by ruffEdgz on 2011-06-09
Why do you need the IP?
Have you tried 'localhost:0.0'?

I just did X11 forwarding from an Apple computer to a linux server (it isn't the same but still) and when I did:
```

echo $DISPLAY

```
I got 'localhost:10.0' so I don't think the IP is needed but that's just me.

;)

---

### Post by meburke on 2011-06-09
OK, I figured it out:

Under Connection ->SSH ->X11 you can put in the display location. If I put in the Display location without the parameters (0.0) and do not try to export the display after logging into my Ubuntu system, I can run an app (xclock &) and there is no problem.

I found this when I noticed a message in Xming that there was a second invocation of display 0. before failing.

I have tried this on a number of apps, and it works just fine. It is really cool to see Evolution come up on my Windows Desktop.

---

