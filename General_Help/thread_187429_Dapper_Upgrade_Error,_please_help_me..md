---
title: "Dapper Upgrade Error, please help me."
date: 2006-06-03
forum: General Help
---

### Post by truenemesis on 2006-06-03
I am using update-manager to upgrade. I dont want a fresh install because i dont have firewire and i dont have usb 2.0. 

so when I use update-manager, i get this error.

Failed to fetch [http://kubuntu.org/packages/kde351/dists/dapper/main/binary-i386/Packages.gz](http://kubuntu.org/packages/kde351/dists/dapper/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/dapper/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/dapper/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/dapper/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/dapper/Sources.gz) 404 Not Found

please help, as i cant do fresh install and i really really want the new ubuntu version.

---

### Post by Dr. Nick on 2006-06-03
Did you just edit your sources.list to change all breezy to dapper? What those message mean is the site doesnt exist. I just tried the first link and it doenst work because they dont have a dapper folder, only breezy. and links 2 and 3 look like old entries since no breezy stuff is thier. 

If i were you i would just delete them 3 lines from the file /etc/apt/sources.lst and  try again

---

### Post by truenemesis on 2006-06-03
but arent those files really important? and those were the sources that were default through update-manager. i didnt mess with my sources.list before hand....

---

### Post by Dr. Nick on 2006-06-03
[quote=truenemesis]but arent those files really important? and those were the sources that were default through update-manager. i didnt mess with my sources.list before hand....[/quote] 
Hmm.. I dont know exactly what they do, all I know is that I dont have them. I installed the release canidate of dapper so I didnt have to do a breezy upgrade. If you dont want to delete them then just open the file like this

sudo gedit cat /etc/apt/sources.list


and put a # before each line and then save and try again

I wouldnt think that they are to important since they are not from the official ubuntu site, If you added them along time ago for something else they could still be their

---

