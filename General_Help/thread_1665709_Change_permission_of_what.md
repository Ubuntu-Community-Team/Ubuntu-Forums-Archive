---
title: "Change permission of what?"
date: 2011-01-12
forum: General Help
---

### Post by Keybored67 on 2011-01-12
Hello
I am fairly new to Linux, currently setting up a machine with Xubuntu to run GPS in my car.
I have the GPS up and running and receiving data from a bluetooth device.  The problem Ive run in to is that I want to write a script to connect the rfcomm and start my mapping program. Its wanting me to "sudo rfcomm connect 4" in terminal to make the bluetooth connection, but the Linux newb in me does not know what bit I need to change ownership of so that its not asking for a password.
Thanks for any help

---

### Post by Wobblybob on 2011-01-13
Hi mate, try this link [[COLOR="Blue"]http://serverfault.com/questions/75620/ubuntu-let-a-user-run-a-script-with-root-permissions[/COLOR]]("http://serverfault.com/questions/75620/ubuntu-let-a-user-run-a-script-with-root-permissions")

good luck

---

### Post by Keybored67 on 2011-01-16
Thanks.  The script is on hold because for some reason I need to start and stop and restart gpsd in a certain order with making the bt connection.  Still working out the least amount of steps, then I will work on a script to do it.  But that page directed my thinking to change permissions of /usr/bin/rfcomm so that I dont need to sudo anything now.

---

