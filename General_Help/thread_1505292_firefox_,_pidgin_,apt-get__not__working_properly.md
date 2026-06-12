---
title: "firefox , pidgin ,apt-get  not  working properly"
date: 2010-06-09
forum: General Help
---

### Post by amite on 2010-06-09
hey yesterday after my system startup i connected internet using my  mobile broadband connectionn ,but after that except my torrent client no other web app. working.when i start firefox it doesn't load pages,when i start pidgin it doesn't connect my aim clients and also i can't connect on IRC channel.Even i can't update or install my system using apt-get.While my torrent client is working fine.
I don't remember what i did before  my last successful restart.
I already restart my system several time but it doesn't work.:confused:

================================================
i don't want to come back on windows but due to this problem i have to come back.....:mad:please help!

---

### Post by lovinglinux on 2010-06-09
Your torrent client is clogging the network. You need to set the UPLOAD limit in the torrent client to 80% of the real UPLOAD bandwidth limit. Also reducing the number of maximum connections and the connections per second might help. See [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923)

---

### Post by amite on 2010-06-09
woh...i forgot to mentioned that even after quiting the torrent client the same problem remain.

After reboot when i connected to the network i first try firefox but as it didn't work so i gave a try to pidgin it also didn't work after that i started Xchat it gave the error message.After all i tried $sudo apt-get update but it also failed.
After all that when i start my torrent client, it works.(So i confirmed it's not the  problem with my network connection).

When i tried with firefox i was supposing it's problem with firefox......but now after several restart and finding problem with other web app. i can't figure out what is the problem?

---

### Post by lovinglinux on 2010-06-09
If they don't work after closing the torrent client, then try to restart your router/modem.

---

### Post by amite on 2010-06-09
> 
If they don't work after closing the torrent client, then try to restart your router/modem.


ok i will be back after trying this...

Thnx....

---

