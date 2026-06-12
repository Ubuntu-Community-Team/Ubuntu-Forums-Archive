---
title: "New Linux user, questions about Wine and Bumblebee"
date: 2012-01-28
forum: General Help
---

### Post by Sophin87 on 2012-01-28
Hey all,

First time Linux user here. I recently bought a new laptop and decided to give Ubuntu a spin.

I have a question regarding activating my nVidia Optimus card using Bumblebee.
I've been unable to install it. Though I suspect the problem might be the firewall at my workspace. I've been unable to connect to the keyserver.
Does anyone know a work-around without changing the firewall settings?

Second question: I'd like to be able to play some videogames on the laptop. Bumblebee, however gives a warning that it does not work with virtual machines. Does this mean I won't be able to run my optimus card under Wine?
If that's the case, I'll have to install Win7 as well. Though I'd like to avoid that.

Thanks in advance for the help!

---

### Post by Mr Nemo on 2012-01-28
Hey Sophin welcome to the forums!

Regarding bumblebee, I believe that bumblebee has been superseded by ironhide. Try installing that by googling for the ironhide ppa. Ironhide is the new version of bumblebee and has the same maintainer. 

As to your second question, unfortunately Linux is not very good at running video games that require windows in any way. Sometimes you get lucky with wine, try checking the wineapp db to see if they have any chance of running in linux. As for virtual machines, I still don't think ironhide will work under them.

I hope was at least some help

---

### Post by Sophin87 on 2012-01-28
Thanks for the tips. I'll google Ironhide and check it out.

I'm a bit confused, is Wine a virtual machine? Or just a method of running windows applications in linux? I.E. will Ironhide/Bumblebee work with Wine?

---

### Post by CatKiller on 2012-01-28
Wine is not a virtual machine. It's a translation layer that translates Windows system calls into Linux ones. It is incomplete, so if the program that you're trying to run makes use of a Windows function that isn't implemented yet then your program will not work in Wine. The [AppDB]("http://appdb.winehq.org/") will give you specifics for particular applications.

Depending on what you're trying to run, the Intel side of Optimus may give you adequate performance. 3D performance will likely improve if you get the NVidia side working too.

---

