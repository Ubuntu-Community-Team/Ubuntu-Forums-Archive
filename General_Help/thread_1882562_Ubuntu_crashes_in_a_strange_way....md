---
title: "Ubuntu crashes in a strange way..."
date: 2011-11-17
forum: General Help
---

### Post by Max81ga on 2011-11-17
Hi all. I have a big problem with ubuntu 10.10 (i did the update from 10.04 and i had the same problem..). When i use it, this happens:
 
- the wi-fi disconnects
- the mouse doesn't work (and the touchpad too)
- the keybords don't work (both the one in the laptop and an usb connected keybord)
 
But the other things seem to work.. for example if i was watching a video, the video still go on.. an animation on a web syte go on.. an installation go on.. but obviously i can't use the pc. After a reboot from a crash, it can crash ofter minutes or after hours, i didn't find any rules! any particular conditions! It can happen also that i launch ubuntu, do login and without doing anything else it crashes after some minutes. 
 
I have an ASUS K50IN laptop with Duo T6600 cpu and NVIDIA Geforce G102M graphic card.
 
Some hours ago i read the /var/log/syslog file at the exact moment of the crash, it reports that:
 
"
Nov 17 10:31:05 ubuntu kernel: [ 1979.508040] No probe response from AP 00:1d:6a:87:e2:27 after 500ms, disconnecting.
Nov 17 10:31:05 ubuntu wpa_supplicant[928]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 17 10:31:05 ubuntu NetworkManager[909]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Nov 17 10:31:05 ubuntu kernel: [ 1979.542868] cfg80211: All devices are disconnected, going to restore regulatory settings
Nov 17 10:31:05 ubuntu kernel: [ 1979.542876] cfg80211: Restoring regulatory settings
Nov 17 10:31:05 ubuntu kernel: [ 1979.542882] cfg80211: Calling CRDA to update world regulatory domain
Nov 17 10:31:05 ubuntu kernel: [ 1979.549202] cfg80211: World regulatory domain updated:
Nov 17 10:31:05 ubuntu kernel: [ 1979.549209]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 17 10:31:05 ubuntu kernel: [ 1979.549214]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 17 10:31:05 ubuntu kernel: [ 1979.549219]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 17 10:31:05 ubuntu kernel: [ 1979.549224]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 17 10:31:05 ubuntu kernel: [ 1979.549228]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 17 10:31:05 ubuntu kernel: [ 1979.549233]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 17 10:31:05 ubuntu NetworkManager[909]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
" 
 
Please help me :-( thanks!

---

