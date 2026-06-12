---
title: "ssh - Open aplication on remote computer"
date: 2011-02-28
forum: General Help
---

### Post by Ocxic on 2011-02-28
I have a small netbook that I would like to use as a terminal for my main computer, so instead of opening Gnome-terminal on my computer it will run from my netbook.

what i want to know is how to ssh from my netbook into my main computer and run an application on that computer.

So i would like to be able to ssh into my computer, and when i type "vlc movie.avi" it will open and run on the REMOTE computer just as if i had opened gnome-terminal and typed the command there.
Does anyone have an idea on how to do this?

thx

Note: I'm not looking for something/anything like "ssh -X" or VNC or Remote Desktop.

---

### Post by Smart Viking on 2011-02-28
This is something I also desperately want to know the answer to.
I've tried logging in and doing
```
export DISPLAY=:0.0
```
but it doesn't work. maybe this will work for the OP though.

---

### Post by HermanAB on 2011-03-01
Howdy,

First install OpenSSH Server on the desktop and make sure it works:
$ ssh user@localhost


Then from the netbook:
$ ssh -X -C -c blowfish user@desktopipaddress gnome-panel

or:
$ ssh -X -C -c blowfish user@desktopipaddress "gedit /etc/fstab"

---

### Post by Smart Viking on 2011-03-01
> **HermanAB said:**
> Howdy,

First install OpenSSH Server on the desktop and make sure it works:
$ ssh user@localhost


Then from the netbook:
$ ssh -X -C -c blowfish user@desktopipaddress gnome-panel

or:
$ ssh -X -C -c blowfish user@desktopipaddress "gedit /etc/fstab"
Hello. This will open the application on the client side, what me and the OP want to do is to launch the application in the X server on the server side.

---

### Post by Ocxic on 2011-03-01
^---What he said

---

### Post by Ocxic on 2011-03-06
> **Smart Viking said:**
> This is something I also desperately want to know the answer to.
I've tried logging in and doing
```
export DISPLAY=:0.0
```but it doesn't work. maybe this will work for the OP though.


yes this worked,, I can't believe i didn't try that sooner.

---

