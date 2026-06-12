---
title: "Command-line Only Boot"
date: 2010-03-04
forum: General Help
---

### Post by Flexico on 2010-03-04
Is there something I can add to my "menu.lst" file to give me the option to boot Ubuntu into command-line only without needing to edit system files every time I want to switch?

I have Ubuntu 8.10 Intrepid Ibex, in case that matters

---

### Post by byStanderone on 2010-03-04
...take a look at this thread: [http://ubuntuforums.org/archive/index.php/t-611759.html](http://ubuntuforums.org/archive/index.php/t-611759.html)

---

### Post by Flexico on 2010-03-04
Ok, so I used the "recovery mode" option and successfully got into command-line logged in as root. But then, the program I needed to run (named "NVIDIA.run", which is supposed to install my graphics driver but won't work as long as X is running) wouldn't run. I used "ls" and saw it right there in the home folder, but it said, "bash: NVIDIA.run is not a known command". It worked before when I (somehow) had gotten into command-line only with X not running, but I was logged in as my own username, not root.

---

### Post by gmargo on 2010-03-04
> **Flexico said:**
> "bash: NVIDIA.run is not a known command". It worked before when I (somehow) had gotten into command-line only with X not running, but I was logged in as my own username, not root.

Root's $PATH does not include the current directory, so you must type "./NVIDIA.run"

---

### Post by Flexico on 2010-03-04
OK, cool! I succeeded in running the program! But now, when I do, it says it needs to be in "runlevel 3" ... but when I switch to runlevel 3 ("sudo init 3") and try to run it, it says I can't have X server running! How do I do "runlevel 3" without running X?

---

### Post by gmargo on 2010-03-04
Is the .run file a shell script?  Can you see where it's looking for runlevel 3?  Ubuntu uses runlevel 2 for X.

---

### Post by Flexico on 2010-03-04
> **gmargo said:**
> Is the .run file a shell script?  Can you see where it's looking for runlevel 3?  Ubuntu uses runlevel 2 for X.

I don't know ... but I just chose to "run it anyway" and it worked. :) Thanks for all your help guys!

---

