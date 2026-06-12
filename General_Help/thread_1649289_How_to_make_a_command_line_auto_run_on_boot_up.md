---
title: "How to make a command line auto run on boot up?"
date: 2010-12-20
forum: General Help
---

### Post by NexusN on 2010-12-20
In dealing with the Nvidia Powermizer, I have to set it to "Prefer Maximum Power" mode from adaptive mode in order that I can avoid laggy in using my GUI.

However, it doesn't save this setting so I have to manually tweak it everytime........
Someone on the web taught me to use the following command line:

nvidia-settings -a [gpu:0]/GPUPowerMizerMode=1

running it in the terminal it will set to the mode I want.
Would I be able to make my computer run the above command in terminal everytime it starts?
I tried to put the command in the start up applications and it seems not working.
Will there be a solution?
Thank you for your kind attention.

---

### Post by wojox on 2010-12-20
Save it with sudo privileges:

```
gksudo nvidia-settings
```

Find the PowerMizer section set it and save.

---

### Post by NexusN on 2010-12-20
> **wojox said:**
> Save it with sudo privileges:

```
gksudo nvidia-settings
```

Find the PowerMizer section set it and save.

Thank you for your reply.
I set it in the root nvidia setting, saving it to xorg.conf, restarting,
looking into the xconf, it is still at the Adatpive mode.
It seems not working to me.

However, when I get into the Nvidia setting on terminal on root, 
it is set as prefer maximum performance............so strange.

I don't know if the Nvidia Setting is of bug, but is there a simple method for running such command on start up automatically?

---

### Post by wojox on 2010-12-20
Depending on what driver your using have a look [at this.]("http://linux.aldeby.org/nvidia-powermizer-powersaving.html")

You could always create a bash script and add it to Startup Applications as well.

---

### Post by NexusN on 2010-12-20
> **wojox said:**
> Depending on what driver your using have a look [at this.]("http://linux.aldeby.org/nvidia-powermizer-powersaving.html")

You could always create a bash script and add it to Startup Applications as well.
I tried something like 

 Option  "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerLevel=0x3; PowerMizerDefault=0x3; PowerMizerDefaultAC=0x3"


And it turned out to be not booting...........
Maybe using a simple command is the way, 
would you mind introducing the method?
what should I add in the command section in the Startup Application?
Simply putting the command I want it doesn't load.
Thank you.

---

### Post by NexusN on 2010-12-20
Don't know why but after some trying, it worked by adding the command to the startup application:

```
nvidia-settings -a [gpu:0]/GPUPowerMizerMode=1
```

Solved finally, thank all who has ever taken a look and given a helping hand.

---

