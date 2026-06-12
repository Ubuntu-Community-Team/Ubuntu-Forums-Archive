---
title: "TIghtVNC stopped working.  Grey screen with X cursor...."
date: 2011-10-12
forum: General Help
---

### Post by ChipGibblets on 2011-10-12
Sorry if there is a better area for this thread.  

I have been using tightVNC to get a GUI for my dummy terminal server running Ubuntu Server 11.04.  It worked fine from the start.  However, now when I execute the 
vncserver -geometry 1280x1024 -depth 24 on the box and then open tightVNC on my windows vista laptop, I get a grey screen with an X for a cursor after logging in.  



The xstartup info seems to be entered fine on the server side.  



The one thing I will say I noticed is this:


WHen I opened tightVNC for the first time I got this screen: ([http://www.havetheknowhow.com/images/Configure_the_server/Install_VNC/VNCFirstTime_htkh.jpg](http://www.havetheknowhow.com/images/Configure_the_server/Install_VNC/VNCFirstTime_htkh.jpg))  and I was instructed to 'delete' that applet from my config via some instructions I was following and that worked perfectly. I was never given that  error screen again...UNTIL this most recent time...I think I hit 'don't  delete' and it hasn't worked ever since.  Ultimately, I thought "no big  whoop...just uninstall tightVNC and all it's component apps then  reinstall and get the same error message and THIS TIME hit 'delete' and  see if it works...but that hasn't done the trick.


Ultimately, I think this might not be a linux question but a tightVNC question.  How do I get that applet error screen to come up so I can delete that dang applet?  

Thanks!

---

### Post by Dexx4d on 2011-10-18
Your image link is an anti-hotlink image, but based on your description, I'm having the same problem.  For me, this started after my upgrade to 11.10.  From what I've been able to find out, this problem is usually caused by an invalid command at the end of the xstartup script.

Here's mine, with a few things I've tried to correct the error:

:~/.vnc$ cat xstartup
#!/bin/bash

# doesn't work - installed, but no go..
# gnome-session &
# gnome-shell &
unity &


So far, nothing works.

---

### Post by Dexx4d on 2011-10-19
I found my solution in this thread:
[http://ubuntuforums.org/showthread.php?t=1847810](http://ubuntuforums.org/showthread.php?t=1847810)

---

