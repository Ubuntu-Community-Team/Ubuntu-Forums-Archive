---
title: "Consistenly Locking Up and Cannot Find the Problem"
date: 2009-08-04
forum: General Help
---

### Post by tdeprato on 2009-08-04
Hi I am running :

 2.6.27-14-generic 

The last few days I have had a constant problem. My Linux just locks up. It does not do it in Windows at all, so I am assuming my hardware is fine. 

When it happens I can be doing anything....sometimes it just locks up while sitting idle. 

I cannot find anything in /var/logs/message ..it only show the hardboot and then the reconnection, no errors. 

When this happens my crtl-alt Function keys do not work, my keyboard is completely frozen, and my WIFI keeps flashing as it seems active. 

In the syslog this is what there was before the crash:

Aug  4 17:29:46 ubuntuxp NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 3 
Aug  4 17:29:51 ubuntuxp NetworkManager: <debug> [1249421391.133258] periodic_update(): Roamed from BSSID 00:23:69:49:9B:E4 (linksys) to (none) ((none)) 
Aug  4 17:29:53 ubuntuxp kernel: [ 2825.989947] wlan0: deauthenticated
Aug  4 17:29:53 ubuntuxp NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Aug  4 17:29:53 ubuntuxp kernel: [ 2826.004697] wlan0: authenticate with AP 00:23:69:49:9b:e4
Aug  4 17:29:53 ubuntuxp kernel: [ 2826.007452] wlan0: authenticate with AP 00:23:69:49:9b:e4
Aug  4 17:29:53 ubuntuxp kernel: [ 2826.007477] wlan0: authenticated
Aug  4 17:29:53 ubuntuxp kernel: [ 2826.007483] wlan0: associate with AP 00:23:69:49:9b:e4
Aug  4 17:29:53 ubuntuxp kernel: [ 2826.016090] wlan0: RX ReassocResp from 00:23:69:49:9b:e4 (capab=0x401 status=0 aid=1)
Aug  4 17:29:53 ubuntuxp kernel: [ 2826.016101] wlan0: associated
Aug  4 17:29:53 ubuntuxp NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 4 
Aug  4 17:29:53 ubuntuxp NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Aug  4 17:29:57 ubuntuxp NetworkManager: <debug> [1249421397.137251] periodic_update(): Roamed from BSSID (none) ((none)) to 00:23:69:49:9B:E4 (linksys) 
Aug  4 17:30:01 ubuntuxp /USR/SBIN/CRON[9912]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug  4 17:38:54 ubuntuxp syslogd 1.5.0#2ubuntu6: restart.

-----------------------------------------------

I am not sure where to look but it keeps happening. My system does not feel sluggish at all. 

Ideas?

---

### Post by blueridgedog on 2009-08-04
Some random ideas:

-try and boot an older kernel and see if this issue subsides
-take a look at this guide and see if any of the tips help:  [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)
-monitor your temperatures

---

### Post by tdeprato on 2009-08-06
Nothing seems to help. I only have one Kernel Version back on my machine, should I add another?  

Here is what I got from the last error log:

Aug  5 00:04:49 ubuntuxp kernel: [14893.218723] Pid: 0, comm: swapper Not tainted 2.6.27-14-generic #1
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<c037e7fb>] ? printk+0x1d/0x22
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<c0122c5a>] dequeue_task_idle+0x2a/0x40
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<c012113f>] dequeue_task+0xcf/0x130
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<c01211ea>] deactivate_task+0x1a/0x30
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<c037ee13>] schedule+0x4b3/0x790
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<c013269b>] ? wake_up_klogd+0xb/0x40
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<c0380931>] ? _spin_lock_irqsave+0x31/0x40
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<c013cabc>] ? __mod_timer+0xac/0xf0
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<c037f494>] schedule_timeout+0x84/0xf0
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<c013c400>] ? process_timeout+0x0/0x10
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<c037f48f>] ? schedule_timeout+0x7f/0xf0
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<f8cdba15>] iwl3945_send_cmd_sync+0xe5/0x280 [iwl3945]
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<c0147680>] ? autoremove_wake_function+0x0/0x50
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<f8cdc0dc>] iwl3945_send_cmd_pdu+0x3c/0x40 [iwl3945]
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<f8cdc2a0>] iwl3945_activate_qos+0xa0/0xc0 [iwl3945]
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<f8ce0071>] iwl3945_mac_conf_tx+0x141/0x150 [iwl3945]
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<f8c7f9e8>] ieee80211_sta_wmm_params+0x148/0x240 [mac80211]
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<f8c85a70>] ieee80211_rx_mgmt_beacon+0x120/0x280 [mac80211]
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<f8c85c45>] ieee80211_sta_rx_scan+0x75/0xb0 [mac80211]
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<f8c8c662>] ieee80211_invoke_rx_handlers+0x92/0x2a0 [mac80211]
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<f8c8c16c>] __ieee80211_rx_handle_packet+0x21c/0x320 [mac80211]
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<f8c8c929>] __ieee80211_rx+0xb9/0x1c0 [mac80211]
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<f8c7b316>] ieee80211_tasklet_handler+0xf6/0x120 [mac80211]
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<c01373f8>] tasklet_action+0x78/0x100
Aug  5 00:04:49 ubuntuxp kernel: [14893.218723]  [<c0137822>] __do_softirq+0x92/0x120


------------------

I am looking all this up but not sure what I am seeing actually. And many of these are tough to break down into a search topic. 

Thanks ....

---

### Post by utnubuuser on 2009-08-06
Have you added any new apps plugins or applets lately?  The only time I've had freezing issues was through some app, panel applet, or a plugin(firefox).  If you've got plugins in firefox, try disabling them.

And of course the usual "Is compix 3d enabled", and does the problem stop if compiz is disabled.

---

