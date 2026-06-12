---
title: "running a simple command/startup script before user logins"
date: 2012-02-04
forum: General Help
---

### Post by GraeW on 2012-02-04
I've been trying to get this to work, but it still isn't clicking the way I want. I need to disable my touchpad completely, during the boot process, prior to the login screen (lightdm) popping on. I know using "synclient" works, as I do have it as a 'startup program' during login to my XFCE session, but I still run into hanging issues with the mouse if I've used the touchpad at all prior to entering my password and logging in.

I've tried to put the command in the /etc/rc.local and also /etc/init.d/rc.local - I've even made my own simple bash script that does nothing but call up the command. I reboot, and the touchpad is still active.

I know I could go into everyone's individual login and disable it as a startup program, but then the touchpad remains active during login screen (selecting user, entering password, changing desktop environment), and thus will cause problems with any user after login.

Where do I put what to make sure this thing gets shut off? Thanks..

---

### Post by sefs on 2012-02-04
> **GraeW said:**
> I've been trying to get this to work, but it still isn't clicking the way I want. I need to disable my touchpad completely, during the boot process, prior to the login screen (lightdm) popping on. I know using "synclient" works, as I do have it as a 'startup program' during login to my XFCE session, but I still run into hanging issues with the mouse if I've used the touchpad at all prior to entering my password and logging in.

I've tried to put the command in the /etc/rc.local and also /etc/init.d/rc.local - I've even made my own simple bash script that does nothing but call up the command. I reboot, and the touchpad is still active.

I know I could go into everyone's individual login and disable it as a startup program, but then the touchpad remains active during login screen (selecting user, entering password, changing desktop environment), and thus will cause problems with any user after login.

Where do I put what to make sure this thing gets shut off? Thanks..

I have a question.  Is there a specific driver/module that drives the touchpad?  If there is maybe it would be possible to blacklist that driver/module in /etc/modprobe.d/blacklist.conf and stop the touchpad functioning altogether on bootup, and then run a script that loads the module/driver after the desktop appears if you need to re-enable the touchpad.

---

### Post by GraeW on 2012-02-05
I'm guessing it's a synaptic touchpad, as that is what synclient is geared towards. I'm not worried about re-enabling the touchpad - the laptop is about 5 years old and it's too finicky to trust. I just want to disable it completely during boot.

---

### Post by GraeW on 2012-02-06
so, re-reading your question, you are saying I should put the synclient, or syndaemon (whatever it is that runs the touchpad) into a blacklist file?

---

### Post by GraeW on 2012-02-07
gratuitous bumpage.. where can I script in synclient to disable my touchpad before X and/or lightdm takes over the screen? I've tried to look through the info in /etc/init.d

---

### Post by pqwoerituytrueiwoq on 2012-02-07
if you have a command you can use [FONT=Courier New]/etc/rc.local[/FONT]

edit:
you tried that 
does the trackpad use a different driver from a usb mouse?
if so you could blacklist the driver
[FONT=Courier New]/etc/modprobe.d/blacklist.conf[/FONT]

edit: this may be useful
[http://www.howtoforge.com/how-to-auto-disable-the-touchpad-when-the-mouse-is-plugged-in-fedora-13](http://www.howtoforge.com/how-to-auto-disable-the-touchpad-when-the-mouse-is-plugged-in-fedora-13)

---

### Post by GraeW on 2012-02-07
I'm not sure if it uses a different driver.. I have to poke deeper to find that. I will check your link out when I get home and can get back on the laptop again.. thanks!

---

