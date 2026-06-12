---
title: "Init scripts tutorial?"
date: 2006-03-16
forum: General Help
---

### Post by commodore on 2006-03-16
I would like to change the init scripts. I know there are simple things like BUM, but I want to do it the hard way so I can learn some Linux again. Are there any tutorials how to change them?

---

### Post by Ivan Matveich on 2006-03-16
Save your executable to /etc/init.d/$n and run 'update-rc.d $n defaults'.

$1 will be 'start' or 'stop' indicating the action to be taken.

---

### Post by Ivan Matveich on 2006-03-16
n/t

---

### Post by codejunkie on 2006-03-16
[QUOTE=commodore]I would like to change the init scripts. I know there are simple things like BUM, but I want to do it the hard way so I can learn some Linux again. Are there any tutorials how to change them?[/QUOTE]
[**[COLOR="Blue"]here[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=89491") is a great howto, that shows you how to disable services and describes what there for and do. if you wan't to make it a little harder, you can use this guide to find the services you wan't to disable, then use the update-rc.d command to remove the services.
use
```
update-rc.d -f nameofservice remove
```
to remove a service and use
```
update-rc.d -f nameofservice defaults
```
to restore it to it's default value.

---

### Post by commodore on 2006-03-17
Thanks people.

---

