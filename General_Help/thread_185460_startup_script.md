---
title: "startup script"
date: 2006-05-31
forum: General Help
---

### Post by ShendZ on 2006-05-31
I know to run a script on startup I can do this
% update-rc.d FOO defaults 
where FOO is the name of the script, but I found it also runs when I reboot/shutdown.

In my case, I make a script to wake the wlan (because my wireless adapter is a lil bit weird, Dlink DWL-122).
It works great. I got internet connection now, but when I shutdown/reboot, the script is run also, so it is like renewing the DHCP ip thing and make the comp stops rebooting/shutting down.

How to add a script ONLY on startup?

Thank you.

---

### Post by chriscando on 2006-05-31
I think you can modify your script to take arguments like start, restart, stop.
I was just looking at the script /etc/init.d/ntpdate and they do this with a case statement. So when your system is starting I think the argument "start" is given to all your scripts (and "stop" when it is shutting down/rebooting). So in your case you would want the case "stop" to do nothing. I have never tried this but would be curious if it works.

---

