---
title: "Application start on boot"
date: 2010-07-12
forum: General Help
---

### Post by killer1390 on 2010-07-12
Hi everybody.

How would one go about making an application start up on boot with terminal? I have a VPS that is ubuntu 8.04, and have command line access. I already compiled the application.

---

### Post by Exp HP on 2010-07-12
If you're talking about starting a program in a new terminal when you log in, go to System>Preferences>Sessions (or Startup Applications, depending on what version of Ubuntu) and try adding a new one.  The command would be something like **gnome-terminal --command *theProgramYouWantToRun***

If you're talking about on the basic Linux terminal (outside of X and GNOME), I think there's a config file where you can put commands to run on boot, but I'll need to look up where exactly that is.

---

