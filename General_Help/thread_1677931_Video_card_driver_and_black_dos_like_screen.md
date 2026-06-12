---
title: "Video card driver and black dos like screen"
date: 2011-01-29
forum: General Help
---

### Post by 5systems on 2011-01-29
Hey everyone, 

I am making a switch over to Ubuntu from windows on one of my kids machines.  It has a Nvidia video card, a g-force fx 440 i believe,  or something like that.  Anyway  I just loaded up Ubuntu 10.10 and and it seems it does not recognize my video card. If i go to system>administration>Additional drivers, the dialog comes back with "No proprietary drivers are used on this system.    Ok so now I go to Ubuntu Software center and search nvidia..... I get the option to installl Nvidia binary x.org driver (version 185), I do so.  

Now in the Additional drivers dialogue it tells me "this driver is active and currently in use".  Awsome, Now when I click on  Nvidia X Server settings under system>Administration I get the following dialogue.

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

If i do what that last message said, run sudo nvidia-xconfig in the terminal, It gives an error saying the xconfig file is not there,  and it will create one. The next time I reboot, Ubunut just shows a black dos like screen asking for username and password.  If i put it in, it does nothing, I end up having to re-install ubuntu.  

Sorry for the long post, but not sure what I am doing wrong.

Thanks,

---

### Post by sikander3786 on 2011-01-29
Maverick has dropped support for some older graphics card and the drivers are not available. You can try installing Ubuntu Lucid 10.04. It is another great release and is a Long Term Support release. It would be supported for 3 years on the Desktops.

Or if you intend to use 10.10, you will need to stay with the open source Noveau Drivers for Nvidia.

---

### Post by 5systems on 2011-01-29
So if I understand correctly,  I will have to load 10.04,  or buy a new video card for this machine to use the latest version of Ubuntu, Is this correct?

---

### Post by sikander3786 on 2011-01-29
> **5systems said:**
> So if I understand correctly,  I will have to load 10.04,  or buy a new video card for this machine to use the latest version of Ubuntu, Is this correct?
Sorry I just found some thing very interesting. We have been saying on the forums for months that 10.10 has dropped support for older cards whereas that is not the case. The old driver was broken in 10.10 and there is a workaround now. See here.

[http://ubuntulifeblog.blogspot.com/2010/12/update-on-nvidia-96-driver-with-ubuntu.html](http://ubuntulifeblog.blogspot.com/2010/12/update-on-nvidia-96-driver-with-ubuntu.html)

Please let us know about your progress as other users might benefit from it.

---

### Post by gufide on 2011-01-29
You can try to download the fine nvidia driver [here]("http://www.nvidia.com/Download/index.aspx?lang=en-us")
just enter your configuration, download it and follow these steps:

#1: put the driver file on your /home/"your username" folder
#2: press ctrl + alt + F1 [B][COLOR=Red]Be careful! Press ctlr + alt + F7 to go back!
[/COLOR][/B][COLOR=Red][COLOR=Black]#3: login
#4: type the command: sudo /etc/init.d/gdm stop
#5: type the command: ls (you will see your home folder and driver file name in white)[/COLOR][/COLOR]
#6: type the command: sudo sh "driver file.run" --uninstall
#7: type the command: sudo sh "driver file.run"
#8: install it
#9: type the command: startx

I think you will be ok with that

---

### Post by 5systems on 2011-01-29
when I type #4: type the command: sudo /etc/init.d/gdm stop

I get the following:
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the stop(8)utility, e.g. stop gdm gdm stop/waiting

What does that mean?

---

### Post by 5systems on 2011-01-30
I just went ahead and installed 10.4, it solved my issue with the graphics card.

---

