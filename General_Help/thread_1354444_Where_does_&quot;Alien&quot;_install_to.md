---
title: "Where does &quot;Alien&quot; install to?"
date: 2009-12-13
forum: General Help
---

### Post by azitizz on 2009-12-13
Im just wondering if I am not looking in the right place or if something is wron with the installation of Alien to convert .rpm to.deb files. I dont see it after using synaptic to install it. Its marked as installed in the list of packages but i cant seem to find it? Is there any other way to search for it?
Thanks

---

### Post by kerry_s on 2009-12-13
alien is a command line program.
example:
alien /path/to/your/rpm

you should really check for deb of what ever it is your trying to install.
using non repo programs can mess up your system.

---

### Post by x33a on 2009-12-13
try the command
```
whereis alien
```

---

### Post by azitizz on 2009-12-13
I see, thanks. Im still new to the linux filing. I have an .rpm file of a canon printer driver (downloaded from the canon Asian website) I was told I would need Alien to convert it to a .deb file to install. Already its sounding alien to me but... Im here to learn. 
So how would I go about converting an rpm file on my desktop called scangearmp-mp510-1.00-1.i386.rpm ?

---

### Post by x33a on 2009-12-13
open a terminal, go to the desktop. once on the desktop give this command
```
alien scangearmp-mp510-1.00-1.i386.rpm
```
this will produce a deb file which you can install by double clicking on it.

---

### Post by azitizz on 2009-12-13
> **x33a said:**
> open a terminal, go to the desktop. once on the desktop give this command
```
alien scangearmp-mp510-1.00-1.i386.rpm
```
this will produce a deb file which you can install by double clicking on it.

It told me: [I]File "scangearmp-mp510-1.00-1.i386.rpm" not found.
[/I]
Not sure why its definately on my desktop. Should I put it somewhere else?

---

### Post by azitizz on 2009-12-13
Im trying to mark this thread as [SOLVED] but cant seem to see how. I managed to find the info needed. Any advice?
Thanks

---

### Post by x33a on 2009-12-14
just edit and add [Solved] to the title of the thread.

---

