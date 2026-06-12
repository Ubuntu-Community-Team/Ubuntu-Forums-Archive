---
title: "Trouble setting up a counterstrike 1.6 server"
date: 2012-04-15
forum: General Help
---

### Post by korovacow on 2012-04-15
I'm having some trouble setting up a CS 1.6 server.

```
alex@korova-milkbar:/home$ sudo mkdir cstrike
alex@korova-milkbar:/home$ cd cstrike
alex@korova-milkbar:/home/cstrike$ sudo wget http://www.cstrike-planet.com/dls/hldsupdatetool.bin
--2012-04-15 18:30:33--  http://www.cstrike-planet.com/dls/hldsupdatetool.bin
Resolving www.cstrike-planet.com... 64.237.53.18
Connecting to www.cstrike-planet.com|64.237.53.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3513408 (3.4M) [application/octet-stream]
Saving to: `hldsupdatetool.bin'

100%[============>] 3,513,408    653K/s   in 5.9s    

2012-04-15 18:30:39 (580 KB/s) - `hldsupdatetool.bin' saved [3513408/3513408]

alex@korova-milkbar:/home/cstrike$ sudo chmod +x hldsupdatetool.bin
alex@korova-milkbar:/home/cstrike$ ./hldsupdatetool.bin
bash: ./hldsupdatetool.bin: No such file or directory
alex@korova-milkbar:/home/cstrike$ sudo ./hldsupdatetool.bin
```When I enter the last command - ./hldsupdatetool.bin - it should display some form of EULA and prompt for agreement, but this isn't happening - if I run as user it complains that the file doesn't exist (it does) and if I run as sudo nothing happens at all. I've tried obtaining the file from alternative sources. I've checked other guides for this but they all describe the process in the same way. Any ideas?

---

### Post by korovacow on 2012-04-15
Managed to find a fix. The solution was as follows:

```
sudo apt-get install lib32gcc1
```Not sure why this fixed it, but there you go!

---

