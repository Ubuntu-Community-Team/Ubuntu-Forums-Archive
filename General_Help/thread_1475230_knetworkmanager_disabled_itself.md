---
title: "knetworkmanager disabled itself"
date: 2010-05-06
forum: General Help
---

### Post by sonshadowcat on 2010-05-06
After I upgraded to ubuntu 10.04 my internet connection was working fine( both wired and wireless) and now all of a sudden knetworkmanager has disabled itself so I cannot get online at all. When I leave the mouse to hover over the icon it says unmanaged.

Does anyone know what could have caused this and if theres a fix?

---

### Post by jkclarkson on 2010-05-07
sudo dolphin
navigate to /var/lib/NetworkManager
open NetworkManager.state with kate
edit NetworkingEnabled=false to true
save
reboot

---

### Post by LK_gandalf_ on 2010-05-12
I had exactly the same problem on a laptop of a friend, unfortunately she is not able to remember if happened something particular before the problem (maybe some system updates).
These workout worked perfectly for me, thank you.

---

### Post by anupkshah on 2010-05-12
@jkclarkson: thank you -- that was exactly the problem I had.

@sonshadowcat: For me, network manager was all of a sudden disabled when trying to come out of sleep on my laptop. Since upgrading to 10.04, Kubuntu has been even better. The sleep (until this moment) had been flawless -- on my laptop I could repeatedly sleep without problems in 10.04 -- and for hours too.

By contrast, in earlier versions, sleep was hit and miss -- would work one time without reboot and only if sleeping for a couple of hours or less.

But this time, for some reason, trying to come out of sleep (for maybe half an hour) it never came back (the screen remained blank, no keyboard/mouse etc). I had to force a reboot. Since then the network manager was disabled. I am guessing there is a link there... Anyway, hope that gives some clues for others.

---

### Post by albert-I on 2010-05-22
> **LK_gandalf_ said:**
> I had exactly the same problem on a laptop of a friend, unfortunately she is not able to remember if happened something particular before the problem (maybe some system updates).
These workout worked perfectly for me, thank you.

I had the same, now i made the work and reboot

tank you

---

### Post by skierpage on 2010-06-02
This seems to happen if you ever have a problem on standby or shutdown.

The underlying NetworkManager bug is [Bug #524454 in network-manager (Ubuntu): “Networking is disabled on boot”]("http://https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454")

KDE's inability to restart networking is Bug [#553994 in network-manager (Ubuntu): “knetworkmanager doesn't connect with networkmanager”]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/553994") , the Debian bug is [576279 "network-manager-kde: Tray icon non-functional, shows "Network Management disabled" message"]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=576279")

If you don't want to reboot, after editing NetworkManager.state you can try entering in a terminal [FONT=Fixedsys]sudo restart network-manager[/FONT] ; you may also need to manually restart networking with commands like [FONT=Fixedsys]sudo dhclient[/FONT] and [FONT=Fixedsys]sudo ifconfig eth0 up .[/FONT] If those don't work, reboot.

---

### Post by axelmasok on 2010-06-09
This inconvenience just cost me an hour of work time. Thanks for the solution but I must say THAT BUG REALLY P^&%$D ME OFF! Kubuntu 10.04. Services automatically disabling themselves .... what's next?

---

### Post by maestrobwh1 on 2010-06-09
It did the same to me.  I am not sure why a fix has not been issued.

If you are having issues with suspending, I found that adding a script to /etc/pm/sleep.d with a filename in the 90's that issues a 5 second pause 100% fixed the issue on my laptop.

I called it 97quirk and the contents look like this

```

#!/bin/sh

#let other scripts catch up

case $1 in
    suspend|hibernate) sleep 5 ;;
    resume|thaw)       ;;
    *) exit $NA ;;
esac
exit 0

```

The sleep 5 just makes the computer hang out for 5 seconds.

Something is a muck with my one box.  Sleep works fine on 4 other machines but this one, it does not.  I would wake it to find that my desktop was still active, THEN it would lock the screen and present me with the password dialog.  Wrong order!  The extra 5 seconds solved it completely and then I did not get the knetwormanager issue.

This does not happen on an old acer, an old IBM thinkpad or two desktops.  Just this one ASUS 1201T EEEPC (sub notebook).

I think there are two bugs creating the perfect storm.  One seems to be the reported bug #553994 for network-manager and the other seems to be certain hardware botching the suspend.  Botched suspend = unclean network-manager state.

---

### Post by wbrokow1 on 2010-07-29
I have a hardwired fresh install of 10.04 and I don't have dolphin installed.  My network is accessible; all shares & router but no internet. I tried restating the network and all suggestions listed in the last few threads. i installed from a new livecd downloaded yesterday. the computer does get an ip address from the server.
Any help is appreciated.
Thanks,

---

### Post by perezomail on 2010-09-19
> **jkclarkson said:**
> sudo dolphin
navigate to /var/lib/NetworkManager
open NetworkManager.state with kate
edit NetworkingEnabled=false to true
save
reboot

well i did not have this problem on my desktop however i did have it on my net-book these instructions worked for getting my net-book to receive a landlines signal however i cannot see any wifi signal and manually entering the wifi signal did not work either any ideas? this seems to be a common problem since i have found this in more than one area in Kubuntu forum

after a few failed attempts with the above instructions i tried one last time but before i rebooted i wiggled that wifi cutoff switch some funny thing is i never go near that thing so i sooner forget about it. this may help  others on netbooks:P

---

### Post by Alasta on 2011-03-20
Perzomails fix worked for me . I think that the latest kde looks better than win 7 or snow leopard . pity its got a win 7 bug....

---

### Post by Alasta on 2011-03-20
Just looking at the age of this thread too...

Really

---

### Post by Gaba_p on 2011-04-18
A year later this sh#t keeps happening to me... Tried EVERYTHING and I can't get the wireless to work.

Getting really tired by now, I'm thinking I'll just have to move on to another distro..

---

### Post by dgray_from_dc on 2011-05-12
I've looked at one of the bug reports listed above and it says that this was fixed as of KDE 4.5.4 and that Maverick doesn't seem to have the same problem (Lucid is still using 4.4.5).

---

