---
title: "Use Maximus Only on Specifically Selected Programs"
date: 2011-03-25
forum: General Help
---

### Post by steevven1 on 2011-03-25
I have read a million threads about adding exceptions to Maximus, and I know how to do that, but is there any possible way of telling Maximus not to touch any programs except the ones I specifically want it to? Actually, the ONLY program I want it to touch is Firefox.

Is there some secret syntax I could put in the exceptions to the effect of "all and not firefox" (as in, make all programs an exception, except Firefox)? lol. I hope that made sense.

Thank you so much!

---

### Post by steevven1 on 2011-03-25
Sorry for the early bump, but this is for someone else who I need to help out TODAY if possible. Thank you!

---

### Post by Krytarik on 2011-03-25
It seems like it's not possible to set Firefox as the sole app maximized by Maximus by default. But you can exclude *all*, meaning unfortunately also Firefox.

Therefore simply edit the key "/apps/maximus/exclude_class" in gconf-editor:
- click "Add"
- enter *nothing*
- click "OK"

Greetings.

---

### Post by steevven1 on 2011-03-25
I appreciate the response...Now here's a question: Is there some super secret way to tell your computer to automatically issue keystrokes when you launch a certain program? Or some command line thing I could write into a shell script that also launches Firefox?

Because there is a keystroke sequence in Maximus that turns it on for a certain window, I think. Just a thought. I'd really like to get this to work...

---

### Post by Krytarik on 2011-03-25
You can use "xdotool" for that, it's in the official repos.

But this is eventually a bit tricky, because

a) the actual run process:

1.) run Firefox
2.) delay the execution of xdotool until Firefox is open
3.) run xdotool

b) the application of those:

- either you replace any occurance of firefox with the new command
1.) launcher
2.) "Preferred Applications"
3.) url-handler
4.) probably more

- or you try to create a "script-in-the-middle"

I believe it's really easier to maximize it manually upon launch, if needed.

---

