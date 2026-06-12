---
title: "vpnc Assistance"
date: 2009-08-20
forum: General Help
---

### Post by Wataru8675 on 2009-08-20
Just moved into my college and my school recommended I install the Cisco VPN program to access their wireless connection with better success (or something of the sort...I was kind of falling asleep...xD).  I found a tutorial on my college's website on how to install it on Linux ([found here]("http://dragon.mnstate.edu/vpnc/")) so I followed it.  I got to step 3 and ran into a problem:

```
kyle@Kyle-laptop:~$ IPSec gateway xxx.xx.xxx.xxx
bash: IPSec: command not found

```So then I did a search on the forum and found [this thread.]("http://ubuntuforums.org/showthread.php?t=1140509&highlight=IPSec")  I got through it (sudo vpnc) until it requested "Password for VPN [etc. etc.]:"  I typed in a password (as if I was making a new one), and after two requests for it, it said that "authorization was unsuccessful".  Is there a certain password I have to use to access this?

And, also, this doesn't relate to my central issue...but what does this vpnc thingy do, and why is it needed?

---

### Post by Wataru8675 on 2009-08-20
Either my questions are becoming difficult for the usual forum-browsers to handle or they're just getting lazier...  This is the 2nd or 3rd thread that I've had to bump...

---

### Post by Wataru8675 on 2009-09-10
Bump from the grave...I'm really not understanding this, despite my efforts to look for help elsewhere.  I'm running 8.04 now, so I'm pretty sure the process is very different.  I'm reading off the same tutorial as in my original post, and am stuck at step 3.  The file I'm required to edit isn't located at /etc/vpnc.conf, so I have no earthly idea as to where to find it.

---

### Post by hwttdz on 2009-09-10
The school should have given you a password for the vpn.  VPN is virtual private network, it's a way to pretend you're on the school local network when you're not, useful for things such as the library proxy.

---

### Post by QaysHP on 2009-10-06
Some campuses also use VPN to secure wireless traffic, rather than bothering with WPA[2]. This seems to be the case with your university.

You might find it easier to install the package network-manager-vpnc and add the VPN settings through the manager. (Network Manager is what opens up when you chose System->Preferences->Network Connections, or right click on the network icon from your panel.

The settings on the link you provided should be enough. These are just my guesses at what would be appropriate, but you may need to play with it.
gateway "199.17.118.250"
                           group name "wireless"
                           group password "dragon-wireless"
user name [YOUR MSUM USER NAME]
user password [YOUR MSUM PASSWORD]
domain and the other settings can be left as default.


Edit:
The settings for the iPhone/iPod touch will work for this as well and can be found at
[http://www.mnstate.edu/it/wireless/iphone.shtml](http://www.mnstate.edu/it/wireless/iphone.shtml)
Or, if you don't want to manually change any settings, download the EXE file from the link bellow and extract it with the built in Ubuntu unarchiver. Then when you are in Network-Manager, on the VPN tab chose to Import and point it to the PCF file you extracted from the EXE.
[http://www.mnstate.edu/cm/installs/VPN.htm](http://www.mnstate.edu/cm/installs/VPN.htm)

---

### Post by dcstar on 2009-10-06
> **Wataru8675 said:**
> Just moved into my college and my school recommended I install the Cisco VPN program to access their wireless connection with better success (or something of the sort...I was kind of falling asleep...xD).  I found a tutorial on my college's website on how to install it on Linux ([found here]("http://dragon.mnstate.edu/vpnc/")) so I followed it.  I got to step 3 and ran into a problem:

```
kyle@Kyle-laptop:~$ IPSec gateway xxx.xx.xxx.xxx
bash: IPSec: command not found

```


You **do not** enter lines that should be in a file as commands.

It clearly says "**Edit/Add the following Lines:**" to the vpnc.conf file. Your system has the facility to search for files.

---

