---
title: "Looping back to the log in screen."
date: 2006-04-06
forum: General Help
---

### Post by bdmp on 2006-04-06
I was installing Japanese input and the power went out and when I restarted my comp it wouldn't let me get past the log in screen.

When I sign in it sits on the blue kubuntu screen for a min and then it goes black and then to the grey x screen and then back to log in screen. 

When I log in with the console and I do startx I get the gray screen and then it goes back to the console. When I get back to the console it says a lot of stuff some of it being:
Skipping"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o": No symbols found 
and
Warning: font renderer for ".pcf" already registered at priority 0
and 
waiting for X server to shut down. 

Everything else is simialr to those errors. Could this be what is looping me back to the log in screen?

Please help.

---

### Post by Tosa on 2006-04-06
I had a similar problem a while ago, but it was my mistake. Anyway someone suggested that this should be run at console

sudo chown -R user /home/user

where user is your user name. I hope I remember this right. I've tried to find the thread with that, but I couldn't somehow. The command should restore your privileges that might have been screwed up...

---

### Post by bdmp on 2006-04-07
Thanks for your help, but that didn't work for me. Any other suggestions?

---

