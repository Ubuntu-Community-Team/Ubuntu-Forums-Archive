---
title: "Gnome Panel crashing"
date: 2005-01-25
forum: General Help
---

### Post by kris kincaid on 2005-01-25
I have installed Ubuntu on my wifes G3 Powerbook laptop, and I went all the way formatting the old drive and going totally Linux. The catch was it has to work. 

Well, now Gnome Panel is repeatedly crashing. When it crashes it gives me the option of closing it or restarting it. No matter which option I choose, it restarts it. However, when it restarts a window pops up saying that Gnome Panel is already running, but then that instance crashes. I uninstalled Gnome Panel with Synaptic, and it forced me to uninstall many packages with it. I reinstalled everything, and it still crashes. I have been able to get it running by typing "sudo gnome-panel" in a terminal. 

What I was doing when it happened:

My wife wanted URL links on the desktop to her most often visited websites. I was drag-n-dropping from the URL bar in Firefox to the desktop. Then it just started.

Please help, or I am in deep kimchie with my wife for screwing up her laptop!  #-o

---

### Post by ctt1wbw on 2005-01-26
Put your Ubuntu cd back in and open up a root terminal and type:

apt-get install GDM

Then see if that works.

---

### Post by kris kincaid on 2005-01-26
Ok, I tried that but it just shows that GDM is the latest version, so I used Synaptic to do it. It reinstalled, but that did not solve the problem.

The odd thing is I can type in a terminal window "sudo gnome-panel" and all is well  :-? 

If I can't figure it out soon, I may just reinstall Ubuntu. Not the option I like, but it'll certainly fix it! :roll:

---

### Post by ctt1wbw on 2005-01-26
I wish I knew more about Linux to tell you what to do, but I ran into a problem similiar to yours and my solution worked perfectly for me.  I know someone here has to be able to help you out.

---

### Post by kris kincaid on 2005-01-26
Thanks for the efforts. I am pretty Inexperienced with Linux myself. I usually fix things by brute force, rather than finesse. Case in point: I just reinstalled Ubuntu on the laptop. My wife needs to use it, and I spent 4 hours trying to fix it to no avail.


I can't wait until I'm able to figure out the easy ways to do things!!  ](*,)

---

### Post by oracledarren on 2005-01-27
I had this. open a terminal which should still work.

navigate and run synptic and reinstall gnome panel.

You dont lose anything and this corrects the problem  :wink:

---

### Post by kris kincaid on 2005-01-29
I tried reinstalling gnome-panel with synaptic through a terminal, it didn't work. I finally just gave up. Thanks for the reply though!

 So far this whole "Linux on a G3 Powerbook" is turning out to be a very bad idea for my marriage!   :mrgreen:

---

### Post by MarkHoward on 2005-01-31
The odd thing is I can type in a terminal window "sudo gnome-panel" and all is well  :-? 

You should never run any gui program as full root (sudo). This is probably what's caused the problems. Some files will now have the wrong permissions, causing the panel to crash. Try sudo chown -r username:groupname .gnome2 and possibly a few other files in your home dir. Some apps (notably mozilla in the past) also seem to change permissions on files in other (seemingly random) places in the filesystem, so it might be difficult to track down (we never managed to find out how to fix mozilla).

---

### Post by kris kincaid on 2005-02-01
> You should never run any gui program as full root

Thanks for that tip Mark! I had been doing that often, so I will stop. [IMG]http://ubuntuforums.org/images/smilies/icon_redface.gif[/IMG]

---

### Post by T31 on 2005-02-01
for me in a terminal window i just typed

sudo apt-get install gnome-panel 

and worked but some people as well do like this

sudo apt-get install --reinstall gnome-panel

good luck! :)

---

### Post by SilvioTO on 2005-04-15
Today the same problem on my desktop in Hoary... Solution is to delete the file "recently-used" from home directory and restart gnome.

---

### Post by dghamilton on 2005-05-12
[QUOTE=MarkHoward]The odd thing is I can type in a terminal window "sudo gnome-panel" and all is well  :-? 

