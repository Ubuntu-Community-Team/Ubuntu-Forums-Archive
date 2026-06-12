---
title: "RDesktop"
date: 2012-03-21
forum: General Help
---

### Post by ph4nt0m117 on 2012-03-21
How exactly do I use remote desktop?  Do I have to install an agent into a computer like with network lookout admin?  It would be useful at home when I have to access a comp in another room completely.

Any banter is greatly appreciated.

---

### Post by ajgreeny on 2012-03-21
If both computers are on the same router you can easily ssh between the machines as long as the host has openssh-server installed and the client has openssh-client.  On the client open a terminal and use command ```
ssh -X user@IP
```eg *ssh -X john@192.168.0.6* (You will need to know the IP of the machine).

You will then be asked for the password of the user on the remote machine, and once logged in can then open any application on that machine by using the appropriate command in the terminal, which by now will be showing the prompt as if it was the remote computer.

---

### Post by ccrs8 on 2012-03-21
Are both computers Ubuntu (or some other GNU/Linux distro)?  If so, then just use ssh like ajgreeny said.  If the remote computer is Windows, then you will either need to set it up for remote desktop use (it's in the control panel somewhere, depending on what version of Windows), and then you can use rdeskop (or any RDP-compliant client) to remote to it, again using the IP address.  There is also a SSH server available for Windows, utilizing cygwin.

---

