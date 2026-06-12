---
title: "just some linux questions"
date: 2009-07-29
forum: General Help
---

### Post by starcraftmaster on 2009-07-29
hey guys
my first question is
is their folders i can delete to make space (Temp folders or cache folders)
and is their a firewall for ubuntu 9.04? i heard theres one that comes with it
how can i enable it ?


also i still got a problem
i can't hibernate
when i hibernate it starts to and almost finishes and then it freezes and the screen says its got no signal but the computer is still on

---

### Post by Sockerdrickan on 2009-07-29
The firewall is a daemon afaik and it runs by default of course (iptables)
As for folders to delete there is a tool you can use in System> menu

---

### Post by jmszr on 2009-07-29
starcraftmaster,

Here is information about the Ubuntu firewall: [https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw) . gufw is the GUI for ufw (Uncomplicated FireWall), that can be found in the Synaptic Package Manager.

---

### Post by starcraftmaster on 2009-07-29
> **jmszr said:**
> starcraftmaster,

Here is information about the Ubuntu firewall: [https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw) . gufw is the GUI for ufw (Uncomplicated FireWall), that can be found in the Synaptic Package Manager.

is their a firewall with a easy GUI ?(easy program that i can deny and allow programs easily)

---

### Post by t0p on 2009-07-29
> **starcraftmaster said:**
> is their a firewall with a easy GUI ?(easy program that i can deny and allow programs easily)

Have you checked out **gufw**?

---

### Post by prshah on 2009-07-29
> **starcraftmaster said:**
> 
is their folders i can delete to make space (Temp folders or cache folders)
and is their a firewall for ubuntu 9.04?

how can i enable it ?

i can't hibernate


> **starcraftmaster said:**
> is their a firewall with a easy GUI ?(easy program that i can deny and allow programs easily)

You can clear downloaded package files that are no longer required with the terminal (Applications-Accessories-Terminal) command```
sudo apt-get clean
``` Mostly, you won't need to do any more housekeeping.

To enable the default firewall program in ubuntu, use the command```
sudo ufw enable
```

You can use gufw (graphical uncomplicated firewall) from the repositories to handle ports as required. Application based firewall handling requires more setup on your part.

You need swap memory more than or equal to your system memory to do hibernation. Check if you have swap memory active with the command```
swapon -s
```

---

### Post by starcraftmaster on 2009-07-29
> **prshah said:**
> You can clear downloaded package files that are no longer required with the terminal (Applications-Accessories-Terminal) command```
sudo apt-get clean
``` Mostly, you won't need to do any more housekeeping.

To enable the default firewall program in ubuntu, use the command```
sudo ufw enable
```You can use gufw (graphical uncomplicated firewall) from the repositories to handle ports as required. Application based firewall handling requires more setup on your part.

You need swap memory more than or equal to your system memory to do hibernation. Check if you have swap memory active with the command```
swapon -s
```


ok i did the hibernate command thing
this is it:
Filename                Type        Size    Used    Priority
/dev/sdb5                               partition    859436    11336    -1

nothing much but

also i got a other problem
its nothing that bad but 
its just the music program called rhythm music player lags a lot
when minimizing or maximizing Firefox or some thing like that the music will stop for a 1 sec or 2 

any way i will try the other things when i come back from school tomorrow
thanks for all the help so far

---

### Post by starcraftmaster on 2009-07-30
what about firestarter ? is that a good firewall?
is gufw free ?

---

### Post by abcuser on 2009-07-30
> **starcraftmaster said:**
> what about firestarter ? is that a good firewall?
is gufw free ?
Both Firestarter and Gufw are using very powerfull iptables firewall system included into Linux kernel.

Gufw is graphical interface of simplified ufw firewall program used in Ubuntu.

Gufw is open source software. It is very simple to use and it is perfect starting place for newbies.

---

