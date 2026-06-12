---
title: "Where does Synaptic put stuff?"
date: 2012-07-06
forum: General Help
---

### Post by Randy Schilling on 2012-07-06
I use Synaptic to install programs and I'm often left wondering to
what directory the programs and its files were place.

Most recently I installed libmysqlclient 
and I think I need to tell Netbeans where this link library is lacated to get my
C-embedded SQL to run.

Does the system keep installation logs?

---

### Post by oldos2er on 2012-07-06
Right-click on an installed package, Properties, Installed Files.

---

### Post by slixz85 on 2012-07-06
click up to your / directory and they go in /var/cache/apt/archives

---

### Post by slixz85 on 2012-07-06
as well most all system logs are in /var/log and i believe what installation would be is /var/log/apt

lol and i didnt read all your post. what i posted is where is downloads all the temporary .deb files

---

### Post by Randy Schilling on 2012-07-06
Thanks, thanks and thanks again -exactly  what I needed- many kind regards - Randy

---

### Post by oldos2er on 2012-07-07
Missed the other question you asked. APT logs are kept in /var/log/apt/
You can see this info in Synaptic in File, History.

You can also see installed files in terminal with **dpkg -L <package name>**

---

