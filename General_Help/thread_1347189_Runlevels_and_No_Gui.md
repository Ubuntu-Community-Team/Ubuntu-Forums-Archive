---
title: "Runlevels and No Gui"
date: 2009-12-05
forum: General Help
---

### Post by mechsin on 2009-12-05
I am trying to upgrade the firmware in my Nvidia Graphics Card. It requires that there be no gui interface running when this happens. So I need to know how to stop X or Gnome or gdm what ever creates the gui from running at startup. I have tried several different things. In the end I would just like to change to Runlevel 3 and have the gui not start. 
Just as a note switching to tty1 and killing X doesn't work even from the login screen. I am fairly new to Ubuntu and am quit frustrated because I would think that something like this should be that hard to do. I am running Ubuntu 9.10.

---

### Post by scoon on 2009-12-05
> **mechsin said:**
> I am trying to upgrade the firmware in my Nvidia Graphics Card. It requires that there be no gui interface running when this happens. So I need to know how to stop X or Gnome or gdm what ever creates the gui from running at startup. I have tried several different things. In the end I would just like to change to Runlevel 3 and have the gui not start. 
Just as a note switching to tty1 and killing X doesn't work even from the login screen. I am fairly new to Ubuntu and am quit frustrated because I would think that something like this should be that hard to do. I am running Ubuntu 9.10.


Hey there, 

It is not.  What isn't working when you switch to tty1?  are you **sudo /etc/init.d/grub-common stop** ?  

thanks.

---

### Post by cariboo on 2009-12-05
You need to enter the command from a console. Press Ctrl-Alt-F1 to get to a console, they type:

```
sudo /etc/init.d/gdm stop
```

If you are running karmic and the above doesn't work try:

```
sudo service gdm stop
```

---

### Post by mechsin on 2009-12-06
Yes thank you 

sudo service gdm stop   Works

I boot as normal and at the login screen press Ctrl+Alt+F1 and run the command

Still is there a way to set it so that if I choose to boot to run level 3  at my grub screen that I don't need to run this command?

---

