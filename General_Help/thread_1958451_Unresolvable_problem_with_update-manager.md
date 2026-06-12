---
title: "Unresolvable problem with update-manager"
date: 2012-04-14
forum: General Help
---

### Post by la cónica on 2012-04-14
Can anybody help? I did something wrong while trying to install a s

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Type ‘n’ is not known on line 2 in source list /etc/apt/sources.list.d/plaxx-random-fixes-lucid.list, E:The list of sources could not be read.'

---

### Post by 2F4U on 2012-04-14
Seems to me as if something is wrong in your /etc/apt/sources.list. It could help if you post the content of the file.

---

### Post by Elfy on 2012-04-14
> 'E:Type &#8216;n&#8217; is not known on line 2 in source list /etc/apt/sources.list.d/plaxx-random-fixes-lucid.list, E:The list of sources could not be read.'

There is an error in a ppa list.

You can edit the file by hand if you know what it should be. 

```
gksudo gedit /etc/apt/sources.list.d/plaxx-random-fixes-lucid.list
```

If not where did you get the ppa from?

---

### Post by la cónica on 2012-04-14
It says...


# deb [http://ppa.launchpad.net/plaxx/random-fixes/ubuntu](http://ppa.launchpad.net/plaxx/random-fixes/ubuntu) maverick main
n

... I guess it's the n on the second line that is loose, I've deleted it and it's all fine. Thank you!!

---

### Post by Elfy on 2012-04-14
Looks like the PPA is disabled anyway unless there are other lines.

---

