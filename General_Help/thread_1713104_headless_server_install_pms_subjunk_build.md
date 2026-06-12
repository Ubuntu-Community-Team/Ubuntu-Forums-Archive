---
title: "headless server install pms subjunk build"
date: 2011-03-23
forum: General Help
---

### Post by adduds on 2011-03-23
Hi i have the paissaid deb package in my sources.conf file from which i installed pms-linux on my headless maverick server

i have an issue with certain mkv files transcoding and there headers to my ps3 so on the pms site i found the sb build downloaded the .tgz and unpacked it

where and how to i install the folder so the old pms-linux isn't used and my server auto runs the new one?

here's a list of the files

CHANGELOG         FAQ          linux    pms.jar  README     WEB.conf
CHANGELOG-SB.txt  LICENSE.txt  plugins  PMS.sh   renderers

so sum up

i have a program installed (pms-linux) 

i want to run the new one which from command line i would run ./PMS.sh on boot

and would still like to be able to run commands

(sudo /etc/init.d/pms-linux restart stop start)

---

### Post by adduds on 2011-03-23
any clue people?

this is all command line which i'm trying to learn and not sure how to accomplish this task... as i don't want to run a ssh terminal from my laptop open running the ./PMS.sh as this is the only way i know how to run it

on a headless media server how do i run the subjunk build at boot so it boots/loads when i start the computer

when i used the deb it just did

i found the /etc/init.d/pms-linux file which is an intense script

but i'd like the same fucntionatliy as running subjunk? possible? ie sudo /etc/init.d/pms-linux restart/stop/start etc...

---

