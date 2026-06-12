---
title: "Can't stop kdm"
date: 2006-05-20
forum: General Help
---

### Post by Fedcer on 2006-05-20
Hi,

I'm having the following problem: when I try to stop kdm form the console-mode with "/etc/init.d/kdm stop", the Kubuntu logo and the loading bar appear but nothing happens, it stays like that forever.

Any idea of what it is? (KDE seems to be working fine).

Thanks for the help,

Fedcer

---

### Post by roachk71 on 2006-05-20
If you've updated from standard Ubuntu to Kubuntu, you could reconfigure from the console using dpkg-reconfigure:
```
sudo dpkg-reconfigure kdm
``` and selecting GDM from the menu that appears.

It would seem that you have either a broken KDM package, or incompatible hardware; some machines can be downright finicky. Let me know if this tip helps. :KS

Special note about terminating your desktop manager: When only GDM or KDM is running under your X server, it is the only active process running under X. Terminating the only remaining process will also stop X, forcing you to restart the machine, unless you know how to invoke either startx or X itself from the console. (Just an interesting note for those new to X.)

Another tip for Fedcer:

I don't believe KDM can be stopped safely the way you described. Another (more effective) way to kill KDM is
```
sudo killall -9 kdm
``` Be warned, however, the above note still applies...

In addition (if this is indeed what you're trying to accomplish,) you could completely disable your desktop manager. This is useful when you only want a console to appear (as a cold joke, or to deter would-be thieves; most only go for WinDoze machines, heh heh.)

To do this, you need the sysv-rc-conf package, which can be installed from Synaptic, Adept or apt-get. 
```
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
``` Scroll down to the gdm or kdm entry, and disable it for all runlevels (this can be reversed later.) Hit Q to quit. Then, you only need the startx command from the console after logging in.

---

### Post by Fedcer on 2006-05-20
Hi,

> 
If you've updated from standard Ubuntu to Kubuntu, you could reconfigure from the console using dpkg-reconfigure:


no I haven't, it is an original Kubuntu installation.

> 
It would seem that you have either a broken KDM package, or incompatible hardware

The strange thing is that kdm works fine otherwise. For example, if I do "sudo /etc/init.d/kdm restart" kdm restarts without problem.

---

### Post by roachk71 on 2006-05-20
Are you doing something memory-intensive from the console that you need to kill KDM to free RAM for, or are you getting a hang during shutdown, when it tries to stop the desktop manager?

Just need to know why you have to stop KDM...:-k

---

### Post by Fedcer on 2006-05-20
I just need to stop kdm because I want to install the nvdia drivers.

---

### Post by RagingOcelot on 2006-06-09
Having the exact same problem here...I also want to install the official Nvidia drivers.  Ready to do a killall dapper by this point.

---

### Post by lespedeza on 2006-06-10
Same problem on an upgrade from Breezy to Dapper.  When I try to Logout, Reboot or Shutdown, the Kubuntu logo with status bar appears and it hangs.  The only way out is to do a hard power off.  Any ideas?

---

### Post by tseliot on 2006-06-10
[QUOTE=Fedcer]I just need to stop kdm because I want to install the nvdia drivers.[/QUOTE]
You should read my guide then (have a look at Method 2):
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

---

### Post by lespedeza on 2006-06-12
[QUOTE=lespedeza]Same problem on an upgrade from Breezy to Dapper.  When I try to Logout, Reboot or Shutdown, the Kubuntu logo with status bar appears and it hangs.  The only way out is to do a hard power off.  Any ideas?[/QUOTE]

I solved my own problem by downloading the latest kernel, which I had neglected to do when I updated everything else.  Maybe that will help someone that is having the same problem due to the same cause.

---

