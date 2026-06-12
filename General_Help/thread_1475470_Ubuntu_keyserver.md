---
title: "Ubuntu keyserver"
date: 2010-05-06
forum: General Help
---

### Post by Primefalcon on 2010-05-06
Not so sure if this is the right place or not.....

but [Ubuntu's keyserver page]("http://keyserver.ubuntu.com/") just brings back a default it works page....

Is there a way to manually search or enter keys here, since this page seems to not have been completed? Doesn't look like this page will be completed either last edit date on this page is Tue 06 Oct 2009 05:49:36 AM CDT

---

### Post by jbrown96 on 2010-05-07
No you have to get the keycode from the ppa page. It's much easier now. Every PPA page has a PPA name like ppa:nvidia-vdpau/ppa and you can add it with the gpg key in one step with ```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
``` 
The keyserver is unreliable, so don't be discouraged if you get timeout errors. I had to try about 10 times the other day.

---

