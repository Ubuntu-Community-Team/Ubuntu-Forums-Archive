---
title: "error after successful install, but on first bootup on E1505&quot;failed to start Xserver&quot;"
date: 2006-04-20
forum: General Help
---

### Post by syxbit on 2006-04-20
i've installed Ubuntu 5.10 once, and Dapper flight six 3 times, but i don't know what's going on.
I can install them fine on my desktop.
upon successful install, it ejects the CD, and then reboots.
then i get the following error msg

"Failed to start the X server (your praphical interface). Is is likely that it is not set up correctly. Would you like to ciew the X Server output to diagnose the problem ?

and then

"the X server is no disabled. Restart GDM when it is configured correctly"

i'm pretty new to linux, so i don't know that much, and can't do anything without a GUI.

in Dapper, at least after this, i get the terminal.
in 5.10 it tries to load the terminal at this point, but says 
"BIOS not found"](*,) 

i'm fine with the 5.10 error, as really i hear dapper is stable, and want to run that.


btw, i have an ATI x1400 gfx card, and the laptop is brand new (core duo)

could you guys help please!

---

### Post by dermotti on 2006-04-20
When you get the xserver error, try running** sudo dpkg-reconfigure xserver-xorg** and select vesa as your driver, then restart

---

### Post by syxbit on 2006-04-20
[QUOTE=dermotti]When you get the xserver error, try running** sudo dpkg-reconfigure xserver-xorg** and select vesa as your driver, then restart[/QUOTE]

worked great. although now my screen rex. is 1024x768

i'm not good in the terminal, and stuff, so i don't know how to install ATI's drivers

i do know how to install easyubuntu (which i believe does the same thing)

am i right?

---

### Post by syxbit on 2006-04-20
that worked, but the problem i have is i'm using the new Dapper beta iso
it's a live boot only. before i would restart to then get into the GUI, but now i can't, as it will lose info (it's not installed) it i restart
any ideas?

---

### Post by Ensnared on 2006-04-20
[QUOTE=syxbit]i'm not good in the terminal, and stuff, so i don't know how to install ATI's drivers[/QUOTE]
I always follow [this guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide), and it's never failed me yet, not for Hoary, nor Breezy or Dapper.

I'm not sure how much good it is installing drivers if you're just running a LiveCD though - I've never really tried those other than to test Xgl/Compiz a while ago. I prefer an installed operating system instead :)

---

### Post by syxbit on 2006-04-20
the new Dapper beta is a live boot, and you run the full install from inside the live.
i just typed
startx 
in the terminal, and then installed from there

---

