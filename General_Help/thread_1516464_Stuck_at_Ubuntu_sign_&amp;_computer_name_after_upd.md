---
title: "Stuck at Ubuntu sign &amp; computer name after update."
date: 2010-06-23
forum: General Help
---

### Post by EndOne on 2010-06-23
Hi, I'm new to Ubuntu and Linux in general. I installed it and everything was fast and easy, best OS installation I've ever dealt with. It told me I needed to update so I let it download and install the updates, and then it said I needed to restart my computer so I restarted, and I get this [http://i525.photobucket.com/albums/cc335/aJzgfx/100623_175533.jpg](http://i525.photobucket.com/albums/cc335/aJzgfx/100623_175533.jpg) . I've let it sit for quite sometime without touching it and it hasn't changed. The panel at the bottom isn't even showing fully anymore. It is just a thin, white strip and I can't see any icons.

I installed it from a CD and over-wrote my Windows files because I was with a friend when he installed his Ubuntu and everything went great and he didn't have this problem. It's installed on a Laptop. Ubuntu 10.04 is the one I've installed. I installed it just an hour or two ago, actually. 

Thanks!

---

### Post by Woody1987 on 2010-06-23
Try pressing ctrl-alt-f1. This will get you to a terminal. Enter your login details when it prompts you. Once done, type: sudo service gdm start. If it says gdm is already running, enter sudo service gdm stop, then enter the first command again. This should start the graphics display automatically. If nothing displays, press ctrl-alt-f7.

This should get you to the desktop. Im not totally sure whats happened here, but at least this will allow you to progress.

---

### Post by EndOne on 2010-06-23
I did exactly as was stated and once I entered 'sudo service gdm start' it said it was already running so i typed 'sudo service gdm stop' it stopped and I entered the first line again and it brought me back to the same screen. Should I try to boot from the CD I installed from?

---

### Post by Woody1987 on 2010-06-23
Have you tried clicking on the name?

---

### Post by EndOne on 2010-06-23
That was the first thing I tried. Nothing seems to happen and the panel at the bottom isn't even fully showing so i can't click on anything down there.

---

### Post by EndOne on 2010-06-23
sorry for the double post, but I had forgotten to press ctrl-alt-f7, and now that I have it is saying that gdm-simple-greeter.desktop is not responding my mouse isn't allowing me to click anything, though.

---

