---
title: "Booting Hangs after/during Configuring Network Devices (No Rescue Mode either!)"
date: 2006-02-11
forum: General Help
---

### Post by Fab on 2006-02-11
Hi!

Since yesterday afternoon, my ubuntu box doesnt want to boot anymore. It goes fine all the way till "Configuring Network Devices", but then it hangs (sometimes with, sometimes without [OK]). No Error message, no Beep, nothing. It just hangs. The disk is fine as far as I can tell, I can read them (so if any log files help, just tell me ;)) Since this is the first time I've run into such trouble, I have no idea where to even start... But I want my box back ;P. So, any help or advice would be really appreciated. 

Thanks in advance,
Fab

---

### Post by Fab on 2006-02-11
nobody? :(

---

### Post by SWAT on 2006-02-11
Your post is a bit unclear about the circumstances. Does your boot hang, or do you just need to wait a while before the boot continues? Do you always have network connection yes/no? What did you change in your networking files/configuration? 

I know that I need to wait a while (at boot time) when the time is being synched with the NTP timeserver.

---

### Post by mednamot on 2006-02-11
I had the same thing happen to me yesterday, while I was testing out my 2wire card - powered off, took out the 2wire, put back the Orinico, and booted fine.

I haven't had a repeat of it either...

---

### Post by Fab on 2006-02-11
[QUOTE=SWAT]Your post is a bit unclear about the circumstances. Does your boot hang, or do you just need to wait a while before the boot continues? Do you always have network connection yes/no? What did you change in your networking files/configuration? 

I know that I need to wait a while (at boot time) when the time is being synched with the NTP timeserver.[/QUOTE]

It hangs completely! I always have network connection over a wireless card, and didn't change anything in the network setup. The same box works just fine in windows. :-k

---

### Post by SWAT on 2006-02-11
You said you somehow could check your logs, that means you can log into the box somehow, right? If you can, check dmesg for output. It's always a good idea to take a look at your logs, they're in /var/log

---

### Post by Fab on 2006-02-11
I can check them because I can mount the partitions read only via windows (its a dual boot box ;))

edit: dmesg stops at the output of my wireless card getting initialised and authorizing with the AP
the last messages are: 

> [4294708.400000] acx_complete_dot11_scan: matching station found: mac1 [replaced!] joining
[4294708.400000] acx_cmd_join_bssid rates_basic 0003->03, rates_supported 0127->1f
[4294708.410000] <acx_cmd_join_bssid> BSS_Type = 2
[4294708.410000] <acx_cmd_join_bssid> JoinBSSID mac1 [replaced!]
[4294708.410000] Sending authentication1 request, awaiting response!
[4294708.410000] acx_set_status: Setting status = 2 (WAIT_AUTH)
[4294708.410000] <acx_set_timer> Elapse = 1500000
[4294709.910000] acx_timer: status = 2
[4294709.910000] resend authen1 request (attempt 2).
[4294709.910000] Sending authentication1 request, awaiting response!
[4294709.910000] <acx_set_timer> Elapse = 2500000
[4294709.911000] mac1 mac1 mac2 mac2 mac2 [replaced!]
[4294709.911000] Algorithm is ok
[4294709.911000] acx_process_authen auth seq step 2
[4294709.911000] acx_set_status: Setting status = 3 (AUTHENTICATED)
[4294709.911000] <acx_set_timer> Elapse = 1500000
[4294709.911000] Sending association request, awaiting response! NOT ASSOCIATED YET.
[4294709.911000] association: requesting caps 0x0051, ESSID xxxxxx
[4294709.914000] acx_set_status: Setting status = 4 (ASSOCIATED)
[4294709.914000] ASSOCIATED!
[4294711.411000] acx_timer: status = 4
[4294715.400000] FIXME: most likely needs refinement, first implementation version only...
[4294715.400000] get_mask 0x00000000, set_mask 0x00000040
[4294715.400000] setting RXconfig to 2010:0fdd
[4294715.400000] get_mask 0x00000000, set_mask 0x00000000 - after update
[4294715.400000] FIXME: most likely needs refinement, first implementation version only...
[4294715.400000] get_mask 0x00000000, set_mask 0x00000040
[4294715.400000] setting RXconfig to 2010:0fdd
[4294715.400000] get_mask 0x00000000, set_mask 0x00000000 - after update


where mac1 is and mac2 are mac adresses that I removed, and xxxx is the Essid of my AP

---

### Post by SWAT on 2006-02-11
I would recommend booting a Ubuntu Live CD. Then mounting your linux partition. After that you could edit a few config files, so would be disabling network 'initiation' at boot. Then you probably could get into your box and try to start networking manually  and then take a look where it goes wrong.

You described that you are using wireless? Native drivers or are you using something like Ndiswrapper?

Note: 
/etc/network/interfaces contains your networking cards (usually LAN, not WLAN). Try commenting them out (so in fact commenting all uncommented lines). Then save the file and reboot (try to get into your Ubuntu box)

---

### Post by Fab on 2006-02-12
[QUOTE=SWAT]I would recommend booting a Ubuntu Live CD. Then mounting your linux partition. After that you could edit a few config files, so would be disabling network 'initiation' at boot. Then you probably could get into your box and try to start networking manually  and then take a look where it goes wrong.

You described that you are using wireless? Native drivers or are you using something like Ndiswrapper?

Note: 
/etc/network/interfaces contains your networking cards (usually LAN, not WLAN). Try commenting them out (so in fact commenting all uncommented lines). Then save the file and reboot (try to get into your Ubuntu box)[/QUOTE]

Okay, I got into the box by booting dsl and commenting out the interfaces stuff, booting works then, I uncommented again, dhcp-ed to get IP (which only worked at the second attempt, so they problem might have been there?), and all works fine now. haven't tried to reboot though so far *g

(And I'm using the native acx100 drivers)

Thanks, at least I can use the box again now, although with still a bit of trouble left.

p.s. I switched from dhcp to static, maybe it works better now, I'll test later on

---

