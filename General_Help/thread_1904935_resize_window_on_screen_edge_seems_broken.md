---
title: "resize window on screen edge seems broken"
date: 2012-01-05
forum: General Help
---

### Post by tibistibi on 2012-01-05
hi,

when i first installed ubuntu 11.10 on my new vaio laptop i could resize the window by dragging it to the screen edge. in the top for full size on the right for halve size. which was great.

now it is gone, i googled for it bout could not find a solution. 
i found options about installing stuff but i had it working so i should have everything installed.

any help?

thanks!

---

### Post by tibistibi on 2012-01-13
more googeling

here is a post:

´Bye bye inelegant hacks to achieve ‘Aero snap’ style window management in Ubuntu, and hello Unity + Compiz with it’s very own ‘edge snap’ plugin named ‘Grid’.´
[http://www.omgubuntu.co.uk/2011/01/aero-snap-in-ubuntu-unity-video/](http://www.omgubuntu.co.uk/2011/01/aero-snap-in-ubuntu-unity-video/)

it seems that the window management in ubuntu 11.10 is done by unity and compiz?

how can you check if this is still working?

---

### Post by tibistibi on 2012-01-13
i installed the compiz config settings manager there i can see that the grid is checked en should be working.

but i think the compiz plugin is not working at all. if i turn on wobbely windows it does not work either. 

is there a way to get compiz working again?

thanks

---

### Post by xc3RnbFO8P on 2012-01-13
I would try
> unity --reset
and restart the computer

---

### Post by tibistibi on 2012-01-15
thanks! i will try it...

a lot of flickering and these messages:

Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: glXCreateContext failed
Compiz (bailer) - Info: Ensuring a shell for your session
tibi@tibi-bhit-ubuntu:~$ 
(metacity:16861): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:16861): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:16861): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:16861): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


i will restart now

---

### Post by tibistibi on 2012-01-15
did a reboot but still nothing.

could it have to do something with my drivers?

i have installed ati/amd proprietary fglrx grophics driver

---

### Post by tibistibi on 2012-01-15
ok i unsinstalled the driver than run unity --reset rebooted and yes it worked.

i reinstalled the ati drivers and restarted and it was gone again. :(

is there a way to make unity work with ati drivers?

---

### Post by xc3RnbFO8P on 2012-01-15
What is the output of:
> lspci -vvv

---

