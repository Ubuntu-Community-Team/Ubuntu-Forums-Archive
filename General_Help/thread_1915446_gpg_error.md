---
title: "gpg error"
date: 2012-01-26
forum: General Help
---

### Post by Amritpal on 2012-01-26
i have ocelot and was trying to install ubuntu tweaks from terminal and got this error...

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease: File /var/lib/apt/lists/partial/ppa.launchpad.net_tualatrix_next_ubuntu_dists_oneiric_InRelease doesn't start with a clearsigned message
E: Unable to parse package file /var/lib/apt/lists/partial/ppa.launchpad.net_tualatrix_next_ubuntu_dists_oneiric_main_i18n_Index (1)

before the installation of tweaks i was doing some updates and a dpkg error occured. So i got an option to either configure manually and also a new dialog box appeared suggesting me to partially install the updates. I tried to partially install them but then canceled it mid way. the above mentioned gpg error started from then onwards.

i am just a beginner, any help would be much appreciated.

---

### Post by jerrrys on 2012-01-27
Partial upgrades:

[http://ubuntuforums.org/showthread.php?t=1641400](http://ubuntuforums.org/showthread.php?t=1641400)

GPG errors:

[http://ubuntuforums.org/showthread.php?t=1914800](http://ubuntuforums.org/showthread.php?t=1914800)

ppa-purge:

This program disables a PPA from your Software Sources and reverts your
system back to the official Ubuntu packages. You can use this to return your
system to normal after testing a new version from a PPA.

In terminal enter:  sudo apt-get install ppa-purge

And welcome to the forum.

---

### Post by raja.genupula on 2012-01-27
> **Amritpal said:**
> i have ocelot and was trying to install ubuntu tweaks from terminal and got this error...

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease: File /var/lib/apt/lists/partial/ppa.launchpad.net_tualatrix_next_ubuntu_dists_oneiric_InRelease doesn't start with a clearsigned message
E: Unable to parse package file /var/lib/apt/lists/partial/ppa.launchpad.net_tualatrix_next_ubuntu_dists_oneiric_main_i18n_Index (1)

before the installation of tweaks i was doing some updates and a dpkg error occured. So i got an option to either configure manually and also a new dialog box appeared suggesting me to partially install the updates. I tried to partially install them but then canceled it mid way. the above mentioned gpg error started from then onwards.

i am just a beginner, any help would be much appreciated.
Hi Jerry 

@ OP 

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

For GPG erros follow jerry suggestions and while coming to the next errors do above code in terminal. 

All the best.
let us know what you got .

---

### Post by jerrrys on 2012-01-27
Hi Raja

I wonder if in this case would your command clear the GPG error.

@OP

Try Raja's suggestion first

---

