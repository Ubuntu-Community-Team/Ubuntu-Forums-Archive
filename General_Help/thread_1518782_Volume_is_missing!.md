---
title: "Volume is missing!"
date: 2010-06-27
forum: General Help
---

### Post by Drop D on 2010-06-27
I have no volume control on my top panel.  I did not delete it, at least I do not think so, but now I cannot find a way to get it back.  Anyone know how to get it? Maybe a restart?

---

### Post by stderr on 2010-06-27
Probably your best bet (same thing happened to me a little while back). You could try closing all apps which are listed under System->Preferences->Volume Control->Applications and then restarting Pulseaudio:

```
pulseaudio -k
pulseaudio -D
```

but I don't know if that'll do it.

---

### Post by Drop D on 2010-06-27
That did not work.  Could I end the pulseaudio process?

---

### Post by stderr on 2010-06-27
If you ran the above commands you already did :): pulseaudio -k kills pulseaudio. The second command starts it again as a daemon process (i.e. starts it and detaches it from the terminal window).

I think I ended up rebooting if I recall. You could probably avoid rebooting per se and just restart the x server (i.e. logout and login again), but that doesn't really save that much hassle.

If you're *really* desperate to avoid a reboot, another possibility could be to find out what your soundcard's kernel module name is, kill pulseaudio, remove the kernel module with rmmod, insert it again with insmod, and restart pulseaudio, but tbh I really doubt that'll do it (and I'm not 100% sure your system will stay stable through the process, although I'm pretty sure it should).

---

### Post by Drop D on 2010-06-27
Well, it did not work.  I am thinking about reinstalling Ubuntu because of this.  Anyone else have any ideas?

---

### Post by robsoles on 2010-06-27
Hi Guys, quick check showed me that my volume control appears to be in 'indicator applet'.

Is your indicator applet still on your panel? Right click your panel and choose 'add to panel...', scroll through list and find 'indicator applet' and add it -

if you can see two sets of the same stuff, with no volume control still, then it was already there and you have a bigger problem.

If you didn't see anything get added then you also have a bigger problem.

If you get a volume control (and perhaps an envelope) then I am glad I haven't made some sort of invisible applet on your panel!!!

---

### Post by Drop D on 2010-06-27
Hot damn, its there. Thanks for all your help stderr and robsoles.  Much obliged and appreciated.

---

### Post by stderr on 2010-06-27
Haha, I just found the app whilst searching through ps aux output.

Just open up a terminal and run this:

```
gnome-volume-control-applet&
```

edit: Glad you got it working!

---

### Post by robsoles on 2010-06-27
Hey stderr, if the indicator-applet isn't on a panel then (AFAIK) you can have all the gnome-volume-control you can execute and still have no visible volume control on your display.

---

### Post by kevinlang21 on 2010-06-27
I found the envelope icon in the indicator applet to be really annoying, and that can be removed with:

sudo apt-get remove indicator-messages

---

