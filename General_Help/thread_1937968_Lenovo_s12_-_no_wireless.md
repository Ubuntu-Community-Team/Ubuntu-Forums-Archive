---
title: "Lenovo s12 - no wireless"
date: 2012-03-08
forum: General Help
---

### Post by viciousalex on 2012-03-08
Hi all,

I have installed 11.10 wubi on my girlfriend's laptop, lenovo s12. No wireless detection. I found and tried this:

sudo rmmod acer_wmi && echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf

from this link:
[http://fakkelbrigade.eu/chris/blog/2010/12/wireless-not-working-in-ubuntu-on-the-lenovo-ideapad-s12/](http://fakkelbrigade.eu/chris/blog/2010/12/wireless-not-working-in-ubuntu-on-the-lenovo-ideapad-s12/)

 - nothing happens.

I have removed network manager by (by apt-get remove) and tried to install wicd: downloaded by another machine from [https://launchpad.net/wicd/+download](https://launchpad.net/wicd/+download)

I've installed wicd by
sudo python setup.py configure
sudo python setup.py install

wicd app is working yet now wireless detection what so ever.
wireless in winXP works perfectly.

I have reinstalled and tried a variety of things. It was very time consuming and I'm very frustrated. 

Any ideas?

---

