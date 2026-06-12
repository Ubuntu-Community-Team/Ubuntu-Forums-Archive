---
title: "Problem is CPU usage."
date: 2009-08-10
forum: General Help
---

### Post by WetWired on 2009-08-10
I'm having a problem with CPU useage. I'm on Ibex, and for some reason, my CPU useage jumps to 100% when I'm not doing much. I was on irssi earlier in the terminal, and installing updates. If I tried to do ANYTHING else, like open a browser, text editor, anything, it'd jump to 100% and mostly lock everything up for a good minute before it'd give me a 10 second break and do it again.

And it doesn't seem to matter what I'm doing. I can't hardly multi task at all.

I'm hoping someone has a solution to this problem, because it just about makes the computer unusable.

---

### Post by twiztid-kid on 2009-08-10
What are your specs?

---

### Post by WetWired on 2009-08-10
P4 3.0ghz
4gb ddr2 pc4200
200gb wd ata
nvidia geforce 7600 gs
fresh install of ibex

If there's something else you need to know, let me know.

---

### Post by Lukian on 2009-08-10
What application are you using to monitor CPU Usage?

System Monitor graphs had a bug which caused up to 100% CPU usage when they were displayed.

---

### Post by WetWired on 2009-08-10
> **Lukian said:**
> What application are you using to monitor CPU Usage?

System Monitor graphs had a bug which caused up to 100% CPU usage when they were displayed.

I just use the system monitor that you add to the gnome panel. Are you saying the monitor itself could be causing the problem?

---

### Post by lonniehenry on 2009-08-10
Yes, it uses quite a bit of cpu usage.  A better solution to finding out what is using cpu cycles is top. Open a terminal and type top. It will give you a more accurate picture of what is going on.

---

### Post by WetWired on 2009-08-10
Well, I just removed the applet (if that's what it's called) and the problem is still there. This browser window is locking up. I'm not sure that's the problem.

---

### Post by ubudog on 2009-08-10
If all else fails, upgrade to 9.04.

---

### Post by WetWired on 2009-08-10
Ok, I sat around watching top  for a bit, and these are the ones causing high cpu useage

defoama-app
fc-cache
frontend
gconftool-2
update-app-inst

the last one was the worst. It hit 100, and stayed there for a good 15-20 seconds.

---

### Post by ubudog on 2009-08-10
> **WetWired said:**
> Ok, I sat around watching top  for a bit, and these are the ones causing high cpu useage

defoama-app
fc-cache
frontend
gconftool-2
update-app-inst

the last one was the worst. It hit 100, and stayed there for a good 15-20 seconds.

Ok.  It looks like somethings trying to update.  That process is probably your problem.

---

