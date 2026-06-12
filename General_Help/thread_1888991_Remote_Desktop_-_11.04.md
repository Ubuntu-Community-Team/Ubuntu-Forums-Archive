---
title: "Remote Desktop - 11.04"
date: 2011-11-30
forum: General Help
---

### Post by GJohanns on 2011-11-30
I am trying to setup Remote Desktop services in 11.04. After checking the 'Allow other users to view your desktop' and 'Allow other users to control your desktop' the system does a check. That check always comes back with "Other users can access your computer using the address LOCALHOST" and any attempt to connect to the machine fails. 

I have seen a number of posts about checking and unchecking the 'Allow other users to view your desktop' option, but that has not worked. I have rebooted with it checked, and unchecked. Spent a half-hour simply checking and unchecking it. Closing the window sometimes, sometimes not.

Are there any other solutions to this issue that I am just missing? 

This is a new install, and the only option that I have that is not vanilla is I have the auto-logon setup so I don't have to enter a password to logon. This results in the Keychain service not initializing correctly if I check the 'Require the user to enter this password:' option I must also enter my Keychain password first.

Thanks,
Gabe

---

### Post by deonis on 2011-11-30
How do you connect to your machine and from where ?  Do you have the firewall enabled ?  You can always install vnc server on ubuntu and ssh server if you want to connect from outside your local network.

---

### Post by GJohanns on 2011-11-30
I am connecting to the machine using TightVNC from the local LAN. I have not edited the configuration for the default Firewall. (My understanding is that the Remote Desktop app, when enabled, would do that for me.) but will look into that issue now.

I understand that I can install the full VNC Server, but that just seems redundant. Why install another copy of VNC when the default Ubuntu install has it already bundled with it? That is not a rhetorical question.  If installing the another VNC Server package will add additional features, be easier to config, work better I am all for it! I am just wondering why replace what is already on the machine. 
Thanks!

---

### Post by GJohanns on 2011-11-30
I have tried connecting to both the IP address and the hostname. I can PING both, so DNS is working to resolve the name correctly. I have also tried to specify the session ID by entering IP_ADDRESS:0 and REMOTE_HOSTNAME:0, but this fails also. 

Because there are other users having issues with this when the 'access your computer using the address LOCALHOST' is shown in the dialog box for the Remote Desktop config screen I think it is a problem on the server machine.

---

### Post by deonis on 2011-11-30
There is perhaps nothing wrong with the default installation, but I usually configure it "my way". I use tihghtvncserver and firewall enabled on my pc. In firewall I open port 22 for ssh and port 5900-5904, you can open only one. Also I edit /home/user/.vnc/xstartup file to enable fluxbox instead of gnome. Of course you will need to create this file by using "tightvncserver" command in terminal. Here is the output: 

New 'X' desktop is denis-desktop:1

Starting applications specified in /home/denis/.vnc/xstartup
Log file is /home/denis/.vnc/denis-desktop:1.log

to check your vnc server type vncviewer localhost:5901

After that you should be able to connect locally (see above) and outside your local zone using vncviewer -via User@"ip of your sshserver inside the local area"  "ip of your vncserver":1


cheers

denis

---

