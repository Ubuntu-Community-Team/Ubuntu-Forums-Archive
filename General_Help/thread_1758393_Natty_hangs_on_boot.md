---
title: "Natty hangs on boot"
date: 2011-05-14
forum: General Help
---

### Post by shanbak on 2011-05-14
Hi,

When I boot Ubuntu 11.04 it goes as far as showing me the OS options (I dual-boot with Windows7) and then what should be the login window. However - here it displays the mouse and nothing else. It just hangs.

I can hit ALT-F1 and get a shell. I login and everything works as expected except X isn't running.

BACKGROUND: I tried to upgrade from 10.10 when (mid-upgrade) my computer turned itself off (suspect housemate unpluged it by mistake and then it ran out of battery). When I turned it on again, it refused to boot, complaining that the / drive was not there. After a bit of digging around I found that it was actually mounting / with read-only permissions. After remounting it with read/write permission I was able to continue with the upgrade. HOWEVER, I never managed to connect to the wireless from the command line (I tried all sorts, sudo iwconfig wlan0 essid "eduroam", sudo dhclient wlan0). Since it hadn't finished to download the new packages, I don't know what it did (presumably installed the ones it did have). Anyway, after doing this I rebooted and everything seemed to work - I logged in and (using update-manager) did a partial upgrade which seemed to work. The only problem was that it was now complaining that nautilus was not configured and for this reason it could not update a package called libglib2.0 or something like that. I tried to repair broken packages/reinstall nautilus etc nothing worked. I then rebooted (I don't remember why I thought that would be a good idea). Since it hasn't given me a GUI login window again. It just hangs, like I said. Help please.

Thanks.

---

### Post by Hedgehog1 on 2011-05-14
Your best option is likely a clean install of Natty/11.04.

If you can:

* Type 'startx' and see if that get you running for the moment
* Boot form the Windows side
* Use another PC

And then download the Natty ISO and make a LiveCD/LiveUSB.

Boot from it and backup your data, then:

From the 11.04 LiveCD/LiveUSB, you may have an upgrade path offered in the 'install 11.04'.

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

**If this is not offered**, if you have your data in a separate '/home' partition you can reinstall 11.04 over your 10.10 '/' partition and be sure to not format the '/home' partition:

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

### Post by shanbak on 2011-05-19
Thank you! Sorry to reply so late, but I've had (actual) work to do and so couldn't mind fixing natty in the past few days.

Here's an update: I haven't got around to doing a fresh install, not least because I've been too lazy to walk to the shop and buy a CD for burning the LiveCD with. It does seem though like a fresh install might eventually have to be the solution.

HOWEVER, I have managed to connect to the Internet from command line. The tricked proved to be stopping the Network Manager process:

```
sudo service network-manager stop
```

Them I could do the following:

```
lshw -C network
```

to obtain the logical name of my wireless interface (in my case: wlan0). Then

```
sudo iwlist wlan0 scan
```

to see if my wireless interface was picking up the signal from the wireless. NOTE: this wireless network was unencrypted! I think things get a bit more complicated once you have to deal with WEP/WPA etc. Anyway, once the above command listed all the signals my computer was picking up, I was able to get the ESSID of the connection I was interested in (in my case: OWL). I then did:

```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "OWL"
sudo iwconfig wlan0 mode Managed
sudo dhclient -v wlan0
```

and I was happily connected. I found these instructions in [this tutorial]("http://ubuntuforums.org/showthread.php?t=571188"). Anyway, I then used my command line VPN client to connect to the Internet and all was OK.

I then ran ```
sudo apt-get upgrade
``` and this claimed to upgrade 118 packages which (I assumed) were left inconsistent from the messy upgrade I'd done before. After this completed with no errors, I rebooted but nothing changed: it still booted up until when I would be meant to see a login screen, but instead of the login screen I get a mouse and nothing else. As before, I'm able to drop to a shell using CTRL+ALT+F1.

I've tried also:
```
sudo service gdm restart
```

which achieves nothing but to take me back to the blank screen with the mouse cursor in the middle. If I do

```
sudo service gdm status
```

It tells me that GDM is running with PID <bla>. If I try

```
sudo startx
```

it complains: gives some sort of error and returns. I would give you the error but I would have to copy it down first so I can't at the moment.

SORRY if I'm being stubborn about this - I think you are absolutely right that a clean install would probably solve all of my problems. But this is quite a good learning experience for me. I'm also just very very curious to understand how the hell it's come to be so broken :)

If you have any other thoughts, please share!

Thanks,
Maria

---

### Post by shanbak on 2011-05-23
I did a fresh install. Still, Natty seems pretty buggy :(
Oh well..

---

### Post by thorstenmz on 2011-05-31
Everybody looking for a solution, have a look here:
[http://ubuntuforums.org/showthread.php?t=1744681](http://ubuntuforums.org/showthread.php?t=1744681)

---

