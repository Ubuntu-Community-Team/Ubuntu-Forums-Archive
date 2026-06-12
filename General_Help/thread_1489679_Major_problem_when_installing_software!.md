---
title: "Major problem when installing software!"
date: 2010-05-21
forum: General Help
---

### Post by jaansson on 2010-05-21
I was trying to just make a routine update with the update-manager. When I did so, I ended up getting two errors. I tried update them in the terminal, but got the same errors, even with apt-get -f install. Here is what I got in terminal:

danne@danne-laptop:~$ sudo apt-get -f install apt-transport-https apt-utils libpangomm-1.4-1 software-center
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
Följande paket har installerats automatiskt och är inte längre nödvändiga:
  realpath fdutils
Använd "apt-get autoremove" för att ta bort dem.
Följande paket kommer att uppgraderas:
  apt-transport-https apt-utils libpangomm-1.4-1 software-center
4 att uppgradera, 0 att nyinstallera, 0 att ta bort och 0 att inte uppgradera.
1 är inte helt installerade eller borttagna.
Behöver hämta 658kB arkiv.
Efter denna åtgärd kommer ytterligare 8 192B utrymme användas på disken.
Läs:1 [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid-updates/main apt-utils 0.7.25.3ubuntu9 [236kB]
Läs:2 [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid-updates/main apt-transport-https 0.7.25.3ubuntu9 [80,7kB]
Läs:3 [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid-updates/main libpangomm-1.4-1 2.26.2-0ubuntu1 [62,2kB]
Läs:4 [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid-updates/main software-center 2.0.4 [278kB]
Hämtade 658kB på 1s (517kB/s)      
Ställer in apt (0.7.25.3ubuntu9) ...
dpkg (underprocess): kunde inte köra installerade post-installation-skript: Formatfel på körbar fil         *translation* : could not run the installed post-installation-script: Format failure on runable file.
dpkg: fel vid hantering av apt (--configure):     *translation* dpkg: failure when dealing with apt (--configure):
 underprocess installerade post-installation-skript gav felkod 2    *translation* the underprocess installed post-installation-script gave error code 2
Fel uppstod vid hantering:     *translation* An error appeared when dealing with:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)




Tried to translate it as good as possible, hope it's of any help :) I also tried installing other packages after this, and it gave me the same error. And I made an apt-get clean, without result. So basically, I can't install anything right now, kind of frustrating :confused:


Edit: Quite possible that my apt-get or software center or something is corrupted I guess, as one line in what I posted above says:

"1 är inte helt installerade eller borttagna."

It means "1 isn't fully installed or removed."

Does not sound promising to me, as it happened when upgraded apt and the software center.

---

### Post by Chesamo on 2010-05-21
Try an apt-get autoremove, then an apt-get -f install.

---

### Post by jaansson on 2010-05-21
Did not work. Same error again. Bu I start to suspect that something is corrupted with the apt things, as it happened the first time when I tried to update the apt and software center things. I also just saw that it said this when I tried autoremove:


0 att uppgradera, 0 att nyinstallera, 2 att ta bort och 4 att inte uppgradera.
1 är inte helt installerade eller borttagna.


The last thing means "1 isn't fully installed or removed." Trouble!?

---

### Post by jaansson on 2010-05-21
*Put a better title and more info to first post*

Failed changing the title though :P

---

### Post by jaansson on 2010-05-21
I tried running:


sudo apt-get -f remove --purge apt-transport-https apt-utils libpangomm-1.4-1 software-center


and it wanted to remove lots of programs, and seem to be working. But I did not dare to press yes, since it's the apt-utils and stuff. Would it really be that cleaver for me to remove those 4 packages and install them again? Or if I remove them, will I maybe not be able to install anything ever again?

---

### Post by jaansson on 2010-05-21
Like I suspected, some apt thing is broken it seems. Just found out this with aptitude:


Följande paket är TRASIGA:
  apt-transport-https apt-utils aptitude libept0 python-apt synaptic 
  tasksel ubuntu-minimal unattended-upgrades 



I means:

The following packages are BROKEN:
  apt-transport-https apt-utils aptitude libept0 python-apt synaptic 
  tasksel ubuntu-minimal unattended-upgrades 


How can I repair them?

---

### Post by jaansson on 2010-05-21
Fixed it!

I force-downgraded the package "apt". Then everything started working again.

---

