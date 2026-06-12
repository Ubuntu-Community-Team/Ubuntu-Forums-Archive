---
title: "Help please my Update Manager isnt working"
date: 2011-04-12
forum: General Help
---

### Post by Tektronix on 2011-04-12
[INDENT]I install the following command in the terminal because i was trying to add ubuntu tweak to the repository, but after I installed the following  code i get   an error :(
can some body help me 

  

```
sudo add-apt-repository ppa:tualatrix/ppa
```




this is my error 





> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '.net/tualatrix/ppa/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-maverick.list'
[/INDENT]

---

### Post by plucky on 2011-04-12
Please post output from a terminal for ```
cat /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
```

When you see what is in there,it should look like ```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu maverick main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu maverick main

```

To edit the file use ```
gksudo gedit /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
```

and remove everything else.

Good Luck

---

