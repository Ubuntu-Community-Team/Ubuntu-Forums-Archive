---
title: "Scripts won't excute except for CLI"
date: 2009-09-12
forum: General Help
---

### Post by shironeko on 2009-09-12
Fresh installed xubuntu 9.04

This is something I never faced before..
Let's see.. I can execute any custom script but only using the terminal.

Anything that is not a command (For instance a custom script.sh file) cannot be excuted using GUI. This affects Thunar when double clicking the file, ALT+F2 (xfrun4), Keyboard shortcuts, etc..

But when I just write ./script.sh in the terminal there is absolutely no problem. 

And yes, I have given everything the right permissions.
Oh, BTW, when trying to execute the script with ALT+F2 it does nothing, but when checking: "open in terminal", then a terminal opens and closes faster than you can say "kitkat"

So what's happening?

---

### Post by Liolikas on 2009-09-12
It may be that your script is very easy task it just runs do all job and closes. And You even think that it do not run at all.

So try to add run-confirmation command to your script like:
echo "Run confirmed" >> ~/Desktop/log.txt

---

### Post by StuartN on 2009-09-12
> **shironeko said:**
> a terminal opens and closes faster than you can say "kitkat"

Open a terminal and edit the default profile preferences - under Title and Command set the When command exits field to "Hold terminal open". At least then you will see any error message.

---

