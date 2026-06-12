---
title: "kill the &quot;undead&quot; X server to install nVidia drivers"
date: 2011-12-28
forum: General Help
---

### Post by agnewton on 2011-12-28
Hello all,

I hope you can help me.  I am running Ubuntu 10.04 LTS, 64 bit and trying to install the nVidia drivers for a GeForce 550Ti GPU.  I've downloaded the shell script from the nVidia website and printed out the installation docs.

When I run the install script (sudo sh* NVIDIA-Linux-x86_64-290.10.run*) from the terminal, I get an error that the X server is still running.  I've tried a couple of different ways based on what I have read in other posts to kill it, but neither has worked.  These ineffective methods are:

1) to edit the rc-sysinit.conf & gdm.conf files per this thread [http://ubuntuforums.org/showthread.php?t=1480813](http://ubuntuforums.org/showthread.php?t=1480813).  (env DEFAULT_RUNLEVEL=3) The result is that the box just boots to the regular GUI desktop.

and

2) CTRL-ALT-F2 to a full-screen shell (I am not really sure exactly what the CTRL-ALT-F* combinations do) and then try to kill the X server with *sudo service gdm stop* but the output on my box is "stop: Unknown instance:"

What other options exist to kill the X server process?  Could there be a "second" X-server running?  

Your help is appreciated.

Thanks for reading.

Aric

---

### Post by stinkeye on 2011-12-28
Why don't you install from the [**_[COLOR="DarkRed"]xswat ppa[/COLOR]_**]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid")?

---

### Post by The Cog on 2011-12-28
The Ctrl-Alt-F1 through F6 give you six virtual consoles into the Linux OS. Each of these is a logical terminal where you can log in, as a different user on each if you like. Ctrl-Alt-F7 switches you back to the console that the GUI normally gets started on.

It is unlikely that there is a second X server process running.

Try using ```
sudo /etc/init.d/gdm stop
``` to stop the GUI, and ```
sudo /etc/init.d/gdm start
```to start it again afterwards.

Is there a reason you are not using the drivers distributed with Ubuntu?

---

### Post by agnewton on 2011-12-28
Thank you both for your replies stinkeye and The Cog.

I wasn't aware of xswat ppa.  The default video drivers were leaving a black border around the display and wouldn't allow me to use the full resolution of the monitor.  There was a second issue (possibly user-created) with an application that needed to use CUDA (optional) and OpenGL but couldn't find them.

The alternate commands to stop gdm also work.  I'll keep them in mind.

I was able to boot without the X-server running by issuing a combination of *sudo init 1 *in the terminal, rebooting, and holding down the ESC key.  I don't know if the ESC key was required or just superstition, but I did end up with a command line log in and no x server running.  From there, I changed to the directory where I had the nVidia shell script and ran it.  Everything worked out and the application now finds the CUDA accelerator and OpenGL.


Thank you for your help and sharing your knowledge.

---

