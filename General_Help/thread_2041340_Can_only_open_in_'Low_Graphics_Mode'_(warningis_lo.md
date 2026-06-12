---
title: "Can only open in 'Low Graphics Mode' (warning:is long)"
date: 2012-08-12
forum: General Help
---

### Post by userqqq on 2012-08-12
Low graphics mode only on Thinkpad r52 with ati x300 graphics.

I was using some (dont remember) terminal commands I found on the internet
 to hook up my cellphone as a hotspot and when I restarted I just get a window 
that says 'running in low graphics mode'. I can log in (with no desktop, mouse 
and just a blinking cursor. But I dont know how to restore the graphics and pretty
 sure there is no internet connection.


I put the drive in a differrent laptop (old HP w intel graphics) and I can 
see my desktop now but the keyboard (even external) doesnt work so cant 
log into admin account but can log into guest account (tried to change user permissions, didnt work)
and use the virtual keyboard and open a terminal.There is no internet connection.

Ubuntu seems to usually change graphics drivers on the fly if you put the drive in 
another computer and it did that when I put it in the HP but I just want it to work 
again in my thinkpad with ATI x300 grapghics and it still only opens in 
'low graphics mode.
I *would* place a log here except I dont have a easy way to get the log file to a computer
that is connected to the internet but like I said I CAN open a terminal window in the guest 
account on the non net connected computer.
ANY suggestions or terminal commands?
Thanks in advance!

---

### Post by MoebusNet on 2012-08-12
After updates, I had a problem with low-graphics mode. The solution suggested to me was:

Try pressing Ctrl+Alt+F1 on your keyboard, then log in. From here, run these commands:

```
sudo rm -v /etc/X11/xorg.conf
sudo reboot
```

This will clear any existing configuration you may have, then reboot the system.

---

