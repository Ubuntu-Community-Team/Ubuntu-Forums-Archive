---
title: "red exclamation mark in ubuntu"
date: 2011-03-25
forum: General Help
---

### Post by vuvuzelarhapsody on 2011-03-25
Hi, I have a problem with updating files in the update manager. Each time i do an update a red exclamation mark shows up eith the following error message :

The update information is outdated. This may be caused by network problems or by a repository that is no longer available. Please update manually by clicking on this icon ant then selecting "check for updates"and check if some of the listed repositories fail.

I tried doing this manually but nothing happens. I get a message saying that my system is up to date, and just underneath that it says "the package information was last updated 17 days ago". 

can someone please help me fix this and get rid of the anoying red triangle :D

---

### Post by Smart Viking on 2011-03-25
Try doing it with apt-get instead from the terminal:
```
sudo apt-get update
```

---

### Post by Frogs Hair on 2011-03-25
Try System > Administration Synaptic Package Manager and reload it until all sources connect . Select installed upgradeable , mark for upgrade and apply.

The same can be done from the terminal with ```
sudo apt-get update && sudo apt-get upgrade
```   and then install the updates from the update manager. Keep trying until the sources connect . A lack of errors will indicate if you have been successful .

---

### Post by vuvuzelarhapsody on 2011-03-25
> **Smart Viking said:**
> Try doing it with apt-get instead from the terminal:
```
sudo apt-get update
```

I have tried this and this is what i get :

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by vuvuzelarhapsody on 2011-03-25
> **Frogs Hair said:**
> Try System > Administration Synaptic Package Manager and reload it until all sources connect . Select installed upgradeable , mark for upgrade and apply.

The same can be done from the terminal with ```
sudo apt-get update && sudo apt-get upgrade
```   and then install the updates from the update manager. Keep trying until the sources connect . A lack of errors will indicate if you have been successful .

Did this as well and i get the same error:

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

I suppose it is the same thing as Smart Viking suggested :) I'v tried reloding many times and i cant get past. Any other ideas as to what the problem might be?

---

### Post by plucky on 2011-03-25
That PPA doesn't exist for Maverick.

See [Here](http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/)

So open Software Sources and un-tick or delete that PPA as a source.

Then reload and see if the problem disappears.

Good Luck

---

### Post by Frogs Hair on 2011-03-25
Make sure the PPA is still valid for your version of Ubuntu and is being maintained.

---

### Post by vuvuzelarhapsody on 2011-03-25
Ok, im not sure i understood what u guys told me to do, but i tried installing ppa-purge 

"This program disables a PPA from your Software Sources and reverts your
system back to the official Ubuntu packages. You can use this to return your
system to normal after testing a new version from a PPA."

and the red exclamation mark dissapeared, but when i try reloding to upgrade software packages i still get the same error message.

I obviouslly didnt do what u asked me to, or i left something out. So, what next?:))

---

### Post by Frogs Hair on 2011-03-25
Open the update manager and in settings on the Ubuntu Software tab there is a server menu. Select other from the menu and choose  best server . Ubuntu  will run some tests to locate the best server for your area .

If you have removed the bad software source I'm not sure what else to try other than change sever and keep trying to reload the package manager.

---

### Post by rs99cool on 2013-04-13
I've got the same red exclamation point that keeps popping up even though when I ask to install updates it says everything is up to date.  Tried the "select best server" route and, if I remember correctly, it chose one in Singapore.  I'm in Panama and there's a huge one in Costa Rica and, of course, several in the US, so I'm not sure why it chose Singapore.  Anyway, logging out and logging back in gets rid of the red exclamation point, at least temporarily, until the next update notice.  You gotta love Linux.  With so many twists & turns, Windows was never this much fun!

---

### Post by sandyd on 2013-04-13
**Necromancing - thread closed**
Please do not post in threads more than one year old as many things change between Ubuntu releases, and the issues described may not be pertinent to your Ubuntu installation.

Thanks!

---

