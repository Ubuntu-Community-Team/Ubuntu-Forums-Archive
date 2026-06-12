---
title: "Uninstalled package still showing up in update manager"
date: 2006-02-18
forum: General Help
---

### Post by jcl on 2006-02-18
Howdy,

Initially I installed webmin from the repository, since that version didn't work I uninstalled via synaptic and installed webmin manually. Everything is fine except that webmin is still showing up under software updates to be installed. When I run synaptic it still shows it to be uninstalled (i.e. the box next to it is unchecked)...

How do I get 'software updates' to stop showing this 'uninstalled' package?

Thanks!

---

### Post by dcstar on 2006-02-18
[QUOTE=jcl]Howdy,

Initially I installed webmin from the repository, since that version didn't work I uninstalled via synaptic and installed webmin manually. Everything is fine except that webmin is still showing up under software updates to be installed. When I run synaptic it still shows it to be uninstalled (i.e. the box next to it is unchecked)...

How do I get 'software updates' to stop showing this 'uninstalled' package?

Thanks![/QUOTE]
When you say "installed manually", do you mean with a dpkg command?

If so, then go back into Synaptic and see if it is listed in the "Installed (local or obselete)" status area, if so then Package-Lock Version it, that will stop the update prompt.

---

### Post by jcl on 2006-02-19
Sorry,

No I mean I downloaded, ungzipped, untarred the version from the webmin website... having nothing to do with packages...

Synaptic shows it totally uninstalled (the box is white) yet update manager still wants to update it.

:confused:

---

### Post by jcl on 2006-02-21
up

---

### Post by jcl on 2006-02-24
Don't tell me I've stumped the entire Ubuntu community with this one!?!?!?

---

### Post by jcl on 2006-02-28
upup

---

