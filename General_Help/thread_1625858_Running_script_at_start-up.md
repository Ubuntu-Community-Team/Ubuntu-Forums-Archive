---
title: "Running script at start-up"
date: 2010-11-19
forum: General Help
---

### Post by JonathanCR on 2010-11-19
Hi everyone,

I'm still pretty new to Ubuntu.

My laptop has a problem with its touchpad - the left button doesn't work. Using my Windows partition, this is no big deal; I just use a mouse. Using my Ubuntu 10:04 partition, I also use a mouse, but if I so much as touch the touchpad, it's a disaster. The computer thinks I am holding down the left button, and nothing I do can stop this, even trying to click the mouse buttons. The only thing to do is reboot.

So I need to disable the touchpad. I have found that the following command will do this:

sudo modprobe -r psmouse

The problem is getting Ubuntu to do this automatically when I turn it on.

I have created a script. The script contains nothing but the command above. I have set the script to be executable. I know it works, because if I double-click on the script and choose the option "Run in terminal", it works: a terminal opens and asks me for my password, after which the touchpad is disabled.

I have also copied the script into my etc/init.d folder, following instructions I've seen elsewhere online. It is called Touchpad-disable.sh . I have gone to "Startup Applications" in my Preferences menu and created a new process there which I've called "Touchpad disable". This process has the command:

etc/init.d/Touchpad-disable.sh

But when I turn on the computer, the touchpad is not disabled. It seems the script is not being run after all. I have to go through the rigmarole of double-clicking the copy of my script that I've left on my desktop and typing my password (and if I forget, and brush against the touchpad, I have to reboot the computer).

Of course, an alternative solution would be just not to turn off the computer, and to let it suspend when I close it. Unfortunately this is not an option with my computer. Ubuntu cannot suspend, and when I close the lid, it just goes to a scary-looking error screen and stays on. There seems to be no solution to this. I have set it so that it simply shuts down when I close the lid. This is not such a big deal, given how incredibly quickly it closes down and boots up - booting from cold in Ubuntu is faster than waking from a suspend in Windows. But the touchpad thing is really annoying.

How can I set it so that it automatically turns off the touchpad when I boot up? What am I doing wrong? Any help would be much appreciated.

---

### Post by sisco311 on 2010-11-19
Hi and welcome to the forums!

You have to *blacklist* the psmouse module.

Create a file /etc/modprobe.d/blacklist-touchpad.conf:
```
gksu gedit /etc/modprobe.d/blacklist-touchpad.conf
```
with the following content:
```
blacklist psmouse
```

---

### Post by JonathanCR on 2010-11-19
That worked! Thank you very much.

What was the problem with the method I was using? Is it not possible to run scripts on start-up in this way, or does there need to be more to the script itself, or something?

---

### Post by sisco311 on 2010-11-19
> **JonathanCR said:**
> That worked! Thank you very much.


You're welcome!

> **JonathanCR said:**
> 
What was the problem with the method I was using?


Check out this HOWTO about Sys-V style init scripts:
[http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)

> **JonathanCR said:**
> 
Is it not possible to run scripts on start-up in this way, or does there need to be more to the script itself, or something?

Well, Ubuntu uses [Upstart]("http://upstart.ubuntu.com/"). Upstart is backward compatible with the old init daemon, it emulates the runlevels and starts the Sys-V style init scripts. So, yes it is possible, but the preferred method for starting an application at boot time is an [Upstart job]("http://upstart.ubuntu.com/getting-started.html").

---

### Post by JonathanCR on 2010-11-19
I see - that's where my nascent expertise reaches its limit, I think!

Thanks anyway for the pointers and for solving that problem. Now if there were a way to get the computer to suspend properly that would be perfect, but I can live with it as it is.

---

### Post by ajgreeny on 2010-11-19
Also you can not run scripts for commands needing sudo, ie root permissions from your Startup Applications list.

Any script like that can be run if it is put into **/etc/rc.local** just above the "exit 0" line, but without the sudo in front.

---

