---
title: "Unable to run script"
date: 2010-05-05
forum: General Help
---

### Post by toscal on 2010-05-05
Just had to re-install after I did some very silly things.
Running 9.10 Ubuntu with XBMC-live

Have gnome desktop, Firefox with adobe flash plugin.

I set up a script called myvpn to run openvpn and this used to work and now it doesn't
I did 
> chmod 755 myvpn
and when I type 
> ./myvpn

I get:
> bash:./myvpn: bin/bash: bad interpreter: No such file or directory

The script is 
as follows
> #!bin/bash
#open vpn script
sudo xset s off
sudo xset dpms 0 0 
cd Downloads/vpn 
sudo openvpn --config MyExpatNetwork.ovpn
If I manually type in each command it works, but the script doesn't any ideas?

---

### Post by lmarmisa on 2010-05-05
A "**/**" character is missing in the first line of your shell script:

> 
#!/bin/bash


Best regards,

Luis

---

### Post by toscal on 2010-05-05
oops I feel stupid
Thanks for the quick reply

---

