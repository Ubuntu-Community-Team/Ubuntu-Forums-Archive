---
title: "T43 XWindows problems."
date: 2006-04-30
forum: General Help
---

### Post by josys36 on 2006-04-30
Hello!

I just put on Breezy Badger and am having a problem with XWindows. When the system starts the splash screen comes up just fine, but when it comes time to display the login screen the screen goes blank and the monitor reports that there is no longer a connection with the system. 

What is really funny is that I just removed Mandriva to install Ubuntu and Mandriva had no problem with this.

I have tried dpkg-reconfigure xserver-xorg, but this does not detect my monitor. It could be a problem trying to use DVI with this NEC monitor, but I am not sure. Any help you can give would be great!

Thanks!

Jason

---

### Post by josys36 on 2006-05-01
Update,

I found out that when I unplug the laptop from the docking station it works just fine. The XWindows login screen and Gnome come up just fine. But when I have it plugged into the docking station, the screen will not come up on either the laptop or the external monitor.

Jason

---

### Post by josys36 on 2006-05-02
Well it looks like dapper drake may have solved the issue for me.

I installed dapper and now the external monitor works just fine. Whatever update they installed in Dapper seems to be doing the trick.

Thanks!

Jason

---

