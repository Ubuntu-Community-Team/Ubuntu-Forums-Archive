---
title: "why when i connect pc with other monitor it does not keep screen resolution?"
date: 2010-02-11
forum: General Help
---

### Post by gabak on 2010-02-11
i m a computer guy and i fix computer for people.
so when ppl bring me their computer and i install them ubuntu in my monitor when they take their computer to their home ubuntu does not keep the screen resolution i set for them.
why is that? how can it be fix?

---

### Post by mechro on 2010-02-11
Perhaps they're using Bakelite?

Seriously, not all monitors are created equal.

Possible solutions...

Leave the installation of any restricted graphics drivers to the client when they've hooked up their monitor.

or...

Delete or rename any xorg.conf file before handing over the computer.

or...

Set up a basic Vesa graphics driver.

---

### Post by scriptsit on 2010-02-11
This happens to me also, and I've yet to find a solution. 

I use my NVIDIA drivers to change my resolution, but whenever I click to 'save the x configuration file', it spits back at me: 

    Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

---

### Post by gabak on 2010-02-11
that is easy to solve just run the nvidia software being ROOT. then u wont have that issue or copy and paste.

> **scriptsit said:**
> This happens to me also, and I've yet to find a solution. 

I use my NVIDIA drivers to change my resolution, but whenever I click to 'save the x configuration file', it spits back at me: 

    Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

---

### Post by gabak on 2010-02-11
thank you . i ll try that. 
i tell you i have many computers at my office , then i have a pc connected to LCD 19" square. Then i took it to other pc where i have an old NEC 15" that support 1024x768 and when i turn on PC then ubuntu shows 640x480 resolution when in other 19" i have 1280x1024 or 1024x768 resolution and it did nt let me to change the resolution in the GUI mode.
It should nt happen , it should be like windows or it should auto adjust the resolution to the maximun then monitor supports ( i should add this to ubuntu forums ;-) )


> **mechro said:**
> Perhaps they're using Bakelite?

Seriously, not all monitors are created equal.

Possible solutions...

Leave the installation of any restricted graphics drivers to the client when they've hooked up their monitor.

or...

Delete or rename any xorg.conf file before handing over the computer.

or...

Set up a basic Vesa graphics driver.

---

