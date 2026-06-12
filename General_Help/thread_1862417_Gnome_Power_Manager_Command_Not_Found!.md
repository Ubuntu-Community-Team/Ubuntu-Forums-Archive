---
title: "Gnome Power Manager: Command Not Found!"
date: 2011-10-16
forum: General Help
---

### Post by decomp on 2011-10-16
Hi all!

(I'm using Lubuntu) and I installed gnome-power-manager from synaptic but it wont run at startup or from command line. If I try it just says 'command not found.' see:

```
hiro@Case:~$ sudo apt-get install gnome-power-manager
[sudo] password for hiro: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-power-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hiro@Case:~$ gnome-power-manager
gnome-power-manager: command not found

```

What do I do?

---

### Post by drs305 on 2011-10-16
When I use Dash and type "Power" (or System Settings > Power) it opens the same GUI as typing "gnome-control-center" in a terminal, if that is what you are looking for.

---

### Post by decomp on 2011-10-17
Sorry I should've mentioned I'm running ubuntu so most gnome stuff isn't installed. I'm just trying to use gnome-power-manager because I'm having problems with xfce4-power-manager.

So I don't have gnome-control-center. Thanks for replying though :)

---

### Post by hwttdz on 2011-10-17
I don't have it installed (also running xubuntu), I'd do a 

find / -xdev -name gnome-power-manager

And then make sure I had that in my path.

---

### Post by confused Bob on 2012-05-10
i have the same problem. 
Executing: sudo  find / -xdev -name gnome-power-manager

gives me: 

/usr/share/doc/gnome-power-manager
/usr/share/gnome-power-manager


how do i add "that in my path" ? 

greeting

---

### Post by woodyg on 2012-08-21
Have you solved your problems with this? I have had occasional crashes, where the laptop rather than suspend when closing the lid, crash and provide me with the login screen to Lubuntu when I open the lid. I googled a bit and found this

            > "standby" under Lubuntu 12.04 with xfce-power-manager  installed leads to irregular crashes (I guess crashes of the X-server). I  could not find any useful information about the crashes but figured out  that xfce-power-manager may be the culprit: After I deinstalled it and  reinstalled xscreensaver instead, standby seems solid again. [here]("http://sourceforge.net/tracker/index.php?func=detail&aid=3544172&group_id=180858&atid=894869"). It seemed to describe my issues, so I uninstalled xfce4-power-manager. As a replacement I tried to install gnome-power-manager, but just like has already been mentioned earlier in this thread, it doesn't seem to run. The command

```
gnome-power-manager
```leads to

```
gnome-power-manager: command not found
```How do I get gnome-power-manager working on Lubuntu?

---

### Post by woodyg on 2012-08-27
Anyone knows how how make gnome-power-manager work on Lubuntu? I don't want to go back to xfce4-power-manager, so I'm pinning my hopes on gnome-power-manager...

---

