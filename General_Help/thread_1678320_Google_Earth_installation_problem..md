---
title: "Google Earth installation problem."
date: 2011-01-30
forum: General Help
---

### Post by adeee on 2011-01-30
Hay guys first i want to tell you i install google earth two times.
Both time installation give problems.
and both time i install it from same thread. see [http://ubuntuforums.org/showthread.php?p=10408171#post10408171](http://ubuntuforums.org/showthread.php?p=10408171#post10408171)

First time i got Vlc and some other package problem.
means when i install it vlc theame changed. some of my games not run. see my vlc problem thread.[http://ubuntuforums.org/showthread.php?t=1676460](http://ubuntuforums.org/showthread.php?t=1676460)

when first time i only remove this file 
apt-get install lsb-core
and other remain there.

second time i got google earth not running problem.
now in my application-->internat area there are two google earth.

How can i remove both times installed google earth and get fresh google earth without any installation problem.?

---

### Post by cogier on 2011-01-30
Have you tried installing it from the **Ubuntu Software Centre**?

---

### Post by philinux on 2011-01-30
> **adeee said:**
> Hay guys first i want to tell you i install google earth two times.
Both time installation give problems.
and both time i install it from same thread. see [http://ubuntuforums.org/showthread.php?p=10408171#post10408171](http://ubuntuforums.org/showthread.php?p=10408171#post10408171)

First time i got Vlc and some other package problem.
means when i install it vlc theame changed. some of my games not run. see my vlc problem thread.[http://ubuntuforums.org/showthread.php?t=1676460](http://ubuntuforums.org/showthread.php?t=1676460)

when first time i only remove this file 
apt-get install lsb-core
and other remain there.

second time i got google earth not running problem.
now in my application-->internat area there are two google earth.

How can i remove both times installed google earth and get fresh google earth without any installation problem.?

Get it this way.
[https://help.ubuntu.com/community/GoogleEarth#Google%20Earth%20download%20of%20.deb%20files](https://help.ubuntu.com/community/GoogleEarth#Google%20Earth%20download%20of%20.deb%20files)

---

### Post by walkseverywhere on 2011-01-30
Just followed the instructions on this page and it worked like a charm. 

[http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/)

---

### Post by adeee on 2011-01-30
guys i really appreciate your response. and yes i want to use google earth but tell me first how i remove both google earth. because its install two times with different methods.
then am able to install again with your method.
:(

---

### Post by gandaran on 2011-01-30
> **adeee said:**
> guys i really appreciate your response. and yes i want to use google earth but tell me first how i remove both google earth. because its install two times with different methods.
then am able to install again with your method.
:(
that depends what type of package you used to install google-earth, if it was .deb packages then open synaptic package manager look/find google earth and mark for complete removal then click the apply button.
if you used any other package post which one.

---

### Post by mosaic2s on 2011-01-30
you can try thist first -

> sudo apt-get install lsb-core

then check if google earth is opening and running. mine was doing nothing till i installed this. now it is running like a charm.

---

