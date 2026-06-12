---
title: "Could not initialize the package information"
date: 2011-05-10
forum: General Help
---

### Post by goPlayYourGuitar on 2011-05-10
I just installed Ubuntu 11.04 a couple days ago.  I went to system settings, double clicked update manager, and this came up:
could not initialize the package information
an unresolvable problem ocurred while initializing the package information
please report this bug against the 'update-manager' package and include the following error message:
  'E:Type'-2011-05-10' is not known on line 1 in source list/etc/apt/sources.list.d/medibuntu.list'

What does this mean?

---

### Post by plucky on 2011-05-11
> **goPlayYourGuitar said:**
> I just installed Ubuntu 11.04 a couple days ago.  I went to system settings, double clicked update manager, and this came up:
could not initialize the package information
an unresolvable problem ocurred while initializing the package information
please report this bug against the 'update-manager' package and include the following error message:
  'E:Type'-2011-05-10' is not known on line 1 in source list/etc/apt/sources.list.d/medibuntu.list'

What does this mean?

It means one of your sources.list files has superfluous information in it.

Open a terminal an post output of ```
cat /etc/apt/sources.list.d/medibuntu.list
```

This is what mine look like ```
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ natty free non-free #Medibuntu - Ubuntu 11.04 "Natty Narwhal"
# deb-src http://packages.medibuntu.org/ natty free non-free #Medibuntu (source) - Ubuntu 11.04 "Natty Narwhal"
```

Good luck

---

### Post by goPlayYourGuitar on 2011-05-11
I tried, this is what I got:

--2011-05-10 00:19:39--  [http://www.medibuntu.org/sources.list](http://www.medibuntu.org/sources.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 88.191.127.22
Connecting to [www.medibuntu.org|88.191.127.22|:80](www.medibuntu.org|88.191.127.22|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-05-10 00:19:40 ERROR 404: Not Found.

I'm confused.  What can I do now?

---

### Post by goPlayYourGuitar on 2011-05-11
Okay, I went to medibuntu.org and found this code

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list 
http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo 
apt-get --quiet update && sudo apt-get --yes --quiet 
--allow-unauthenticated install medibuntu-keyring && sudo apt-get 
--quiet update

and this

sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu

and now everything appears to be working.  
Thanks!

---

