---
title: "Login screen in ubuntu 9.10"
date: 2009-12-04
forum: General Help
---

### Post by jambel on 2009-12-04
My login screen for some reason turned the login/users window to a default look in a gray window. I was tried to change it using this [guide]("http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/") but with no luck (I also get those errors) ```
(gnome-control-center:2257): Unique-DBus-WARNING **: Unable to open a connection to the session bus: Failed to connect to socket /tmp/dbus-KacRKHzV8u: Connection refused

(gnome-control-center:2257): Unique-DBus-WARNING **: Unable to connect to the running instance, aborting.

``` Another thing is that I tried to edit gconf-editor and change the state of this 
/apps/gdm/simple-greeter/disable_user_list to true but when I reboot the user list still existed.
I think both problems are linked to same cause.

Any solution for my issues?

Thanks, 
- John

---

### Post by jambel on 2009-12-05
anyone?

---

