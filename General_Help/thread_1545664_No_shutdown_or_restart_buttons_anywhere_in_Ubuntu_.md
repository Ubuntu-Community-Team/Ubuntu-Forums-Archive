---
title: "No shutdown or restart buttons anywhere in Ubuntu 10.04"
date: 2010-08-04
forum: General Help
---

### Post by acl123 on 2010-08-04
Where have all the shutdown and restart buttons gone?
They are not under the System menu.
They are not on the top task bar.
If you log out, they are not on the login screen.
In old versions of Ubuntu I could push the power button on my computer to bring up the shutdown/restart/logout options. This doesn't work.

As far as I can tell the only way for me to shutdown the computer is through the command line.

What the hell?

---

### Post by jesuisbenjamin on 2010-08-04
Hello there,

You can right-click on the panel and add to panel a custom application launcher.

In this launcher you can point to the command: gnome-session-save --shutdown-dialog

The shutdown icon of the ambiance theme is located in /usr/share/icons/ubuntu-mono-dark/actions/24
For any other theme change ubuntu-mono-dark by the theme of your choice.

Hope this helped!
B.

---

