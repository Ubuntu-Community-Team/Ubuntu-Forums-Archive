---
title: "Net Connection getting inactive"
date: 2011-09-01
forum: General Help
---

### Post by vishal khialani on 2011-09-01
Hi,
I am using ubuntu 11.04 and I don't have a net connection problem if I am using the computer myself but the moment I put something to download and leave my computer for say a few hours the net connection becomes inactive and  my download never finishes.

I have to personally keep using the laptop for the download to finish.

Any clue why this is happening ?

Cheers,
Vishal

---

### Post by debd on 2011-09-01
are you using firefox to download the files?

AFAIK there's a offline mode in FF that is activated after some time of inactivity.
try disabling that.

---

### Post by vishal khialani on 2011-09-01
no, I am using bittorrent


cheers,
Vishal

---

### Post by icankzappa on 2011-09-01
mine also has quite the same problem..the wireless connection isn't stable, even though this doesn't happen all the time..
is possibly caused by a wrong setting?

btw, sorry to post this in your thread, visal :)

---

### Post by vishal khialani on 2011-09-01
no problem :)

 I think the problem is with the wifi .

All I need to do is turn it off and then on again and I am back online.


I think its the driver or a setting issue.


Cheers,
vishal

---

### Post by icankzappa on 2011-09-01
yeah..it's the best solution so far, i also want to check my AP setting

thanks

---

### Post by debd on 2011-09-01
I think network-manager is the root of the problem..it does not work well with some hardware.
have you guys tried wicd? Its a replacement for the default network manger and has been reported to work better in many cases.

[http://ubuntuguide.org/wiki/Ubuntu:Natty#Wicd_Network_Manager]("http://ubuntuguide.org/wiki/Ubuntu:Natty#Wicd_Network_Manager")
[http://www.liberiangeek.net/2010/10/replace-network-manager-wicd-network-manager-ubuntu-10-0410-10-maverick-meerkat/]("http://www.liberiangeek.net/2010/10/replace-network-manager-wicd-network-manager-ubuntu-10-0410-10-maverick-meerkat/")

---

### Post by icankzappa on 2011-09-05
> **debd said:**
> I think network-manager is the root of the problem..it does not work well with some hardware.
have you guys tried wicd? Its a replacement for the default network manger and has been reported to work better in many cases.

[http://ubuntuguide.org/wiki/Ubuntu:Natty#Wicd_Network_Manager](http://ubuntuguide.org/wiki/Ubuntu:Natty#Wicd_Network_Manager)
[http://www.liberiangeek.net/2010/10/replace-network-manager-wicd-network-manager-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/10/replace-network-manager-wicd-network-manager-ubuntu-10-0410-10-maverick-meerkat/)


it seems like my current wireless connection has QoS enabled because the download speed is less than what I suppose to get

i'll try your tip and this also [http://ubuntuforums.org/showthread.php?t=418394](http://ubuntuforums.org/showthread.php?t=418394)

thanks

---

### Post by vishal khialani on 2011-09-05
I tried different network managers and nothing seemed to work.. then I resintalled the default network manager and voila my problems got solved.

maybe thats the solution for everyone ?

---

### Post by icankzappa on 2011-09-06
> **vishal khialani said:**
> I tried different network managers and nothing seemed to work.. then I resintalled the default network manager and voila my problems got solved.

maybe thats the solution for everyone ?

what about your wireless connection? any additional driver needed? i'm getting frustrated on this particular prob :(

---

### Post by vishal khialani on 2011-09-06
nope. Just use ubuntu software management to remove the network manager connect  your land and reinstall it.

cheers,
vishal

---

### Post by vishal khialani on 2011-09-13
no additional driver :) just remove network manager and  reinstall  it.

---

