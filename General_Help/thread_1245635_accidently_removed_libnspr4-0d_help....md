---
title: "accidently removed libnspr4-0d help..."
date: 2009-08-20
forum: General Help
---

### Post by mtech84 on 2009-08-20
hello all i had problem with playing youtube videos on firefox it appeared black so i made a mistake i disable flash in firefox and try to install flash again from adobe site then i cud not install the package since there was the problem with library error which was this libnspr4-0d. so i completely removed this and then i lost network manager and related packages with this like ubuntu-desktop and then i restarted it and when i enter the username and password iy shows blank screen and i cannot see the display.

the system is ubuntu 9.04 and it has nvidia geforce 8100 built in graphics.

i tried to boot in with ubuntu 9.04 dvd and did resuce option but still i cannot install these lost packages with apt-get it gives error failed to fecth..

help please what to do i don't want to install it again...all over again


thx

---

### Post by mtech84 on 2009-08-20
please reply....

---

### Post by mtech84 on 2009-08-20
ding dong plz reply

---

### Post by mtech84 on 2009-08-20
what is this plz reply...:confused:

---

### Post by mtech84 on 2009-08-21
i found the solution . after login name and password u see blank screen with cursor, so after that ctrl+alt+f1 then login again 

mount ubuntu dvd 9.04 32 bit on /media/cdrom0 and go to main folder in cdrom there go in n directory and install network manager 1st after that install nvidia drivers similarly if you nvidia card from main n directory and once thats done.

you have working internet restart and follow the same upto command line and then type sudo apt-get install ubuntu-desktop follow the screen instructions , u r all set. and last thing sudo apt-get -f install and similarly for autoclean. and then restart you are back to normal...

thx:guitar:

---

