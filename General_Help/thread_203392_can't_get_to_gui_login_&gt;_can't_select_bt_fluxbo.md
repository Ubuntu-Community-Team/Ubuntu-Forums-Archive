---
title: "can't get to gui login &gt; can't select b/t fluxbox and xfce4"
date: 2006-06-25
forum: General Help
---

### Post by takayuki on 2006-06-25
Hi,

I did a server install and then installed xfce4 and fluxbox like this: sudo apt-get install wdm x-window-system-core xfce4 

then later installed fluxbox

Once i got everything set up, I got a Debian login screen that allowed me to select between xfce4 or fluxbox on login.

after some messing with my xorg.conf file in an attempt to get my keyboard recognized, i now just get the text based ("console"?) login which does not allow me to select between fluxbox and xfce4.  i want fluxbox to start but keep getting xfce4.

how can i get back to the gui login?

any thoughts greatly appreciated.

-takayuki

---

### Post by ayoli on 2006-06-25
if your wdm doesn't launch you can try from the text-based console to run:
```
sudo /etc/init.d/wdm start
```
then see if it runs or if you get any errors you can paste here.
I m not sure but I believe to remember that fluxbox has a startfluxbox command that you can run from a console also to launch fluxbox.
hope that helps.
regards.

---

### Post by takayuki on 2006-06-25
ayoli,

thanks for the reply.

[QUOTE=ayoli]
```
sudo /etc/init.d/wdm start
```

did the trick.  

i knew there was some command to get me there.  now i'm grooving in fluxbox.  xfce4 is a beefy dog on the old 400mhz, 64mb ram test box!

thanks for the help.  

takayuki

---

### Post by dirtvoyles on 2006-06-30
I am having the opposite issue. I did sudo apt-get install wdm and all was well.

THEN I rebooted. Now I'm staring at the WDM login screen, I cannot login to failsafe, ctrl-alt-F1 doesn't open terminal, and when I try to just login normally, X will start for a split second, then come back to the login.

Any help would be appreciated as I JUST got this old laptop running fluxbox, installed all my programs, and except for X everything was great. (I was having to use sudo startx)

Edit: I forgot Recovery Mode. (I'm new, be nice) I removed wdm, now time to reboot and cross my fingers.

Edit, Part Deux: IT WORKED!! Now I just have to get X setup properly, but that's in another thread.

---

