---
title: "Install Python2.4 on Natty? (for Airpwn)"
date: 2011-08-17
forum: General Help
---

### Post by GrantStoner on 2011-08-17
So I've been looking to try out Airpwn, but it seems to only run with Python2.4. Natty, buy default uses Python2.7, and Airpwn will not compile with it. Python2.5 is the lowest in the repos. I tried just downloading Python2.4, and doing the "./configure, make, make install" dance, but I end up with```
root@L1NUX:~/Python-2.4# make
*[...code snipped to save space...]*
Aborted
make: *** [sharedmods] Error 134
```So, can anyone help me figure out **any** way to install Python2.4 on Natty? Any method will do fine. If you have a .deb that would be even greater. :)

Anyone who's been able to run Airpwn on something other than Python2.4 is also welcome to tell me their solution. :)

(There used to be a .deb for Airpwn itself, but it seems one was never made for Natty.)

---

### Post by GrantStoner on 2011-08-18
Bumpidy bump bump. Anyone, anyone? This is pretty important to me. And I'm still trying to get it to work to no avail.

---

### Post by GrantStoner on 2011-08-25
It's cool - don't all jump at once Ubuntu community - I've managed to solve it on my own. Good luck though to anyone else who comes across this issues; you'll have better luck asking me directly than posting a thread.

---

### Post by thefinn93 on 2011-10-31
Wait so you're just not gonna post your solution? gee, thanks

---

### Post by GrantStoner on 2011-10-31
Didn't feel it was necessary since no one else seemed concerned with installing Python2.4 on Natty except me.
[http://public.upfronthosting.co.za/debian/natty-amd64/](http://public.upfronthosting.co.za/debian/natty-amd64/) contains the .deb's I needed (minimal, full, and dev). If you need a different architecture or for Lucid or Maverick .deb's look in [http://public.upfronthosting.co.za/debian/](http://public.upfronthosting.co.za/debian/) someone graciously built .debs for each for the impatient. Or if you'd like to do it all your own follow the instructions here: [http://www.upfrontsystems.co.za/Members/izak/sysadman/how-to-compile-python2.4-packages-for-newer-versions-of-ubuntu](http://www.upfrontsystems.co.za/Members/izak/sysadman/how-to-compile-python2.4-packages-for-newer-versions-of-ubuntu)

---

