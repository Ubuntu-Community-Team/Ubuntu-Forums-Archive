---
title: "kvpnc script"
date: 2011-12-04
forum: General Help
---

### Post by obrienn on 2011-12-04
Hi guys, I hope you can rescue me from this one.. I've been trying for a few hours now to get this to work. 

First off, I am trying to avoid using network-manager, not for any particular reason, I just prefer wicd. So I have a KVpnc, which works perfectly fine, I have a script that calls KVpnc and it runs perfectly from the terminal.

Script to run kvpnc:

#!/bin/bash
/usr/bin/kvpnc

Using WICD's script utility I asked it to run that script after a connection was made, it did not work. I can get it working with any other script, specifically my synergy script.

So then I looked into putting the kvpnc script into the /etc/network/if-up.d/ folder, which worked as an alternative also for my synergy script. It did not work though for my kvpnc script.

I have no clue how to get this beast to work. It works just fine when the script is called from terminal, but not when called from WICD or if-up.d.

I have guessed that it could be permissions and it is being run as root. I've tried chmod 777 and +x. Neither work. I've tried adding sudo chmod +x /usr/bin/kvpnc which still didnt work. 

Please help!!!

---

### Post by obrienn on 2011-12-04
62 views and no ideas lol? Still looking for a little bit of help! Any advice would be appreciated!

---

