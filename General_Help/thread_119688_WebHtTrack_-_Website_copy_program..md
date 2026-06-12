---
title: "WebHtTrack - Website copy program."
date: 2006-01-20
forum: General Help
---

### Post by brakmaren on 2006-01-20
Hi
I installet httrack (terminal version) and it works like a dream. 
So i thought i try webhttrack (gui version). But i get this error message when starting.

```
/usr/bin/webhttrack(13389): launching /usr/bin/x-www-browser
/usr/bin/webhttrack(13389): spawning regular browser..

run-mozilla.sh: Cannot execute /opt/firefox/x-www-browser-bin.

/usr/bin/webhttrack(13389): waiting for browser to terminate..

```

I have Firefox 1.5 installed by automatix.
It seems to me that webhttrack don't find a webbrowser...

Any thoughts?
Thank's

---

### Post by z_diver on 2006-01-20
Not really sure why it would look for firefox in /opt.  Below is what I get if I run webhttrack from the command line.  I installed httrack using synaptic and also have firefox v. 1.07 installed although I've changed the /usr/bin/firefox symlink to point to version 1.5 in my ~/bin directory.

me@medina:~$ webhttrack &
[2] 29804
me@medina:~$ /usr/bin/webhttrack(29804): launching /usr/bin/x-www-browser
/usr/bin/webhttrack(29804): spawning regular browser..
/usr/bin/webhttrack(29804): waiting for browser to terminate..

What happens if you run:
ls -l /usr/bin/firefox

---

### Post by brakmaren on 2006-01-21
Hi z_diver.
You are typing a & after webhttrack. I did not do that.
What does the & do?
I'm not on that machine at the moment. I'll try it as soon as i get there.
I also installed through synaptic. But i do not have firefox 1.0.7 installed, just 1.5.
Thank's

---

