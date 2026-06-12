---
title: "help with bluetooth script"
date: 2009-09-03
forum: General Help
---

### Post by seven winter on 2009-09-03
hi all, wondering if anyone can help me with a script to scan for bluetooth devices. Im getting used to using bash now but not quite sure how to put this together. Basically i want it to scan for devices, i imagine i can use hcitool scan for that part, then if it returns my phones mac address or phone name  as true (which means my phones bluetooth is on) then do  "My command", if false (phones bluetooth is off) then "My command"

Example:
#!/bin/bash
hcitool scan "scan for device"

if 00:XX:00:XX:OO:XX or sony ericsson
then
"MY COMMAND"
else
"My COMMAND"

anyhelp?
cheers

---

### Post by adusty on 2009-09-12
Hello,
I was looking for infos no how to connect my ericsson mobile phone to my kubuntu and I stumbled in this post.

I still need to understand how do I configure bluez to make it work with kmobiletools (how do I pair the phone??) but I can answer on the script :)

The bash syntax for doing what you ask is something similar to that:

#!/bin/bash
if [ -z "`hcitool scan| grep XX:XX:XX:XX:XX:XX`" ] ; then
  echo No phone found
else
  echo Phone found
fi

---

