---
title: "When I kill Gnome...my monitor does not return to a command prompt..."
date: 2011-07-25
forum: General Help
---

### Post by jmarcedwards on 2011-07-25
I'm trying to install the latest Nvidia device drivers.  I tried installing the driver from inside of Gnome, but was promptly messaged that I must not be in the X Server.  So when I tried to kill the X Server with "sudo /etc/init.d/gdm stop" the X Server does stop, but it seems that the video card stops sending all video to the monitor as the monitor enters "Sleep Mode".

I do not have a command prompt, nor a way to recover back to Gnome.

Any thoughts on why this is happening?

Thanks in advance.

Regards, Marc

---

### Post by Mr. Shannon on 2011-07-25
First, have you tried the drivers found in Additional Drivers on Ubuntu?  Installing drivers manually is not the easiest thing to do.

As for your problem, try pressing Ctrl+Alt+F1 and then kill gdm.  Ctrl+Alt+F1-F6 will give you a "real" terminal.

---

### Post by jwbrase on 2011-07-25
> **Mr. Shannon said:**
> First, have you tried the drivers found in Additional Drivers on Ubuntu?  Installing drivers manually is not the easiest thing to do.

As for your problem, try pressing Ctrl+Alt+F1 and then kill gdm.  Ctrl+Alt+F1-F6 will give you a "real" terminal.

You could even kill GDM first and then use Alt+F1 (you don't need Ctrl to switch tty's if the tty you're currently on isn't running X).

@jmarcedwards: Linux interacts with the user through a number of "virtual terminals" (also called "tty's", for historical reasons). You can switch between them with Alt-F<number of the virtual terminal you want to switch to>. The first six virtual terminals generally present a command line interface, the seventh is usually used for X, and the ones beyond the seventh are generally left blank. When you shut down the X server, tty7 doesn't have anything to display anymore and goes blank. You can then switch to one of the first six tty's to get a command line interface.

---

### Post by seawolf167 on 2011-07-26
Were you able to get this resolved by entering TTY1 by hitting [CTRL][ALT][F1] then stopping GDM with 

```
sudo service gdm stop
```

and then install your graphics drivers?

---

### Post by jmarcedwards on 2011-07-26
I haven't been able to resolve the problem as of yet.  I can kill the gdm service, but my monitor does not return to a terminal prompt.  I am now posting on the Nvidia drivers forum for some resolution.

---

### Post by seawolf167 on 2011-07-26
Hitting [CTRL][ALT][F1] should go straight to a terminal from a GUI with no extra commands entered, does it not?

---

### Post by tredegar on 2011-07-26
Since ubuntu 10.04 I have not usually been able to install the NVIDIA driver manually by using the "old" methods.

So do it "the ubuntu way": System -> Administration -> Hardware Drivers.

Then select & install the NVIDIA module.

This has the additional advantage that when the kernel is updated, the module is automatically rebuilt, so you don't get dumped to a terminal and have to do it yourself (*again*).

---

### Post by seawolf167 on 2011-07-26
I haven't had any problems... just enter TTY1, stop GDM, chmod the driver to flag it executable, run the driver, start GDM, done.

---

### Post by jmarcedwards on 2011-07-26
That is the behavior that I expected to see, but what happens is that the output from the ASUS graphics card stops driving video signals out of the DVI connector to the monitor.  I cannot seem to get that command prompt after killing the GUI.

---

### Post by jmarcedwards on 2011-07-26
What do you mean by entering TTY1?

---

### Post by seawolf167 on 2011-07-26
TTY1-6 are virtual terminals and are used for "terminal mode" access or diagnostics/repair if X fails.

The default shortcuts in Ubuntu are

[CTRL][ALT][F1] through [CTRL][ALT][F6] for the terminals, and [CTRL][ALT][F7] for the GUI. These just change the display type.

---

### Post by jmarcedwards on 2011-07-26
OK...this sounds like a preferred method.  But, when I am in the Additional Drivers, I don't know how the Additional Drivers application detects the various drivers.  How/where do I put the new Nvidia driver so that I can then "Activate" this new driver?

---

### Post by seawolf167 on 2011-07-26
You don't - these are separate drivers with separate installation methods. You can install the driver from the manufacturer to get the full proprietary driver suite, or you can install any available open source (or proprietary - read the info on the Additional Drivers items) drivers through the Additional Drivers program.

The Additional Drivers is much easier to use, and much easier to maintain which is why this is the supported method to install wireless, video, etc. drivers.

---

