---
title: "pear installation / package installation"
date: 2010-08-20
forum: General Help
---

### Post by veilig on 2010-08-20
I have pear installed on my local machine.  Everything is working correctly but a few things

1. to issue a pear command, i have to sudo - is this the normal behavior?
2. when I sudo pear install a package - I usually don't have access to run it as a normal user and either have to change owner/group of the files in /usr/share/php/PACKAGE  and permissions in /usr/bin/PACKAGE


This is my personal machine, so I'm the only user and changing the owner/group doesn't affect anyone else.  but I'm curious why these commands wouldn't just work for me out of the box?

I've tried copying over the /etc/pear.conf to my ~/.pearrc and set myself as the owner/group which then allows me to run pear as my user - but when I try to install a package it dies when trying to create the executable in /usr/bin.  This wasn't a big deal - I just changed the config to a dir in my path, but then when setting up hudson, these programs weren't in the path visible to hudson.  I feel like I'm heading down the wrong path and there is a better fix.  Anyone have ideas?

---

### Post by bobcollard on 2010-08-20
After reading about pear I have to wonder what it has that Synaptic Package Manager does not?

---

