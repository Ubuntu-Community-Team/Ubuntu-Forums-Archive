---
title: "Screen capture"
date: 2011-02-19
forum: General Help
---

### Post by J V on 2011-02-19
I have a nice little system (Took over a year to find all the parts needed to build properly) which abolishes the useless desktop and replaces it with a nice grid of terminals. (With top automatically started)

Screenies are attached.

I would like to demonstrate this in action but recordmydesktop is pushing out corrupted files due to a bug in the lucid version.

If someone knows where to get a PPA for an updated (working) version of gtk-recordmydesktop and recordmydesktop could you please post? Thanks!

(The images below are before and after hitting ctrl+alt+D)

Edit: Debian squeeze is out... finally... I'll just switch to that (Which will probably actually WORK *gasp*) and post a vid here afterwards...

---

### Post by Habitual on 2011-02-20
not to burst your bubble, but I see a desktop, but anyway here's a trick to record the screen that may be of help...


from a terminal, run 
```
ffmpeg -f x11grab -s wxga -r 25 -i :0.0 -sameq ~/mymovie.mpg
```

Control+C to stop recording. Check your /home directory for movie.
It's =>1M per second of record time.

21 seconds was 20 megs but tar.gz'd to 15.7M
Converting format to save disk space sacrifices quality.

Hope that helps.

---

