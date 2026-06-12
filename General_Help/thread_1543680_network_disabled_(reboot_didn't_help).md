---
title: "network disabled (reboot didn't help)"
date: 2010-08-01
forum: General Help
---

### Post by luvgirl12345 on 2010-08-01
I started my computer today and there was no network... I didn't do anything yesterday that could cause such a problem and I even tried rebooting. When I click on the Networking icon in the Notification panel theres one greyed out line: "networking disabled"

Thanks for the help that I will hopefully get :p

---

### Post by NFblaze on 2010-08-01
Is it Wifi? Do you have a toggle button or switch on the computer> You may have accidentally toggled it off so you just have to hit that button.

If that fails I'd try:
```

sudo ifup eth0

```

If that doesnt work can you type in:

```
sudo lshw -C network
```

---

### Post by luvgirl12345 on 2010-08-01
I am using a pc without wifi (cable) there is no switch (that I know of). I will try those commands and report back

---

### Post by luvgirl12345 on 2010-08-01
[

deleted
[/CODE]

---

### Post by sydbat on 2010-08-01
Couple of dumb questions - how are you accessing this forum? With another computer?

How do you have Ubuntu set up on your computer? Is it in it's own partition or via WUBI? Personally, when I tried WUBI, all it did was mess things up in Ubuntu, but once I installed in it's own partition, all was good.

---

### Post by NFblaze on 2010-08-01
Hmm.. try 

```
sudo ifup --all --force
```

Are you running Ubuntu via Virtual Box, btw?

---

### Post by luvgirl12345 on 2010-08-01
Ok i fixed it ;) really dumb sorry. My niece or nephew seem to have disabled it... they are 3 and 5 years old and were listening to pandora on my computer... I told them how to switch to the next song if they didn't like it and left them alone with the computer. I saw my nephew play with the right mouse button but didn't think he would find the exact place to disable the network :popcorn:

SOLVED (it wasn't a bug and was my fault)

edit: a few answers: yes this is another computer (my sisters with windows) and the ubuntu installation is a native installation.

---

### Post by WanderingMinds on 2010-11-16
hello luvgirl12345,

Can u tell me how exactly did you nephew turned it off, and how did you turn it on again?
I am having similar problem, and don't know how to enable it.

Thanks for any help.

---

### Post by windowsh8r on 2010-11-16
If you right click the network icon in the panel, you can deselect Enable Networking.  I learned that one the hard way too.

---

### Post by anur.bhargav on 2011-01-15
> **windowsh8r said:**
> If you right click the network icon in the panel, you can deselect Enable Networking.  I learned that one the hard way too.

Thank you...:popcorn:

---

