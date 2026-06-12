---
title: "Why is this script crashing?"
date: 2010-07-19
forum: General Help
---

### Post by fishLlama on 2010-07-19
I wrote a bash script to completely shut down my wireless because it was interfering with airmon-ng, part of the aircrack-ng suite.
However, when I run this, my computer crashes and the screen turns black.
I'm sort of perturbed.

Here's the script:
```
#!/bin/bash

#check for root
if [[ $EUID -ne 0 ]]; then
        echo "Run as root" 1>&2
        exit 1
fi
pses=$(ps -e) #get processes
#check for and shut down NetworkManager, avahi-daemon, and wpa_supplicant
if [ ! -z "$(echo $pses | grep -w NetworkManager)" ]; then
        stop network-manager >/dev/null && echo "stopped service network-manager"
fi
if [ ! -z "$(echo $pses | grep -w avahi-daemon)" ]; then
        stop avahi-daemon >/dev/null && echo "stopped service avahi-daemon"
fi
if [ ! -z "$(echo $pses | grep -w wpa_supplicant)" ]; then
        kill -9 $(echo $pses | grep -w wpa_supplicant | grep -w '[0-9]*') >/dev/null && echo "killed process wpa_supplicant"
fi
echo "Operation complete"

```Any help would be appreciated. :D
I am running Ubuntu Lucid 64-bit with GNOME.

---

### Post by fishLlama on 2010-07-19
Nevermind I solved it. Turns out I also needed the -o option enabled on the last instance of grep, that way I would only pass the match to kill -9. Oops. :p

---

### Post by fishLlama on 2010-07-19
Here's the finished script, in case anyone is interested:
```
#!/bin/bash

#check for root
if [[ $EUID -ne 0 ]]; then
        echo "Run as root" 1>&2
        exit 1
fi
pses=$(ps -e) #get processes
#check for and shut down NetworkManager, avahi-daemon, and wpa_supplicant
if [ ! -z "$(echo $pses | grep -w NetworkManager)" ]; then
        stop network-manager >/dev/null && echo "stopped service network-manager"
fi
if [ ! -z "$(echo $pses | grep -w avahi-daemon)" ]; then
        stop avahi-daemon >/dev/null && echo "stopped service avahi-daemon"
fi
wpa_check=$(echo $pses | grep -w wpa_supplicant)
if [ ! -z "$wpa_check" ]; then
        { kill -9 $(echo $wpa_check | grep -wo '[0-9]*') & } 2>/dev/null && echo "killed process wpa_supplicant"
fi
echo "Operation complete"

```

---

