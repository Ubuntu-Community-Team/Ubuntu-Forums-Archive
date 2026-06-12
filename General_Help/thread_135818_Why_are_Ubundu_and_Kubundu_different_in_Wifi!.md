---
title: "Why are Ubundu and Kubundu different in Wifi?!"
date: 2006-02-24
forum: General Help
---

### Post by ESM on 2006-02-24
Hi,

I am new to Ubuntu and Kubuntu. I tried Kubuntu but could not get my WiFi to work at all. The connections could never be made in networks.

I did the same after installing Ubuntu and it worked flawless...

I like Kubuntu best but without an internet connection it is worth nothing alas :(

If someone has a solution please let me know here!

---

### Post by tadashi on 2006-02-24
If you like KDE you can always try to load the KDE desktop using the package manager.  Then when you log in just select KDE under the session type.  I am not sure if this will break the WiFi but it should not.  I did the reverse by accident and was able to use a Gnome desktop on my Kubuntu.  However, do not uninstall the packages once you install them.  I tried that and it stripped KDE of everything and crashed the machine.  I had to reinstall afterwards.

---

### Post by gamma on 2006-02-24
The wifi manager (kwifi) doesn't seem to auto-connect to networks for me either. What I do to connect to wifi is 'sudo iwconfig wlan0 essid NETWORK' then dhclient wlan0. Of course wlan0 could be eth1 or something else for you..

What program are you using to manage your wireless network connections?

---

### Post by TheSoko on 2006-02-24
I've been using wifi-radar which is actually pretty nice.

Just sudo apt-get install wifi-radar.

---

### Post by ESM on 2006-02-25
Gamma, I will first try out your option. But the question still is, why does Kubuntu works differently than ubuntu where there is no problem at all for wifi?

Kubuntu sees my two wireless cards and can't ahndl;e them, while ubuntu shows all and just does what I tell it to do :)

I just come up with another option now: I will shut down the onboard wlan. Maybe that can help too. Conflict maybe netween wlan's?

---

### Post by Alterion on 2006-02-25
hmm i'll try that and see if it solves my wifi problem  too. In both kubuntu and ubuntu is that i have to do ```
sudo modprobe ndiswrapper
``` and then enable my card at every startup :(

---

### Post by ESM on 2006-02-25
Strange to see too that every pc seems tro act different with both Ubundu's...

---

### Post by ESM on 2006-02-25
The sudo option of Gamma worked with me too. Thanks a lot! I will install Dapper now because I see that there are far better options for networking in that distro.

I really hope that I will be able to do without Microsoft all together in a few months by using Ubuntu.

---

### Post by sadjack on 2006-02-25
I have been having this problem as well. My PC has Ubuntu installed and has worked from the first boot without any bother with the wireless card.

I've just bought a laptop with KUbuntu installed and the only way I can get the card to work is to activate it under kwifimanager and then issue the command ifup ra0. It has to be in that order too.I'm about to download the Ubuntu desktop, it will be interesting to see if there is a difference.

---

### Post by ESM on 2006-02-25
There is...

I downloaded, after I saw that it worked with the live cd, and installed Kubuntu dapper flight 4 and that installation worked different and all of sudden I could not do anything in the network system anymore...

I'm now downloading Ubunbtu to see how that dapper version does it now. It wouldn't surprise me if all goes well and then i can't think of anything else than saying to the developers that they are doing a terrible job at Kubuntu, alas.

---

### Post by essexman on 2006-03-19
[quote=ESM]There is...

I downloaded, after I saw that it worked with the live cd, and installed Kubuntu dapper flight 4 and that installation worked different and all of sudden I could not do anything in the network system anymore...

I'm now downloading Ubunbtu to see how that dapper version does it now. It wouldn't surprise me if all goes well and then i can't think of anything else than saying to the developers that they are doing a terrible job at Kubuntu, alas.[/quote]

This is a bug please go to [https://launchpad.net/distros/ubuntu...onf/+bug/35129]("https://launchpad.net/distros/ubuntu/+source/knetworkconf/+bug/35129")

and add a "me too" to get developers to fix it

---

### Post by Kosmonaut on 2006-03-20
@Alterion> hmm i'll try that and see if it solves my wifi problem too. In both kubuntu and ubuntu is that i have to do
Code:

sudo modprobe ndiswrapper

and then enable my card at every startup 

Have you tried to add "ndiswrapper" into etc/modules? ...This line will load ndiswrapper while the computer boots up. Tell me if it worked :cool:

---

### Post by fritzk3 on 2006-03-20
I booted with the live CD of Dapper Drake Alpha Flight 5, and while the wireless wasn't automatic, it certainly was pretty painless to start up.  Just give it the name of the router, and the WEP key, and off I go!

(Though it did do some strange fade-to-black thing, and then brought the screen back up - anyone know what that's all about??)

---

