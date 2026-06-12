---
title: "Could not initialize the package information"
date: 2011-02-17
forum: General Help
---

### Post by jchase45 on 2011-02-17
I have this red Circle with a line through the middle in my system trey . 

Pressing it makes me launch update manager. But it fails and gives me this error 

[PHP]

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

[/PHP]

---

### Post by jchase45 on 2011-02-18
bump

---

### Post by jerrrys on 2011-02-18
guess you got a bug in update manager, try synaptic package manager

---

### Post by jchase45 on 2011-02-18
synaptics package manager gives this error , neither that or ubuntu software center will laod

[PHP]
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


[/PHP]

---

### Post by gordintoronto on 2011-02-18
Run Administration/Software Sources, and look for:
maverick-security_universe_binary

Un-click or delete that line.

---

### Post by jchase45 on 2011-02-19
nothing in the "other sources" list like that .

got some maverik stuff but no universal or security

---

### Post by jerrrys on 2011-02-19
i would hide that security file and see if it regenerates

---

### Post by jchase45 on 2011-02-19
how about a explanation

---

### Post by jerrrys on 2011-02-19
you create a folder and place this security folder in it.  try synaptics again and see if said folder will regenerate itself and maybe fix your trouble.  if not, no harm done and you can restore this folder

---

### Post by jchase45 on 2011-02-19
I have no idea where to find that

---

### Post by jerrrys on 2011-02-19
[attach]183910[/attach]

---

### Post by jchase45 on 2011-02-20
how do I change permission on it or log in as root?

---

### Post by jerrrys on 2011-02-20
have a care with what you do.  gksudo can be very unforgiving...

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+gksudo+nautilus&as_qdr=all&sa=Google+Search&lang=en#851](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+gksudo+nautilus&as_qdr=all&sa=Google+Search&lang=en#851)

---

### Post by jchase45 on 2011-02-20
that worked!

thanks :P

---

### Post by jerrrys on 2011-02-20
glad to hear that jc, please to mark your thread as solved

---

