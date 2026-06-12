---
title: "Tv tuner problem"
date: 2010-03-23
forum: General Help
---

### Post by Lam3r4e on 2010-03-23
Hello! 
I have a small problem when you switch from your previous version to 9.10 (karmic). My problem is connected with TV tuners, who previously drove by the following commands:
sudo rmmod saa7134 saa7134_alsa tuner
sudo modprobe saa7134 card=78 tuner=54
sudo modprobe tuner secam=l
Information on these commands, I found it by: [https://blueprints.launchpad.net/ubuntu/+spec/add-remove-hardware-wizard](https://blueprints.launchpad.net/ubuntu/+spec/add-remove-hardware-wizard)

 
Use a player who is TvTime. For now I have picture but no sound and I think that occur after the upgrade (as mentioned above). 
The error that I go when I enter the commands in the console is: 
**The first command, the output is:**

ERROR: Module saa7134 is in use by saa7134_alsa,saa7134_dvb
ERROR: Module saa7134_alsa is in use
ERROR: Module tuner is in use
**And the other two:**

WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.



Thank you for the help in advance and I apologize if I did not explain properly!

---

### Post by Lam3r4e on 2010-03-25
up!!!!

---

### Post by fragos on 2010-03-25
Ubuntu has been changing how they recognize devices and become much more automatic. I no longer need to do anything to use my Haupauge TV card except install tvtime. It all just works. Could your problem be that both you and Ubuntu are setting up your card?

---

### Post by Lam3r4e on 2010-03-26
> **fragos said:**
> Ubuntu has been changing how they recognize devices and become much more automatic. I no longer need to do anything to use my Haupauge TV card except install tvtime. It all just works. Could your problem be that both you and Ubuntu are setting up your card?
I changed / etc / modprobe.d / options to / etc / modprobe.d / options.conf as I stated in error, did the same with / etc / modprobe.d / blacklist it renamed / etc / modprobe.d / Blacklist.conf but again I have a picture, but I have no sound. I do not know what to do now?

---

### Post by Lam3r4e on 2010-03-28
up

---

### Post by asmoore82 on 2010-03-28
Typically, low cost tuners like mine will pipe the sound to one of the
"line_in" or "microphone" inputs on the main sound card.

Check your sounds mixers and make sure these channels are as a reasonable level and not muted.

---

### Post by fragos on 2010-03-28
Run alsamixer in a terminal. Right and Left arrow moves through the items controlled. "M" will mute or un-mute and Up Down arrows will change the input volume. As long as the are a number of ">" in the right border there are more items off screen.

---

