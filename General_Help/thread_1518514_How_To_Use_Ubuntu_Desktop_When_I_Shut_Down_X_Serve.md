---
title: "How To Use Ubuntu Desktop When I Shut Down X Server"
date: 2010-06-26
forum: General Help
---

### Post by SecretLegend on 2010-06-26
Hey guys so right now I am running Ubuntu Desktop and using it as a server for my wordpress blog. So since I am not on it most of the time I shut down the GUI by using this command in the Terminal while in the GUI:

sudo /etc/init.d/gdm stop


Which brings me to a blank screen which is supposed to be the command line interface. But my question is, is how do you like enter commands such as "ifconfig" and stuff like "sudo blah blah" I hope you get what I mean. When I am at the command line interface I don't know how to enter anything. When I type something and press enter nothing happens, it just goes to a new line and doesn't do anything. Please help It's my first time doing this. Any answers are greatly appreciated :)

---

### Post by dabl on 2010-06-26
Which version of Ubuntu is this?  For 10.04 (and I think for 9.10), the command to shut down the X service is 

```
sudo service gdm stop
```

The command you wrote is the earlier one.

So, if you want a clean exit from the desktop to the command line, you should first Ctrl-Alt-F1, and log in there, and then issue the command to shut down X.

Then you have the Linux console and the bash shell at your disposal.  When you are ready to run the X server again, just ```
sudo service gdm start
``` and you'll have the greeter start up to log in to.

---

### Post by SecretLegend on 2010-06-26
> **dabl said:**
> Which version of Ubuntu is this?  For 10.04 (and I think for 9.10), the command to shut down the X service is 

```
sudo service gdm stop
```The command you wrote is the earlier one.

So, if you want a clean exit from the desktop to the command line, you should first Ctrl-Alt-F1, and log in there, and then issue the command to shut down X.

Then you have the Linux console and the bash shell at your disposal.  When you are ready to run the X server again, just ```
sudo service gdm start
``` and you'll have the greeter start up to log in to.

Hey man thanks I will try this :)

---

