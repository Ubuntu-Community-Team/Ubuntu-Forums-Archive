---
title: "Broken Dependency Tree"
date: 2009-12-31
forum: General Help
---

### Post by Linux_Newbee on 2009-12-31
Hi, 
every once in a while (month or so) , I get this red error circle on the apt bar telling me that a problem occured when the system was searching for updates. I can't open the Synaptic Package Manager because it fails to complete a dependency tree. 
When I go to the terminal and type in 
Sudo apt-get check 
or
Sudo apt-get upgrade

the dependency tree again fails to complete. it gets to 50% and stops.

milen@milen-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Segmentation faulty tree... 50%



I dont know what to do next, 
Can anyone help me out? 
Thank you very much, 
LN

---

### Post by Pollox on 2010-01-01
This [older forum post]("http://ubuntuforums.org/showthread.php?t=19563") (searching the forums for a solution never hurts) suggests deleting the .bin files in /var/cache/apt/, which you can do with the terminal command:

```
sudo rm /var/cache/apt/*.bin
```

I don't know much about the error, but apparently it worked for them.

---

