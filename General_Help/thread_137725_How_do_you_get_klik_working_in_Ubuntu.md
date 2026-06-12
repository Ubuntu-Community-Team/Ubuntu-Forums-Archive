---
title: "How do you get klik working in Ubuntu?"
date: 2006-02-28
forum: General Help
---

### Post by fipple on 2006-02-28
How do you get klik working in Ubuntu? 
[http://klik.atekon.de/](http://klik.atekon.de/)
I pasted the suggested script after typing "sudo" 
but then there was a message saying I need ar. 
Please tell me how to get that package and install it on Ubuntu 5.10.

---

### Post by yanik on 2006-02-28
I don't know, but why would you want to do that?

Ubuntu already has the best package manager out there, along with every other debian based distro.

---

### Post by MartinG on 2006-02-28
You don't need to use sudo, just paste the full line (wget klik.atekon.de/client/install -O -|sh) in a terminal as a user.  It's not a package, just a script to set up your system and install the klik packages.

As to why anyone wants it, the repositories don't contain everything, and sometimes they don't have the latest versions.  klik is a useful extra.

---

### Post by towsonu2003 on 2006-03-03
[http://klik.atekon.de/wiki/index.php/Troubleshooting#I_get_.22Xdialog:_command_not_found.22](http://klik.atekon.de/wiki/index.php/Troubleshooting#I_get_.22Xdialog:_command_not_found.22)

---

### Post by probono on 2006-12-18
Please look here:

[http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Which_command_should_I_use_to_prepare_.28K.29Ubuntu_for_klik.3F](http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Which_command_should_I_use_to_prepare_.28K.29Ubuntu_for_klik.3F)

You need to use "sudo apt-get install binutils libstdc++5 rpm gnome-about" and THEN install the klik client by pasting "wget klik.atekon.de/client/install -O -|sh" into a terminal window.

Regards,
probono

---

