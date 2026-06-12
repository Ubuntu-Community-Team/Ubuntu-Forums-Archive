---
title: "Canon MP 560 ink level monitor"
date: 2010-05-15
forum: General Help
---

### Post by t2000kw on 2010-05-15
Has anyone found a useful solution to monitor ink levels in a Canon MP 560 printer? 

I was able to get the printer to work over a wireless network in Lucid but the printer properties do not show any ink levels. 

Donald

---

### Post by nomnex on 2010-06-19
it will only work with local printers.

libinklevel (cli) in the repos or inkblot if you need a gui.

---

### Post by hayhursm on 2011-01-03
> **t2000kw said:**
> Has anyone found a useful solution to monitor ink levels in a Canon MP 560 printer? 

I was able to get the printer to work over a wireless network in Lucid but the printer properties do not show any ink levels. 

Donald

Hope this helps, open Terminal and at command line type "sudo  apt-get update", "sudo apt-get install ink", and then "ink -p bjnp"  (all without quotes of course).  This detected my network printer and  reported back the ink levels.  I haven't looked for a GUI to accommodate  this command but I'm sure it can be done.

---

