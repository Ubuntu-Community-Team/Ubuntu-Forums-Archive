---
title: "Is there a Unity startup file?"
date: 2012-01-14
forum: General Help
---

### Post by Randy Schilling on 2012-01-14
I added the command, gnome-terminal, to open a terminal,
to my /home/randy/.profile.
This did not work as I expected.
After reboot, a terminal opened in my graphic login screen.
I expected the terminal to open in my Unity desktop.

Apparently .profile is executed before unity starts up.
Is there a Unity start up file where I can add commands, like
gnome-terminal, and have them run automatically after Unity starts up?

Is there a  setting that requests that Unity remember 
what programs are runnings at shutdown and open them at 
the next system start up.  This idea comes from the way 
the Hibernate command works

Thanks and Regards - Randy

---

### Post by Bobhuber on 2012-01-14
> **Randy Schilling said:**
> I added the command, gnome-terminal, to open a terminal,
to my /home/randy/.profile.
This did not work as I expected.
After reboot, a terminal opened in my graphic login screen.
I expected the terminal to open in my Unity desktop.

Apparently .profile is executed before unity starts up.
Is there a Unity start up file where I can add commands, like
gnome-terminal, and have them run automatically after Unity starts up?

Is there a  setting that requests that Unity remember 
what programs are runnings at shutdown and open them at 
the next system start up.  This idea comes from the way 
the Hibernate command works

Thanks and Regards - Randy
1. Startup - Yes - applications-startup commands

---

### Post by Randy Schilling on 2012-01-14
Thank you for looking into my problem but 
I don't understand what you're telling me.
Would you please provide some details or provide a reference?

---

### Post by Bobhuber on 2012-01-14
> **Randy Schilling said:**
> Thank you for looking into my problem but 
I don't understand what you're telling me.
Would you please provide some details or provide a reference?
  
You have a program called Startup Applications that can be accessed from the applications menu.
OR from a terminal run >

gnome-session-properties

It will give you a menu that will allow you to add any program you would like to start after the system boots.

---

### Post by Randy Schilling on 2012-01-14
ok thanks

---

