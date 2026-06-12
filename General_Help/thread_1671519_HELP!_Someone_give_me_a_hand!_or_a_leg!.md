---
title: "HELP! Someone give me a hand! or a leg!"
date: 2011-01-20
forum: General Help
---

### Post by zuberbuhler on 2011-01-20
Aloha,

New to Ubuntu, made switch from windows about 5 days ago and I am lost!
I don't want to give up that quickly but i have a problem.

Since yesterday, my CPU level is really high (between 50 -100%), making the OS run really slow, the cooling fan is working over time which is irregular.
The only apps running are Firefox and skype so i don't understand why it is happening.

Noticed that Xorg (don't know what it is and didn't see it before) is the only app' running in addition to Firefox and skype.

system specs:

MSI Wind Notebook
Memory: 2GB
Intel Atom 1.60GHz
Disk space: 27.2 GB
Release 10.10 (macerick)
Kernel Linux 2.6.35-24-generic
GNOME 2.32.0


Everything was fine at the beginning and I didn't change anything so I don't understand...](*,) 
any ideas?

---

### Post by geirha on 2011-01-20
First off you need to figure out which processes are using so much CPU.

You can monitor that in the processes tab of System Monitor (under System -> Administration) or with the "top" command in a terminal.

---

### Post by Ziskille on 2011-01-20
I'm sortof having the same problem, except I know its Wine beta causing the problems, I added a "system monitor" launcher on the top panel and simply started running a few apps and copy/paste etc, just keep your eye on the system monitor link, as soon it spikes you will know which app is the culprit! Obviously this wont work if youre running 10 apps simultaniously, so patience is key lol.
 
Hope you get everything right and enjoy ubuntu!!

---

### Post by sanderd17 on 2011-01-20
you say firefox, do you have flash websites open? Adobe didn't optimize flash for Linux. All the rendering is done on the CPU instead of on the GPU. And therefore it causes big CPU levels.

Maybe install the flashblock add-on, that will replace all the flash elements with "play" buttons. If you want to see the flash, you just have to click play. If you're not intrested in the flash blocks (e.g. because it are ads) it won't use your CPU.

---

### Post by zuberbuhler on 2011-01-20
Thank you all for helping out!

I added to the top panel the system monitor and CPU Frequency Scaling Monitor and this is the data I got
while running_ Firefox (writing this reply) + Skype_ in the background :
CPU: 50% and up
Processor: 72%

Only 3 taking up CPU at all are Firefox,Xorg and Skype.
I noticed that I have many processes "sleeping", do they have any influence?

So flash doesn't seem to be the problem..

---

### Post by sanderd17 on 2011-01-20
sleeping processes just use a bit of RAM. That are things like the volume applet: waiting until you click on it or do an other action that triggers it.

BTW: CPU = central processor unit. I don't understand why you make a distinction between "processor" and "CPU". 

Can you see what app uses the most CPU? (you can sort the apps in the system monitor by cpu usage).

---

### Post by MiKOTRON on 2011-01-20
Aloha.  To see what the CPU hog is, open up a terminal 
"Applications>Accessories>Terminal" and type in 
```
top
```
You'll see the culprit at the top of the list.
Do that and let us know what it was so that we can let you know if it can be killed or not.

Here's a screenshot of mine running flash from youtube for example.

---

