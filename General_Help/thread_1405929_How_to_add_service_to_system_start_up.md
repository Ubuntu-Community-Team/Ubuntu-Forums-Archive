---
title: "How to add service to system start up ?"
date: 2010-02-13
forum: General Help
---

### Post by karmic-koala on 2010-02-13
Hi,

My Ubuntu 9.10 Server does not automatically get an ip address at start up and I have to run 

```
sudo dhclient
```every time so I it connects to the network, gets an ip etc. This is fine so long as I am physically present. If I am accessing it remotely using SSH and reboot the system there's no way I can connect back again untill someone runs a sudo dhclient on the machine.

No I am trying to add dhclient to startup automatically. I was hoping to put it in 
/etc/rc2.d but to be able to run the script must be present in /etc/init.d. The dhclient command is located in /sbin

Creating a sym link in etc/init.d to point to /sbin/dhclient hasn't worked for me so far. I can't copy the command to  /etc/init.d before running ```
update-rc.d dhclient default 
```?? How else do I have it run at system start?

Any help appreciated.

---

### Post by giammy on 2010-02-13
Hi,

get a look at 

```
/etc/rc.local
```

that scripts is executed at boot time, so you can add your commands

bye
giammy

---

### Post by mickie.kext on 2010-02-13
Easiest way to do it would be to use System --> Preferences --> Startup Applications. It is on top panel. 

Then you can add (via "add" button") what will will be run on boot-up. You just type  **sudo dhclient** in command box, and as a name you type whatever you want. Then that command should be run on every startup.

---

### Post by karmic-koala on 2010-02-13
> **mickie.kext said:**
> Easiest way to do it would be to use System --> Preferences --> Startup Applications. It is on top panel. 


Thanks for the pointer but I am actually running a Ubuntu 9.10 Server ~ No GUI ~ :(

---

### Post by nothingspecial on 2010-02-13
Edit /etc/network/interfaces

and add```


auto eth0
iface eth0 inet dhcp
```

to the end of the file.

See [[COLOR="Magenta"]here[/COLOR]]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/network-configuration.html")

---

### Post by karmic-koala on 2010-02-13
> **giammy said:**
> Hi,

get a look at 

```
/etc/rc.local
```that scripts is executed at boot time, so you can add your commands

bye
giammy

Thanks a bunch! that worked, however just curious.... the method I was trying to use, what's that used for then? I mean Apache, FSFTPD and MySQL etc get loaded that way :) Am I just being daft or did I just miss something?

---

### Post by karmic-koala on 2010-02-13
> **nothingspecial said:**
> Edit /etc/network/interfaces

and add```


auto eth0
iface eth0 inet dhcp
```to the end of the file.

See [[COLOR=Magenta]here[/COLOR]]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/network-configuration.html")

I've already done that here's my interface file
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

---

### Post by giammy on 2010-02-13
> **karmic-koala said:**
> Thanks a bunch! that worked, however just curious.... the method I was trying to use, what's that used for then? I mean Apache, FSFTPD and MySQL etc get loaded that way :) Am I just being daft or did I just miss something?

tipically that method is used to start/stop services with scripts located in /etc/init.d:
those script follows a well defined syntax and convenctions.

The method I told you is quick and dirty to execute an arbitrary command at boot: 
but if you want a cleaner method for your problem, the solution is the one of nothingspecial.

bye
giammy

---

### Post by karmic-koala on 2010-02-13
Thank you Giammy. That makes sense now.

---

