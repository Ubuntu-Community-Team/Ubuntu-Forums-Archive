---
title: "boot script"
date: 2006-02-09
forum: General Help
---

### Post by rkakkar on 2006-02-09
I have certain command which I want executed every time I reboot the machine. How can I go about doing so?

---

### Post by el3ktro on 2006-02-09
It depends on which command you want to execute.

Tom

---

### Post by rkakkar on 2006-02-09
Its to enable my bluetooth dongle:

modprobe l2cap
sudo modprobe rfcomm
sudo mknod /dev/rfcomm0 c 216 0
sdptool add --channel=10 OPUSH
sudo rfcomm bind /dev/rfcomm0 00:0F:DE:53:35:5B 10

I need the above commands to execute everytime I boot up.

---

### Post by el3ktro on 2006-02-09
Hmm okay, the problem is that sudo asks you for a password, so this wouldn't work automatically. But - as always - there's a solution: You can tell sudo that it should not ask for a password for these few commands.

Then you have to way of strting this automatically at boot:

Either you create a little init script and put it into /etc/init.d, or you create a little script and let this script run by Gnome autostart. If you go to "System -> Settings -> Sessions" you'll see that you can add programs which you want to start when Gnome loads.

To write a script whcih executes your commands, create a new file and put the following content in:

```

#!/bin/sh
modprobe l2cap
sudo modprobe rfcomm
sudo mknod /dev/rfcomm0 c 216 0
sdptool add --channel=10 OPUSH
sudo rfcomm bind /dev/rfcomm0 00:0F:DE:53:35:5B 10

```

Put this script into /usr/local/bin for example (the standard location for self-created little scripts). Then make it executable (chmod +x) and you can run it.


Tom

---

### Post by rkakkar on 2006-02-09
How do I tell sudo not to ask me for password for these commands?

---

