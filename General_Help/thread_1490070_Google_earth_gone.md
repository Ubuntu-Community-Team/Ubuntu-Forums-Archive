---
title: "Google earth gone"
date: 2010-05-21
forum: General Help
---

### Post by bth73 on 2010-05-21
ubuntu 10.04 lost google earth today after todays update. Try to reinstall and get this:
sudo apt-get install googleearth
[sudo] password for bt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package googleearth is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package googleearth has no installation candidate
bt@bt-desktop:~$ 

Anybody know what's up?:confused:

---

### Post by -humanaut- on 2010-05-21
I don't know about google earth but there are some free open-source alternatives you could try such as World Wind & earth3d

---

### Post by wojox on 2010-05-21
Do you have the medibuntu repo's enabled?

Or you can install the googleearth-package from the repo's.

---

### Post by bth73 on 2010-05-21
medibuntu was disabled via update - re-enabled - no change - same message. Was working since 8.04, (almost 2 years), till today. Installed through terminal originally via multimedia how-to.
I think it was today's update. Different description in synaptic manager now. Go to googleearth and no linux download only bin file for windows.

now get this message: 
bt@bt-desktop:~$ sudo apt-get install googleearth
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by wojox on 2010-05-21
Look here [How to Install Google Earth in Ubuntu 10.04]("http://tombuntu.com/index.php/2010/05/02/how-to-install-google-earth-in-ubuntu-10-04/")

---

### Post by bth73 on 2010-05-21
THANKS wojox, working again. even picked up the address folder so all my addresses are still there.

---

### Post by wojox on 2010-05-22
Your welcome. :)

---

