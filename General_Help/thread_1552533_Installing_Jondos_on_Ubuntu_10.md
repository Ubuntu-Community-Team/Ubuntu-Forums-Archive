---
title: "Installing Jondos on Ubuntu 10"
date: 2010-08-13
forum: General Help
---

### Post by akabanekuroido on 2010-08-13
**JonDos Install on Ubuntu**

First go to: [http://anonymous-proxy-servers.net/en/jondo/download](http://anonymous-proxy-servers.net/en/jondo/download).
Go to the Linux section on the left side. There you click on "KEY",  (Schlüssel, in German)and save it with Firefox (save page as). Now you  have the GPG key.
First go to your system software Sources: System > Administration  > Software Sources> Authenticate. (need to type in your password).  Here you can add your recently saved GPG key.

Now go to your system -Software Sources: System > Administration >  Software Sources  Choose: software source (its where you can add APT  command line). Now choose: add, and copy the atp line:
deb [http://debian.anonymous-proxy-servers.net](http://debian.anonymous-proxy-servers.net) lucid main 
(lucid is Ubuntu 10) Now click close. A screen will appear. Choose:  reload. Now this part is done and your GPG key will also be validated  and loaded. If you do this the wrong way, just as like its written at  Jondos, it won't work and you can't install.

Final: Go to your command line (terminal editor), there you copy this  command:
sudo aptitude update
Install starts. When ready copy this command line:
sudo aptitude install jondo jondofox-en
Jondos and JondosFox will install.

Now Jondos is installed. You can now start Jondos from your applications  menu >internet >Jondos. Now close Firefox and start Jondo fox. A  Jondos profile will be added. With this profile you can surf the  internet like a ninja.

---

