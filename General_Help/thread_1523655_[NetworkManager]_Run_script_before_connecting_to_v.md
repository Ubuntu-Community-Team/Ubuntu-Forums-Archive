---
title: "[NetworkManager] Run script before connecting to vpn"
date: 2010-07-04
forum: General Help
---

### Post by revered on 2010-07-04
I am trying to run a script before starting to connect to a vpn (when clicking in the network manager applet). I googled: if-down.d if-post-down.d if-pre-up.d if-up.d   But couldn't find any good info, only bug reports. And as I understand those will run when an interface (which one?) is upped|etc...  I need to run the script BEFORE the vpn starts because it uses the command "host" and if the vpn has already started I cant access internet. The script setup routes for a list of host, so I would need to run another script to remove them after disconnecting the vpn or my normal connection wont work.

---

### Post by MarkoCro on 2011-03-23
Network Manager has all you need to run scripts triggered by Network Manager actions here is an example:

[http://www.techytalk.info/start-script-on-network-manager-successfull-connection/]("http://www.techytalk.info/start-script-on-network-manager-successfull-connection/")

---

