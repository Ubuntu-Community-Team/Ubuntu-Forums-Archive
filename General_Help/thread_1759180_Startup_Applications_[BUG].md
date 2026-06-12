---
title: "Startup Applications [BUG]??"
date: 2011-05-15
forum: General Help
---

### Post by shashanksingh on 2011-05-15
I tried a few things in startup. Some did work, while others didn't.

eg: firefox works
google-chrome dsn't

(all commands tested from terminal, and all work when appended to .profile)

neither did compiz --replace (was trying that coz my startup compiz does not enable drag and drop, I dnt know why)

Is it that it can run only a type of application or is it some kind of bug?? I have read a few previous threads regarding startup having problems with chrome

---

### Post by Larkspur on 2011-05-15
It could be that Chrome is so fast that it's trying to start before there's an environment to start in, and you're asking to restart compiz before compiz has started.  Try putting this as the command:

```
bash -c "sleep 10; chrome"
```

(If "chrome" isn't the command to start chrome, put whatever is.  I don't have it.)

If that works, try the same with "compiz --replace."  Have you reported the drag-and-drop bug with launchpad?

---

### Post by shashanksingh on 2011-05-17
> **Larkspur said:**
> It could be that Chrome is so fast that it's trying to start before there's an environment to start in, and you're asking to restart compiz before compiz has started.  Try putting this as the command:

```
bash -c "sleep 10; chrome"
```

(If "chrome" isn't the command to start chrome, put whatever is.  I don't have it.)

If that works, try the same with "compiz --replace."  Have you reported the drag-and-drop bug with launchpad?

Thank you :)

in the command field: simply
'google-chrome' didn't work. But using bash in the command itself
'bash -c "sleep 10; chrome' did not work.

Strange, coz simply 'firefox' works.

Anyways, just for the reference, I did try the forums for the bug. Its [here]("http://ubuntuforums.org/showthread.php?t=1757053")

How do you report a bug to launchpad???

---

### Post by CrushingYourHead on 2011-05-17
I've had the google-chrome command disappear randomly from the startup applications list in several of the last few version of Ubuntu/Gnome. And similarly, the firefox command seemed to have no problem.

Just an hour ago, I had the thought to keep the same entry in the list, but simply change the command from "firefox" to "google-chrome". Knock on wood, so so far, its working like a charm. I've re-booted about 25 times trying to crash it, to no avail. No need to set a delay.

---

