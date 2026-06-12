---
title: "ubuntu 11.04 x64 and my radeon card"
date: 2011-05-08
forum: General Help
---

### Post by ugsquish on 2011-05-08
ok I am running an ati radeonHD 4550 and ubuntu 11.04 x64. I have gone through the steps outlined in a number of forums with no love. I have tried removing and purging all fglrx parts and attempted to redownload and installing. I keep getting the message

E: /var/cache/apt/archives/fglrx_2%3a8.840-0ubuntu4_amd64.deb: subprocess new pre-installation script returned error exit status 1
and it then tells me that fglrx-amdcccle is a broken module and will not run the card under the drivers. any better ideas?

---

### Post by Blasphemist on 2011-05-08
Did you use this already?

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I searched Googlubuntu and Google for your error and all I found was this. I don't get an option to translate it so I'm afraid it doesn't do much for me.

[http://forum.ubuntuusers.de/topic/update-auf-natty-probleme-mit-propietaeren-tre/#post-2856929](http://forum.ubuntuusers.de/topic/update-auf-natty-probleme-mit-propietaeren-tre/#post-2856929)

---

### Post by ugsquish on 2011-05-08
The first site you posted I did go to and it was no help at all. :/ I checked the other site out and could not translate. But reading the message output in console I went to an sh file for ati in the usr/share file and edited it. forced removal of the files. I then ignored the restart recomondation and and attempted to install the drivers. then restarted. worked like a charm. there are lots of warnings in this course of action so I would only say to use it when all else fails.
 Thanks for the assist tho :D

---