You should never run any gui program as full root (sudo). This is probably what's caused the problems. Some files will now have the wrong permissions, causing the panel to crash. Try sudo chown -r username:groupname .gnome2 and possibly a few other files in your home dir. Some apps (notably mozilla in the past) also seem to change permissions on files in other (seemingly random) places in the filesystem, so it might be difficult to track down (we never managed to find out how to fix mozilla).[/QUOTE]


Usually those symptoms lead to a permission issue (works for root but not for you) but it's only working for root because he has a different set of icons/applets loaded on his panel.  I started encountering this immediately after messing around with different themes and THAT's seems to be what's causing the issue for me.  It was when I switched to the Human icon theme that this  started.

I'm sure removing your .gconf or .gconfd dir will fix it, but you will lose all the panel settings which kind of stinks.

---

### Post by dghamilton on 2005-05-12
[QUOTE=SilvioTO]Today the same problem on my desktop in Hoary... Solution is to delete the file "recently-used" from home directory and restart gnome.[/QUOTE]

I just tried that but that did not work.  I think that file is actually left there by gnome-panel itself ad is part of it's self restarting mechanism.

---

### Post by SilvioTO on 2005-05-13
Reboot your system with Ubuntu live (or other live distro like Damn Small Linux or Knoppix), mount the partition where ubuntu is installed and delete te file. Restart your system. ;-)

---

### Post by moon2js on 2005-05-13
I have had the same gnome-panel crashing issue in the past, and it happened during my attempts at using wifi. Whenever I boot up the computer with a wifi card in the pcmcia, I would have this issue. But whenever I booted up a wired LAN, gnome-panel was fine.

I worked around the problem by enabling hibernation and so what I always do is hibernate instead of turning off the computer. As long as I remember to bring down the wireless interface before hibernating (and as long as i bring it back up after waking from hibernation), I don't seem to have any gnome-panel issues.

I haven't tried just normal restarting (when I'm away from my wired LAN) for a while now because I haven't had the time to get to the bottom of this. Either that, or somehow working in ifup and ifdown into the hibernation script.

But reading this thread reminded me of the dangers of running things as root, and I remember that my wifi card uses the ralink2400, which doesn't support scanning with iwlist. So, back when I was trying to get my computer to be roamable. The driver included a utility to look for wireless networks and I installed it, but oddly it required not just to be run as root, but it required me to type sudo natilus in a console to bring up a root natilus and then run the utilty program with nautilis. I'm still a bit of a newbie with understanding linux but I was just following the directions . I'm wondering if this could have screwed up my gnome-panel, and if it did, why did the directions say to do that without any kind of warning?

Also, because it was so awkward to run the utility, I just didn't use it. It worked flawlessly the first time I ran it, but every time I tried it after that first time, it would completely hose my system. I don't ever use that utility anymore, but the gnome-panel acts up whenever I bootup without a wired LAN (so technically it started acting up after I installed the wifi driver/utility), so after reading this thread, I'm wondering if having to run that sudo nautilus that one time messed up my gnome-panel.

Anyone have any ideas? Once I get a chance to fiddle with things, I'd like to figure a non-hibernation solution.

---

### Post by Jazzinghen on 2006-01-30
Thanks for your help. I really didn't know what to do, but I've reinstalled the Gnome-Panel by passing to a terminal (With [CTRL]+[ALT]+[F2]) and then using sudo apt-get install --reinstall gnome-panel.
Then I've removed the file .recently-used and I've rebooted the machine (sudo reboot).
Now it works all fine. Thanks!

---

### Post by zigoto on 2006-04-21
Hi!
Iam  newbie in Linux/Ubuntu, and i have the same problem, and i trie to fix the problem with your posts, but i dont know how to do it. Please can some one tell me how to do it, step by step, because i dont understand how to do it.

Regards!


P.S. Sorry my english!

---

### Post by ginapi on 2006-05-04
I had the same problem. Try this:

CTRL+ALT+F1

login to the console as normal user

sudo killall gdm
rm .recently-used
sudo gdm &

---

