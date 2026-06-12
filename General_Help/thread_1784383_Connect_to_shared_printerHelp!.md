---
title: "Connect to shared printer??Help!"
date: 2011-06-16
forum: General Help
---

### Post by DeMartini on 2011-06-16
I have a file server running 11.04 w/ a shared printer connected to it, all my windows machines see it as shared & connect to it no prob. My laptop running the same OS 11.04 can see all the shares but no printer???


I have been at this all day, someone please help! Thanks...

---

### Post by pqwoerituytrueiwoq on 2011-06-16
odd never had a issue with shared printer using 10.04
speaking of which i need to add my new printer to my laptop lets see how this goes
begin log...
system ->administration->printing
click add
select find network printer (under network printer)
type ip address under host (10.0.0.50)
click next
seems i need a driver
$ sudo add-apt-repository ppa:hplip-isv/ppa
$ sudo apt-get update
run update manager
[laptop is having issues with package manager]("http://ubuntuforums.org/showthread.php?t=1773079")
i do not want to run a partial upgrade
the printer was found i just did not have the driver for a hp deskjet 2050 on 10.04

---

### Post by DeMartini on 2011-06-16
Solved, thanks man...........

---

