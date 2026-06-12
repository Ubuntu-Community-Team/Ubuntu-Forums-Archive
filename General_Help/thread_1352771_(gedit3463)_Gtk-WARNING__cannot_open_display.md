---
title: "(gedit:3463): Gtk-WARNING **: cannot open display:"
date: 2009-12-12
forum: General Help
---

### Post by g000we on 2009-12-12
Title = problem on my machine.

I went to [http://ubuntuforums.org/archive/index.php/t-166863.html](http://ubuntuforums.org/archive/index.php/t-166863.html) and rooted around there. I did the xauth adding part.
Didn't seem to work!

I then went to [http://www.linuxquestions.org/questions/slackware-14/gtk-warning-cannot-open-display-182090/](http://www.linuxquestions.org/questions/slackware-14/gtk-warning-cannot-open-display-182090/)

I tried to add users using the xhost command.

I first got..
```
xhost:  unable to open display ""
```..response from running xhost.

I tried.. (obv. root$ is the shell prompt for root)
```
root$host +
```Got..
```
access control disabled, clients can connect from any host
```..in response.


From [http://forums.oracle.com/forums/thread.jspa?messageID=2144787&tstart=0](http://forums.oracle.com/forums/thread.jspa?messageID=2144787&tstart=0) 
I used this (obv. $ is the shell prompt)
```
$DISPLAY=:0.0 ; export DISPLAY
```Seems to work. I've opened (using gedit :) ) .bashrc file of my user and added this commented out and will uncomment it out if this issue happens again, as a permanent fix.

Note: links are active as of date posted.

g000we

---

