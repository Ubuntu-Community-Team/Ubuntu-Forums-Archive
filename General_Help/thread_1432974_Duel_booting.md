---
title: "Duel booting?"
date: 2010-03-18
forum: General Help
---

### Post by Jonty789 on 2010-03-18
Hello.

I just wondering that is it possible to duelboot Ubuntu and Window xp SP3?

I can duel boot Ubuntu and Window XP but i not sure about Ubuntu Studio.


thank u

---

### Post by cariboo on 2010-03-18
You should get a better answer to your question here.

---

### Post by Jonty789 on 2010-03-18
Thank you

---

### Post by lake54 on 2010-03-18
If you mean "Can you dual boot Ubuntu Studio and Windows XP" then yes, it's the same method as a standard installation (although you won't have the fancy graphical installer).

If you already have a dual-boot setup, and want to 'switch' to Studio, just install the "ubuntustudio-desktop" package through either Synaptic or apt-get.

```
sudo apt-get install ubuntustudio-desktop
```

James

Apologies if any of that is incorrect - I'm returning to Ubuntu after a sort of hiatus!

---

### Post by audiomick on 2010-03-18
The principle is right, but there are a few more packages than just the desktop.

[ATTACH]150565[/ATTACH]
edit: the screen shot is the synaptic package manager

and then there is the Kernel. As far as I know, Ubuntu Studio  uses a Real Time kernel. I believe it is possible to install and activate this in a normal install, but have no idea how to do it.

---

### Post by Jonty789 on 2010-03-19
Ok how then pls?

---

### Post by audiomick on 2010-03-19
The packages are easy. Just open
system> administration> synaptic package manager
and type ubuntustudio in the search field the same as if visible in the screen shot. Click on the box to the left of the package and select "install", then click on the "apply" icon in the task bar.

As far as the kernel goes, that is really only relevant if you are doing overdubs in an audio recording, as far as I know. The real time kernel keeps the latency down, so you have a minimum lag in your monitoring. Even if you are doing overdubs, it might not be a big problem. I don't really know how to load and activate another kernel, so you will have to try it with the existing kernel and see if it is really an issue, or research the topic yourself or wait for someone else to give you advice. I am sorry I can't offer you more than that.

---

### Post by Jonty789 on 2010-03-20
Thank you very much for taking your time to help me.

Do you know how to make this thread SOLVED?

---

### Post by audiomick on 2010-03-20
> **Jonty789 said:**
> 
Do you know how to make this thread SOLVED?
That is an option under "Thread tools" at the top of the thread.

---

