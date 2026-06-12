---
title: "Startup Script"
date: 2009-08-25
forum: General Help
---

### Post by marius_vt on 2009-08-25
Hi Guys,
 
This is my first script, and really need some help :)
 
Here is what I have done so far.
 
!
tunctl
ifconfig tap0 192.168.255.1 netmask 255.255.255.0 up
sleep 10
/home/marius/./start.lab.sh
/home/marius/Dynamips/IE/./start_lab.sh
!
It works great when I run it from a terminal, but.......
 
I need a terminal to open upon startup and then run the above commands.
 
When "/home/marius/Dynamips/IE/./start_lab.sh" run it actually launches the app.
 
Now, can one send commands to the app in the terminal?
 
I ask allot, it would be awesome if someone can help
 
Regards,

---

