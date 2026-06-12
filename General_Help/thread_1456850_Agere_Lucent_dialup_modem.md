---
title: "Agere Lucent dialup modem"
date: 2010-04-17
forum: General Help
---

### Post by pseudo_nz on 2010-04-17
I've put Ubuntu 9.10 on a former XP Media Edition PC, and am having trouble getting dialup to work.

Scanmodem tells me that it's an Agere System Lucent modem, which I found drivers for and installed with no problem.  Returned it to the owner without testing the connection (I don't have dialup myself) and PPP can't detect the modem.

Did a bit of digging, and found a deb called agrsm_tools, which runs a few diagnostics and sets up a symlink.  I ran that, then tried PPP, and it detected the modem, dialed out and then hung.  So I tried wvdial, which worked - but only the once.

Each time the computer is rebooted, the configuration file for wvdial has reset to its default, and the tools script needs to be run again, creating a backup of the config file.  All of which is a bit complicated for the end user, who is very new to linux.

Can anyone help me figure out how to get the config file to *stick* between boots, and/or get PPP to work?

TIA

---

### Post by GeorgeVita on 2010-04-18
Hi **pseudo_nz**,
main configuration file for wvdial is **/etc/wvdial.conf** which possibly changes running again wvdialconf (or some other program). Usually a 'scan/setup' modem utility must be ran once.

If you cannot find the program which changes the configuration file, you can use a copy of that file to connect:
```
sudo cp /etc/wvdial.conf /etc/mywvdial.conf
```
To connect use --config= parameter:
```
sudo wvdial --config=mywvdial.conf
```

If the problem comes from another configuration file, post more data to find a solution.

Regards,
George

---

### Post by Silvertones on 2010-04-18
I had trouble with a USB dial modem. Not sure if it's at all related. George can probably comment. 9.1 has a bug. To get the modem to work I removed modemmanager with Synaptic.
Read ALL of it
[https://bugs.launchpad.net/ubuntu/+bug/469881](https://bugs.launchpad.net/ubuntu/+bug/469881)

---

### Post by pseudo_nz on 2010-04-19
Thanks guys, will work through your suggestion George, and the list of links on the Launchpad thread tomorrow, fingers crossed.

At the very least, I will try uninstalling modemmanager and then trying an external USB modem I've got - I used to have it running with no drivers at all, which would be infinitely easier :)

---

### Post by pseudo_nz on 2010-04-24
Turns out it was the modemmanager utility - once that was removed I could use both the internal and external modems.  Thanks for pointing me in the right direction (and sorry about the delay in getting back to you)!

---

### Post by Silvertones on 2010-04-24
Great.

---

### Post by aliirani on 2011-01-08
I use a lucent modem.
I can't install this modem in ubuntu 10.04!
Is there any idea to solve this problem?!
[http://ubuntuforums.org/showthread.php?p=10330831#post10330831]("http://ubuntuforums.org/showthread.php?p=10330831#post10330831")

---

