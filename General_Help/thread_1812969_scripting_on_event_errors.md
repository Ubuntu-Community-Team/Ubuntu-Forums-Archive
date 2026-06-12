---
title: "scripting on event errors"
date: 2011-07-27
forum: General Help
---

### Post by Kissell on 2011-07-27
I used to trap error codes in DOS batch files many decades ago...  is there something similar in linux?

My system automatically runs a script when it needs to, that runs someone else's python script which queries an internet database to rename a file.  Then my script moves the file to its proper location.

The problem is that internet goes down occasionally at this unmanned remote site, cheap router needs rebooted or whatever...  and when the internet is down, the file doesn't get renamed, yet my script still moves it to the finished location...  :(

I need a way to check if the files was actually recently renamed before I attempt to move it...  or to act based on a successful error code from the other person's python script...  or a way to test if there is internet connectivity from my script...  any way to do any of that?

I don't know how to change the python script, the author is unresponsive and I installed with easy_install so I don't know how to see/edit the actual script.

---

