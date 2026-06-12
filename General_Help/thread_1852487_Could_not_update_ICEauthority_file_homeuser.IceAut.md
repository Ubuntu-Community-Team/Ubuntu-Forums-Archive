---
title: "Could not update ICEauthority file home/user/.IceAuthority PROBLEM"
date: 2011-09-30
forum: General Help
---

### Post by Nadim.Khayrallah on 2011-09-30
Hi everyone it's my first post, I have a problem with my ubuntu system. I was installing an application via terminal, after rebooting the system this message showed up on startup : Could not update ICEauthority file home/user/.IceAuthority displays on startup, followed by there is a problem with the configuration server (/usr/lib/libcon2-4/gconf-sanity-check-2 exited with status 256)]


I searched for the directory in console, I found a home folder that is completely empty, and another home.backup followed by the date that contains all my data... 

I'm thinking of using rm- to remove the empty home directory, and then mv home.back home...

Any input will be highly appreciated, thank you all in advance :)

---

### Post by Nadim.Khayrallah on 2011-10-01
It is SOLVED :D

Did this:

Sudo passwd root

logged in as root

then:

mv. and renamed the backup to normal "home"

rebooted and all is perfect again :)

---

### Post by Rubi1200 on 2011-10-01
Hi and welcome to the forums :-)

We are glad you found a solution to the problem and are back in business.

Please mark this Solved using the Thread Tools near the top of the page.

---

