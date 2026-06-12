---
title: "Starting FatRat on boot on headless machine?"
date: 2010-08-14
forum: General Help
---

### Post by al090187 on 2010-08-14
Hi,
I recently installed FatRat on my headless system. I am having trouble starting the program on boot though. When I launch it using the -n switch for no gui, it uses the terminal window as a log file, which means I cannot put it in the bootup programs because the constant logging stops the next program in the list from starting. 

Is there any way to launch fatrat without the gui, and letting it release the terminal for further commands after?

---

### Post by viralmeme on 2010-08-14
> **al090187 said:**
> Is there any way to launch fatrat without the gui, and letting it release the terminal for further commands after?
$FatRat &

---

### Post by al090187 on 2010-08-14
That solved that problem. Thanks.

Now, it starts up, but as the user is now root, not myself, the config file is not loaded, meaning I cannot access the program. When I launch it myself using a sudo command, it launches as root, with a different set of configuration files again. Is there any way of launching a process on boot, as a specific user, not just root?

---

### Post by viralmeme on 2010-08-14
> **al090187 said:**
> Now, it starts up, but as the user is now root, not myself, the config file is not loaded

[http://fatrat.dolezel.info/doc/contents/config.html](http://fatrat.dolezel.info/doc/contents/config.html)

---

### Post by Capt.Insano on 2010-09-01
I am trying to do something similar, but my idea was to start fatrat on boot in a screen session; meaning terminal is not a necessary. 

I can get a fatrat daemon to start with the command "screen fatrat -n" and sucessfully close the terminal without fatrat closing, but I have no idea how to get it to start on boot with that command. 

I presume it has someting to do with init.d start scripts but I don't know how to write one. Any Ideas?

Many Thanks,
The Capt.

---

### Post by josip_broz on 2012-02-19
Bump!!
Same issue. I would like to have fatrat started at boot time on my headless server.
Any ideas?

---

