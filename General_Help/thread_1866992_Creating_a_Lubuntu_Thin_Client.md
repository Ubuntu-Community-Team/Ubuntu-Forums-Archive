---
title: "Creating a Lubuntu Thin Client"
date: 2011-10-22
forum: General Help
---

### Post by SteveDee on 2011-10-22
This is a really dumb idea, so why do it?

Well, I've just created 50 thin clients on a Windows network using ThinStation, on old desktop computers that were no longer quick enough to cope with either XP or Win7. I need to do the same with around 30 laptops, but unfortunately I can't get wireless to work using ThinStation. So while I continue to look for a ThinStation wireless solution, I decided to push ahead and use Lubuntu as a quick fix, as Lubuntu boots fast and wireless works on my hardware.

Here is a summary of what I've done. There are many more possibilities to tune the system up, such as removing unwanted software packages, but I still wanted access through an admin account to use the system as a Linux based Thick Client.

Basic procedure:-
1. Install Lubuntu, initially with a single admin account.
2. Install "rdesktop" via Synaptic Package Manager
3. Disable updates via Update Manager > Settings > Updates
4. Create a desktop user account (I've called mine "user") and apply further restrictions if necessary via Users & Groups > Advanced Settings > User Privileges.
5. Set to autologin for "user" (go to: /etc/xdg/lubuntu/lxdm/lxdm.conf & enter: autologin=user)
6. Now reboot to autologin as "user"
7. Probably a good idea to disable the screensaver
8. Create  a desktop login icon:-
 In a terminal type;
```

lxshortcut -i ~/Desktop/LoginRDP.desk

```
 In the Lxshortcut dialog, enter the command:-
```

rdesktop -d {domain} -u {default user} -f -n {client name} -r sound:local {server name}

```
 Example: rdesktop -d Hogwarts -u Harry -f -n laptop-12 -r sound:local RDP-server

 Also enter a name (the icon caption) and select an appropriate icon.

9. Create a Power Off icon using the same process. The command line should something like this:-
```

lxsession-logout -p "Shutdown Hogwarts Laptop?"

```
10. You can also create a simple help page & desktop icon using the web browser. Command line:-
```

chromium-browser /home/user/Help.html

```
 Note: this may give users internet access, but not via your domain.

11. Edit the desktop Panel (via right-click menu) and remove most things. Suggest you leave Volume & clock
12. Set Panel to auto-hide when not in use (or maybe set volume to max then delete the Panel?)
13. Final step (so do anything else you want to do now) is to make /home/use read-only

You can also get the system to connect to your Windows server automatically when it boots (as long as the network connects quickly) by creating a script containing your rdesktop command.
...so the script would basically look like this:-
```

#!/bin/sh
rdesktop -d Hogwarts -u Harry -f -n laptop-12 -r sound:local RDP-server

```
Call the script something like rdp.sh then add to /usr/local/sbin and set execution flag (right-click Properties > Permissions > Make the file executable).

Also add:-
```

@rdp.sh

```
...to end of: /etc/xdg/lubuntu/lxdm/lxdm.conf

Once you have the system working the way you want, you should be able to use Remastersys to create an install disk. Don't forget to change the client name via the rdesktop -n part of the command in your script and desktop icon, each time you deploy to a computer.

---

### Post by collisionystm on 2011-10-22
Awesome!

---

