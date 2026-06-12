---
title: "How to get arm-gcc?"
date: 2006-06-12
forum: General Help
---

### Post by mattG on 2006-06-12
Hello!

I need the arm-gcc cross compiler to compile some programs for the Sharp Zaurus 3200.
Is there a pre-compiled binary of the arm-gcc for Ubuntu or do I have to get the source code and compile it myself?

Thanks!


Matt

---

### Post by fer5437 on 2006-06-12
I think you can try install libpath-class-perl. I not too sure it work for you or not but you can get it from synaptic manager.

---

### Post by mattG on 2006-06-12
[QUOTE=fer5437]I think you can try install libpath-class-perl. I not too sure it work for you or not but you can get it from synaptic manager.[/QUOTE]

To be honest, I do not really understand how this libpath-class-perl relates to arm-gcc. Can you explain? Thanks!

---

### Post by IYY on 2006-06-12
I developed for an ARM-based system a few months ago, and my device came with a CD that included all the compilation tools. These same tools you can find in many places on the net, along with a readme file describing how to install them. For example:

[http://ftp.snapgear.org/pub/snapgear/tools/arm-linux/](http://ftp.snapgear.org/pub/snapgear/tools/arm-linux/)
(read this [http://ftp.snapgear.org/pub/snapgear/tools/arm-linux/build-arm-linux-3.3.2](http://ftp.snapgear.org/pub/snapgear/tools/arm-linux/build-arm-linux-3.3.2) )

Or just google for *linux arm tools*, it should be easy to find. And yes, you'll have to compile it, but it's very easy (just follow the instructions in the readme).

---

### Post by mattG on 2006-06-14
[QUOTE=IYY]I developed for an ARM-based system a few months ago, and my device came with a CD that included all the compilation tools. These same tools you can find in many places on the net, along with a readme file describing how to install them. For example:

[http://ftp.snapgear.org/pub/snapgear/tools/arm-linux/](http://ftp.snapgear.org/pub/snapgear/tools/arm-linux/)
(read this [http://ftp.snapgear.org/pub/snapgear/tools/arm-linux/build-arm-linux-3.3.2](http://ftp.snapgear.org/pub/snapgear/tools/arm-linux/build-arm-linux-3.3.2) )

Or just google for *linux arm tools*, it should be easy to find. And yes, you'll have to compile it, but it's very easy (just follow the instructions in the readme).[/QUOTE]

Thanks, I will do just that. I'm a little spoiled by this comfortable apt-get installing, so I was hoping there would be a similar solution for arm-gcc... :D

---

