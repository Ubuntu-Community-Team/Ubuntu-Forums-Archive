---
title: "Shorewall Not Starting On Server"
date: 2010-07-01
forum: General Help
---

### Post by ShapeShiftme on 2010-07-01
Good day all. Thanks for taking time to read this stupid propblem im having

I have a 3 interface shorewall setup (2 internet connections AND 1 Local Lan)
Now the setup is working perfectly that is untill i reboot my box.

The setup
==========
eth0 = local lan
eth1 = fixed ip adsl connection
eth2 no config as used for dsl connection
ppp0 internet connection 2. dsl dialup.

Now as i say all of this runsperfectly however it doesnt start at boot

Yes i do have /etc/default/shorewall startup=1
AND /etc/shorewall/shorewall.conf startup_enabled=Yes
And Yes the server does startup and is appently running.

The problem is that once the machine is booted internet doesnt work untill i run shorewall stop and then shorewall start again.

I have read on google [http://swiss.ubuntuforums.org/showthread.php?t=853024](http://swiss.ubuntuforums.org/showthread.php?t=853024)
that the problem might be with shorewall is not seeing my ppp0 connection till boot.
And therefore not starting properly

> I found my problem now.

It seems that somewhere down the line new versions of Ubuntu's start up  have interferred with shorewalls start up scripts and now dynamic dns  address can't be processed at boot time, most likely because the IP  addresses haven't become registered in the system yet. That explains why  the firewall will start when you manually kick it off once the desktop  is loaded.

I contacted the makers of shorewall but they just don't give a ****.  They told me that using DNS address was at my own risk and have no  solution to this problem.

However i cant find and fix for the senario.
I have tried adding wait_interface="ppp0" in default/shorewall
But to no avail.

Does anyone have a solution for this.
If not a direct solution perhaps someone can tell me to run a script after bootup has completed and il then tell shorewall to sop then start again in that script

Thanks for any help

Regards

---

### Post by ShapeShiftme on 2010-07-02
Has noone done this before. im sure there are many ubuntu users.

Or should i be be usung suse for my server and ubuntu for desktops

Regards

---

### Post by ShapeShiftme on 2010-08-01
I have discovered my own fix for this however crude it may be.

The problem boiled down to the server haveing to be stoped then started after boot.
So all i did id this and its working percectly, perhps not perfect, as it is not doing what its ment to however it works for my needs

Here is what i did 
Create a script that restarts firewall {Stop then start as restart doesnt work}

```

sudo nano /root/firewall_restart.sh

> 
#! /bin/bash
/etc/init.d/shorewall stop
/etc/init.d/shorewall start


chmod 755 /root/firewall_restart.sh

```


then i added the file to rc.local (I found out it runs after ubuntu has booted)

```
nano /etc/rc.local
> 
/home/donovan/firewall_restart.sh

```

I hope this helps someone out
Regards

---

