---
title: "Is this normal?"
date: 2011-09-14
forum: General Help
---

### Post by termin on 2011-09-14
I would just like to ask about the cpu usage of ubuntu. It normally uses less memory (130MB minimum. 300MB maximum) using gnome. (but my main environment is e17, which uses only 120-150 MB.) However, the cpu usage is insane, comsuming 50-80% of cpu. (regardless of desktop environment.) Is there a reason for this. I've used different distro's of linux for a long time now,(2 years) and it's like this for every single one that I've tried. There is a attachment of gnome-monitor showing the cpu usage in e17 (which uses the same amount for gnome). Is this amount normal?

---

### Post by Basher101 on 2011-09-14
You should check your processes. It looks like one is bugging and taking all the CPU. Run the System Monitor and click on the Tab Processes and then click on % CPU to display the processes that take up most of the CPU. Try to end them and see if that resolves your issue. Also please post what the process is that takes up the CPU

---

### Post by termin on 2011-09-14
Oh, sorry, heres the attachment.

---

### Post by Basher101 on 2011-09-14
Yes thats your system monitor. Now on the top of it you have those tabs there - click on Processes and on % CPU for it to display the process with the highest CPU load

---

### Post by termin on 2011-09-14
here's the result of the %cpu (see attachment.)
thanks again for the fast reply.

---

### Post by Basher101 on 2011-09-14
Now this seems odd. What version of Ubuntu do you use and what is your Graphics card? Also run this in a terminal in the background ```
top
``` it will display the processes with the highest cpu load (not all are listed in the system monitor)

---

### Post by termin on 2011-09-14
I'm using natty narwhal.
My specs:
gpu: nvidia geforce 4 mx 4000
cpu: pentium4 3.06 GHZ
mem: 3GB

---

### Post by Basher101 on 2011-09-14
Your hardware looks decent enough. Run the command in the background and just look what process takes the CPU load up

---

### Post by termin on 2011-09-14
top displays this:

---

### Post by Basher101 on 2011-09-14
If you use natty why do you have gnome 3 installed? Looks like its the gnome 3 session that takes up so much CPU. Try logging out with the fallback session or gnome classic (gtk 2.3x) and run the command again (or look in the system monitor)

---

### Post by termin on 2011-09-14
I've never attempted to install gnome 3 and as soon as I got natty installed, I just left everything at it's default settings and installed e17.
here's top in gnome 2:

---

### Post by Basher101 on 2011-09-14
Your session looked like gnome 3...but if you have no problems with the gnome 2 session you should keep using that one. Maybe its that e17 that is causing your CPU load? try uninstalling it, run top and see if it still uses up so much CPU on your "normal" session. If so, i advise you to stop using it and look for an alternative.

---

### Post by termin on 2011-09-14
That previous session was e17 in it's default theme. (or enlightenment)

As I said in my previous post, the cpu usage is the same in e17 and gnome. I don't mind it being used, It's just that the cpu changes instantly. Like for example, one second it could be 20% and the next it could be 80%. This is what worries me.

---

### Post by termin on 2011-09-14
I compiled e17 and all it's dependencies from source, because the one in the repos was old. uninstalling it would take a LONG time.

---

### Post by Basher101 on 2011-09-14
I experience this too, but not on such extremes, more on the level of the CPU load on 3% and it jumps to 20% but never more than that. Also it usually goes down again after those "jumps" to 5% or so. You should try a live CD with Kubuntu to see if you got CPU issues there. If you have a USB stick and your BIOS supports USB boot you can even save burning a CD

---

### Post by termin on 2011-09-14
I would just like to say thank you for helping me this far!


the reason I use e17 is because gnome 2 is so slow. Also, on some games, it flickers. All of these issues are resolved when using e17 or some other window manager.

---

### Post by termin on 2011-09-14
It won't matter, because I dual boot windows 7 on this same machine. I don't experience any of the problems there that i do in Linux. I will try kubuntu live cd and see if that helps. Thank you for your help.

---

### Post by Basher101 on 2011-09-14
Glad to help^^ i should be doing homework tho ._.

---

