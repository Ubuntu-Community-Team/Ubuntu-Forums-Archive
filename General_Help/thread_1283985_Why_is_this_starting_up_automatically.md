---
title: "Why is this starting up automatically?"
date: 2009-10-06
forum: General Help
---

### Post by frankwakeman on 2009-10-06
I've been using Xubuntu 9.04 for a week or so. As of a few hours ago, each time I boot up, when restarting or from the machine being off, I get the settings manager there on the screen. There is no listing for it in Session & Startup.

The only thing I can think of is that it relates to some work I did on a theme while in root. But I don't exactly know how or what or what I do to reverse this.

Do I type anything sudo-prefixed in the terminal to kill this?

Thanks in advance.

---

### Post by Brandon Williams on 2009-10-06
It's probably listed in the session cache. You could try running 'rm -f ~/.cache/sessions/*' from a console when logged out from X entirely. Alternatively, you could open the 'Session and Startup' panel, select the 'Session' tab, and clock 'Save Session' to write the current session information to the cache. I find the other method more reliable, though.

---

### Post by frankwakeman on 2009-10-06
Yep, that did the job thank you.  

(I had seemed to have drawn a blank with the same post in the other category and would have deleted that if there was the facility to.)

---

