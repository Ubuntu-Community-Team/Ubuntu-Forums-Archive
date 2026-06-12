---
title: "How to: Enable the Creative SoundBlaster Live! and Audigy sound cards device driver."
date: 2010-05-30
forum: General Help
---

### Post by ivox on 2010-05-30
[q]http://manpages.ubuntu.com/manpages/lucid/man4/snd_emu10kx.4freebsd.html

     To compile this driver into the kernel, place the following lines in your kernel configuration file:

           device sound
           device snd_emu10kx

     Alternatively, to load the driver as a module at boot time, place the
     following line in loader.conf(5):

           snd_emu10kx_load="YES"[/q]

Is there a better driver for Creative sound card support? 

If this is the best method: How do we edit the kernel configuration driver file? 

Alternatively if this is the best method: How do we edit the driver loader.conf & where is it located? 

Will submit to /r/linux if problem is solved.

---

### Post by ivox on 2010-05-30
Refering to: [http://www.linuxquestions.org/questions/ubuntu-63/how-do-i-load-the-sound-card-module-during-boot-478688/](http://www.linuxquestions.org/questions/ubuntu-63/how-do-i-load-the-sound-card-module-during-boot-478688/)

decided to take the advice and edit the modules config

so did ran a sudo gedit /etc/modules

Added line: snd_emu10kx_load="YES"
Per:[http://manpages.ubuntu.com/manpages/lucid/man4/snd_emu10kx.4freebsd.html](http://manpages.ubuntu.com/manpages/lucid/man4/snd_emu10kx.4freebsd.html)

"   Alternatively, to load the driver as a module at boot time, place the
     following line in loader.conf(5):
"
but ubuntu works on etc/modules not loader.conf

Can anyone else confirm?

---

