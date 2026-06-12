---
title: "How start program(that lacks --display flag) on second monitor"
date: 2010-10-12
forum: General Help
---

### Post by Pithikos on 2010-10-12
I was thinking to do my music producing completely on linux and found a plethora of good tools for it. The thing is I have two monitors and instead of launching manually every little app each time I feel creative, I want to make a script that launches all my favorite apps.

So long I have written this little bash script:
```
#!/bin/bash
#Start my audio programs for music production
(qjackctl --start)&
(hydrogen --nosplash)&
sleep 1
ardour2
```So what it does is that it starts the jack server, then hydrogen and lastly ardour2. The thing is that I want hydrogen to start in the second monitor but don't know how. I have devilspie but I didn't have any luck on finding some command to choose display. 
I am aware of the --display flag that some programs have like firefox but hydrogen doesn't have it. Btw I use a _different X server_ on each screen.
So I was wondering.. is there a universal way to launch _ANY_ kind of program on a specific display?

---

### Post by searchfgold6789 on 2010-10-12
You might find [this thread]("http://ubuntuforums.org/showthread.php?t=271045") useful.

---

### Post by Pithikos on 2010-10-12
That didn't help much. From what I understood that link is on how setting up a dual monitor. My both monitors are already working without any problem. What I need is a way to specify on which monitor an application will start or at least make a launcher that will start a program on a specific monitor.
Unfortunately didn't find any info about that on the thread you gave me :|

---

### Post by vinkic on 2011-01-07
Hi, I have this problem with vlc media player and I find this post, hope it helps :) 
[http://pyverted.com/linux/vlc-on-a-separate-x-screen/2009/07/](http://pyverted.com/linux/vlc-on-a-separate-x-screen/2009/07/)

---

### Post by Pithikos on 2011-01-16
.

---

### Post by Pithikos on 2011-01-16
.

---

### Post by Pithikos on 2011-01-16
> **vinkic said:**
> Hi, I have this problem with vlc media player and I find this post, hope it helps :smile: 
[http://pyverted.com/linux/vlc-on-a-separate-x-screen/2009/07/](http://pyverted.com/linux/vlc-on-a-separate-x-screen/2009/07/)

Thanks buddy! That worked as a charm. [FONT=monospace]Here's how my bash looks in case someone gets in the same problem:
  
[/FONT]```

#!/bin/bash

#Start my audio programs for music production
DISPLAY=:0.0
(qjackctl --start)&
sleep 2

DISPLAY=:0.1
(hydrogen --nosplash)&

DISPLAY=:0.0
ardour2 zebra

#What to do when ardour2 is closed
killall qjackctl.bin
killall hydrogen

```

---

