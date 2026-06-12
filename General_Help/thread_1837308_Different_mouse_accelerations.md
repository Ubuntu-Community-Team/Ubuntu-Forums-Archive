---
title: "Different mouse accelerations"
date: 2011-09-01
forum: General Help
---

### Post by pederbruusgaard on 2011-09-01
Hey,
I'm still pretty new to Ubuntu and Linux in general, so I'm sorry if this is a really stupid question.
I have a Lenovo X220 and when I'm at home I use it with a wireless mouse and keyboard. This works very well, but there's one little issue:
The external mouse is super fast, so to make it usable I have to adjust the acceleration to the absolute minimum, but then when I take it with me to work somewhere else, the trackpad is slow as a tortoise.
I was wondering if there's a way to switch between sort of "mouse profiles", just like one can switch between keyboard set-ups (like I use American and Norwegian keyboard layouts, that I can select from the top bar).
Maybe it's possible to make a command or something, and then a keyboard shortcut to that command, to switch between them?

Again, sorry for all the noob-ish questions, and thanks for all help! :)

---

### Post by gekken on 2011-09-01
Try this: [http://www.linuxlog.org/?p=107](http://www.linuxlog.org/?p=107) 

It doesn't seem too complicated....

---

### Post by pederbruusgaard on 2011-09-01
> **gekken said:**
> Try this: [http://www.linuxlog.org/?p=107](http://www.linuxlog.org/?p=107) 

It doesn't seem too complicated....

Thanks! That looks just right! :)

---

### Post by pederbruusgaard on 2011-09-02
> **gekken said:**
> Try this: [http://www.linuxlog.org/?p=107](http://www.linuxlog.org/?p=107) 

It doesn't seem too complicated....

Ok, so it seems just about perfect, but I didn't quite get it working.
What I'm having trouble with is the last step with the file to be created. This is what I've written:

```
peder@peder-ThinkPad-X220:~$ nano ~/.mousespeed
xinput set-prop 'Microsoft Microsoft® Nano Transceiver v1.0' 'Device Accel Profile' -1
xinput set-prop 'Microsoft Microsoft® Nano Transceiver v1.0' 'Device Accel Constant Deceleration' 1.00000
```

Is that correct? Because I saved the file as "mousespeed", and when I try to run the command in terminal this is the result:

```
peder@peder-ThinkPad-X220:~$ sh ~/.mousespeed
sh: Can't open /home/peder/.mousespeed

```

Thanks for all the help with this!

---

### Post by pederbruusgaard on 2011-09-03
So I still can't get that command right, but I installed gpointing, which allows me to set parameters for the trackpad specifically, so it sort of solves my problem.
Thanks for the help :)

---

