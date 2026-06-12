---
title: "Qemu"
date: 2006-07-01
forum: General Help
---

### Post by Just4 on 2006-07-01
Does anyone know of a GUI for QEMU?

---

### Post by FredB on 2006-07-01
Qemu Launcher : [http://emeitner.f2o.org/qemu_launcher]("http://emeitner.f2o.org/qemu_launcher")

I didn't test it. I am **too** used to launch qemu from command line ;)

---

### Post by Just4 on 2006-07-01
I'll try it out, I am in the midst of getting Ubuntu to run everything I do in Windows (Minus gaming, though 2 of my most played games do have Linux ports, which I am definately going to look into in a few days) and I can use the commandline for QEMU for the most part, but sometimes I like working with a GUI.

---

### Post by porked on 2006-07-02
You could just create your own launcher and put it on the top bar. That's how i launch mine all the time saves on typing out the command line all the time. if you want i can post a sample of the very small but useful shell script.

---

### Post by Just4 on 2006-07-02
Sure, I'd appreciate it. (I still haven't gotten around to installing Qemu Manager yet so.) - Thanks.

---

### Post by porked on 2006-07-03
This is kind of silly but it works and i don't have to use terminal.

#!/bin/bash

cd Desktop

qemu XP.img -net user -soundhw all 

if you create a launcher from the add to panel option and just do ./nameofscript.sh in the command it should work....like i said, it's a very basic script but it works.:D

---

### Post by Just4 on 2006-07-03
ah, thanks, that gets the job done nicely (Turns out the GUI didn't work too well for me, so).

---

### Post by aysiu on 2006-07-03
If you really like GUIs, you can try VMPlayer, which is available in the repositories as of Dapper.

---

### Post by FredB on 2006-07-03
Yes, but you'll have to use already made OS images. You cannot make your own OS installs. So, no Windows if you need it...

---

### Post by mannheim on 2006-07-03
[QUOTE=FredB]Yes, but you'll have to use already made OS images. You cannot make your own OS installs. So, no Windows if you need it...[/QUOTE]

I don't think it works that way. It's like getting a real PC with some OS installed: there's nothing to stop you popping in a Windows install CD and installing Windows (on the virtual machine).

---

### Post by aysiu on 2006-07-03
[QUOTE=FredB]Yes, but you'll have to use already made OS images. You cannot make your own OS installs. So, no Windows if you need it...[/QUOTE]
I don't know where you're getting your information, but you can make your own OS installs. It gets tricky only if you're trying to use an already existing partition as a virtual drive.

---

