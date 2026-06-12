---
title: "bring running proccess to &quot;foreground&quot;?"
date: 2010-02-05
forum: General Help
---

### Post by justleen on 2010-02-05
Hey all,

Bear with me, this needs some explaining.

My kids love tuxpaint. 
My kids can start tuxpaint themselves via a shortcut in the toppanel.
My kids have a hard time yet to notice the running instance of tuxpaint in the taskbar.

What happens: The kids misclick, and voila, they get a full screen browser. 
They miss the icon in the task panel (or fail to grasp the concept of running procs, to be more precise), and they simply launch a new instance of tuxpaint.

So far, so good, if it weren't for the fact that tuxpaint hoggs all my recources when launched for a 2nd, or 3th/4th/etc time. 
Nothing crashes, but my CPU runs @100% and memory usage sky rockets, so my system gets really slow.

What I did, is replace the shortcut with a script, that checks if its already running. If yes then kill the old one and start a new one.

This works, BUT it gets me dissapointed faces of my kids: "where did my painting go? :( " 


So, what I'd like to know, does anyone know how to "push" a program to the foreground in gnome? So that when there is already an instance running, it brings it to the front?


Any thoughts on this would be appreciated!

Leen

---

### Post by sheehan on 2010-02-05
have you tried wmctrl?
There is an example of it here,
[http://superuser.com/questions/16647/custom-hotkey-shortcut-to-open-bring-to-front-an-app](http://superuser.com/questions/16647/custom-hotkey-shortcut-to-open-bring-to-front-an-app)

Check out the answer by jtb, it sounds like what you 
are after.

---

### Post by justleen on 2010-02-05
Yes, that is exacly what I needed! A lot less hassle then with Devilspie...

Thanks a bunch!


For reference: ```

ps -ef |grep -v grep |grep -q tuxpaint && ( WID=$(xdotool search "tuxpaint" 2> /dev/null |head -1;  xdotool  windowactivate $WID) || /usr/bin/tuxpaint 
```

---

