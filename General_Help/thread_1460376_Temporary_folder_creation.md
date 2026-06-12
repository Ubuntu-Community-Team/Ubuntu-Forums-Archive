---
title: "Temporary folder creation"
date: 2010-04-22
forum: General Help
---

### Post by nux_guy22 on 2010-04-22
I am looking for a way to create a temporary folder in Ubuntu with the ability to edit parameters.  Specifically, we would like to implement a simple security system using ZoneMinder (like a Dorgem set-up in Windows).  We would want to store the captured images locally, but have them automatically deleted after a set length of time (maybe 2 or 3 days).  What method would be best to accomplish this? Thanks!

---

### Post by anaconda on 2010-04-22
how about creating the folder under 
/tmp

the contents of /tmp are deleted each time you boot your machine.

---

### Post by nux_guy22 on 2010-04-22
Thanks for the reply. I've considered storing them in the /tmp, but the machine will probably always be left on.  I am looking for some way to set specific parameters regarding storage time.

---

