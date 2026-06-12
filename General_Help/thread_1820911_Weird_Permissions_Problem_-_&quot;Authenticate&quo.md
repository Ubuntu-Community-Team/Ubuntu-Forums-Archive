---
title: "Weird Permissions Problem - &quot;Authenticate&quot; Buttons not Working"
date: 2011-08-08
forum: General Help
---

### Post by SavageWolf on 2011-08-08
The following buttons do not seem to work:
In the network manager thing, checking "Available to all users" then save shows no prompt, and doesn't seem to do anything.
The "Install Desktop-Couch" button in Ubuntu One does nothing.
And operation in the users admin does nothing.
The Startup USB creater stops working with a generic error.
The unlock button in "Login Screen" does nothing.
The "Make Defualt" thing in Power Settings does nothing.

GKSudo seems to work fine, and this installation is about a day old. Anything I said "does nothing" does not print anything to a terminal.

usb-creator-kde gives a "org.freedesktop.DBus.Python.dbus.exceptions.DBusException: com.ubuntu.USBCreator.Error.NotAuthorized" error when trying to erase the disk.

EDIT: Fixed it, I was using the "Safe Mode" session from the login screen.

---

