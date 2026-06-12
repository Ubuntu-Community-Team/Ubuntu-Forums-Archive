---
title: "&quot;Error: BrokenCount &gt; 0&quot;"
date: 2012-07-04
forum: General Help
---

### Post by switchfoot123 on 2012-07-04
Okay, issue here! Hooray for problems!

I have a small red minus sign/icon in my notification area telling me
> An error occurred, please run package manager from the right-click menu or apt-get in the terminal to see what is wrong. The error message was: 'Error: BrokenCount > 0'. This usually means that your installed packages have unmet dependencies,

I have NO idea what that means. Total noob here.

In addition, when I head over to the software center, it tells me, "Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?"And when I click repair, it give me a message saying "package operation failed". I don't know what is going on, haha!

Any help on the problem would be appreciated :) thanks so much!

---

### Post by msammels on 2012-07-04
Hey switch,

Check out [this thread](http://ubuntuforums.org/showthread.php?t=1940523).

---

### Post by raja.genupula on 2012-07-04
open your terminal and type this

```
sudo apt-get install -f
```

gives the terminal code also here between code tags .

---

### Post by switchfoot123 on 2012-07-04
Hey! I'll try that now. I just tried a bit, it was downloading some stuff it looked like, but then my computer shut down. (Overheat or part of the process?)

---

### Post by msammels on 2012-07-04
The system should never automatically reboot... I would say overheat.

---

### Post by switchfoot123 on 2012-07-04
i can't put all the code here since I'm using a different computer and still correcting the internet issues on the other one, but here's the basic:

the following extra packages will be installed:
libreoffice-core
1 upgraded, 0 newly instaled, and 188 not upgraded
10 not fully installed or removed
need to get 0 B/37.2 MB of archives.
After this  operation, 15.4 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
libreoffice-core
Install these packages without verification? Y/N

which to choose?

---

### Post by raja.genupula on 2012-07-04
Gives yes (Y) , no problem and after this try again with what you are trying to do .

---

### Post by switchfoot123 on 2012-07-04
It had a whole bunch of stuff, looks like it installed that libreoffice, and my red dot is gone! Yay!

Is that all then?

---

### Post by msammels on 2012-07-04
Well, if you are experiencing no more problems, I guess :)

---

### Post by switchfoot123 on 2012-07-04
haha okay! :) thanks so much for the help!

---

### Post by raja.genupula on 2012-07-04
if you have solved your issue , you can mark the thread as solved from thread tools .

Thank you .:)

---

