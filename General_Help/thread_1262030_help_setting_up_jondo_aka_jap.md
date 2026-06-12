---
title: "help setting up jondo aka jap"
date: 2009-09-09
forum: General Help
---

### Post by 26venger on 2009-09-09
can someone pleaze tell me how to install jap i punched in a bunch of commands but they didnt work.

---

### Post by creeddd on 2009-09-12
i also downloaded the jar file but dont know how to install it. if you get the answer please tell me

---

### Post by ackanao on 2009-09-12
Easiest way is to use JonDo repositores:

[https://www.jondos.de/en/download/linux]("https://www.jondos.de/en/download/linux")

[https://www.awxcnx.de/wabbel-en.htm]("https://www.awxcnx.de/wabbel-en.htm")

Do not forget to install JonDoFox profile:

[https://www.jondos.de/en/jondofox]("https://www.jondos.de/en/jondofox")

JonDo Client depends on Java - it's in the repos so just use: ```
sudo apt-get install sun-java6-jre
``` to install it.

---

### Post by Hoplophobia on 2009-10-11
Attempting to use their repository generates an error when trying to download and add the Key.

sudo apt-key add 0x12BD5A35.asc 
gpg: can't open `0x12BD5A35.asc': No such file or directory

Edit: Are there alternate, manual instructions available? Following the manual instructions on the JonDo website also results in failure.

---

### Post by ackanao on 2009-10-11
Try copying the key to your text-editor (like gedit) and import it manually via synaptic.

---

### Post by pelastikbintang on 2010-02-27
> **ackanao said:**
> Easiest way is to use JonDo repositores:

[https://www.jondos.de/en/download/linux]("https://www.jondos.de/en/download/linux")

[https://www.awxcnx.de/wabbel-en.htm]("https://www.awxcnx.de/wabbel-en.htm")

Do not forget to install JonDoFox profile:

[https://www.jondos.de/en/jondofox]("https://www.jondos.de/en/jondofox")

JonDo Client depends on Java - it's in the repos so just use: ```
sudo apt-get install sun-java6-jre
``` to install it.

ive tried this..doesn't work for me...i also tried to install sun java6...but failed..huhu

---

### Post by akabanekuroido on 2010-08-13
Dear Ubuntu members.
I also struggled with installling Jondos, but found out what I did wrong and what seems to be wriiten in the incorrect word order at Jondos.
This is how I installed Jondos:

JonDos Install on Ubuntu
First go to: [http://anonymous-proxy-servers.net/en/jondo/download](http://anonymous-proxy-servers.net/en/jondo/download).
Go to the Linux section on the left side. There you click on "KEY", (Schlüssel, in German)and save it with Firefox (save page as). Now you have the GPG key.
First go to your system software Sources: System > Administration > Software Sources> Authenticate. (need to type in your password). Here you can add your recently saved GPG key.

Now go to your system -Software Sources: System > Administration > Software Sources  Choose: software source (its where you can add APT command line). Now choose: add, and copy the atp line:
_**deb [http://debian.anonymous-proxy-servers.net](http://debian.anonymous-proxy-servers.net) lucid main **_ (also include: deb at the beginning)
(lucid is Ubuntu 10) Now click close. A screen will appear. Choose: reload. Now this part is done and your GPG key will also be validated and loaded. If you do this the wrong way, just as like its written at Jondos, it won't work and you can't install.

Final: Go to your command line (terminal editor), there you copy this command:
sudo aptitude update
Install starts. When ready copy this command line:
sudo aptitude install jondo jondofox-en
Jondos and JondosFox will install.

Now Jondos is installed. You can now start Jondos from your applications menu >internet >Jondos. Now close Firefox and start Jondo fox. A Jondos profile will be added. With this profile you can surf the internet like a ninja.

---

### Post by akabanekuroido on 2010-08-13
Dear Ubuntu members.
I also struggled with installling Jondos, but found out what I did wrong and what seems to be wriiten in the incorrect word order at Jondos.
This is how I installed Jondos:

JonDos Install on Ubuntu
First go to: [http://anonymous-proxy-servers.net/en/jondo/download](http://anonymous-proxy-servers.net/en/jondo/download).
Go to the Linux section on the left side. There you click on "KEY", (Schlüssel, in German)and save it with Firefox (save page as). Now you have the GPG key.
First go to your system software Sources: System > Administration > Software Sources> Authenticate. (need to type in your password). Here you can add your recently saved GPG key.

Now go to your system -Software Sources: System > Administration > Software Sources  Choose: software source (its where you can add APT command line). Now choose: add, and copy the atp line:
deb [http://debian.anonymous-proxy-servers.net](http://debian.anonymous-proxy-servers.net) lucid main 
(lucid is Ubuntu 10) Now click close. A screen will appear. Choose: reload. Now this part is done and your GPG key will also be validated and loaded. If you do this the wrong way, just as like its written at Jondos, it won't work and you can't install.

Final: Go to your command line (terminal editor), there you copy this command:
sudo aptitude update
Install starts. When ready copy this command line:
sudo aptitude install jondo jondofox-en
Jondos and JondosFox will install.

Now Jondos is installed. You can now start Jondos from your applications menu >internet >Jondos. Now close Firefox and start Jondo fox. A Jondos profile will be added. With this profile you can surf the internet like a ninja.

---

