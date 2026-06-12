---
title: "/home (new install)"
date: 2006-06-01
forum: General Help
---

### Post by _simon_ on 2006-06-01
I have just installed a fresh copy of Dapper onto my other halfs machine.

Unless I chose the wrong install option I was given no choice as to where I wanted /home so it's defaulted to having it at the same location as the install.

How do I move it from there to a partition on another drive?

I want to move it to hda1

---

### Post by bollix47 on 2006-06-01
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by cleentrax on 2006-06-01
[edit] Sorry. Meant to start a new thread.

---

### Post by darkhatter on 2006-06-01
you need to edit your fstab file, I'm updating to the final version right now so I'm not sure of a easier option.

you need to add a line to fstab to make it work. 

not sure what you partition is but it should look something like this

/dev/sda2       /home    reiserfs defaults



just go 

sudo kwrite(gedit if your on gnome)
open up "/etc/fstab"

and add the following line (but change it for your partition)

/dev/sda2       /home     reiserfs defaults

This is how I would do it in slackware, I know there is a easier way you'll have to ask a real ubuntu user for that (This is my second day of using kubuntu)

---

