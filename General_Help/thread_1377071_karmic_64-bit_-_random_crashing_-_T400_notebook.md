---
title: "karmic 64-bit - random crashing - T400 notebook"
date: 2010-01-09
forum: General Help
---

### Post by conmat on 2010-01-09
System:
T400 notebook, intel and ATI graphics, only intel graphics enabled.
9.10 64-bit, whole disc encryption.  New install.

My system recently started crashing periodically.  At first there was no problem. There is no particular program that causes a crash.

I haven´t edited any configurations.  The most recent packages I installed were some data recovery packages and Gkrellm.  Is there any way to find the time of installation for each package?

I upgraded to kernel 2.6.32

I´ve been looking at the syslogs and before every crash there are several lines of:

Jan  9 20:46:24 username wpa_supplicant[1677]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 20:48:24 username wpa_supplicant[1677]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 20:50:25 username wpa_supplicant[1677]: CTRL-EVENT-SCAN-RESULTS 

I did a google search on this error but the only real suggestion I found was the kernel upgrade.

Thanks

Here is a longer listing:

Jan  9 14:17:01 username CRON[4350]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  9 14:17:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:19:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:21:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:23:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:24:40 username wpa_supplicant[1602]: WPA: Group rekeying completed with 00:21:91:0e:35:4f [GTK=TKIP]
Jan  9 14:24:40 username NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Jan  9 14:24:40 username NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Jan  9 14:25:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:27:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:29:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:31:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:33:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:35:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:37:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:37:40 username nmbd[1596]: [2010/01/09 14:37:40,  0] nmbd/nmbd.c:71(terminate)
Jan  9 14:37:40 username nmbd[1596]:   Got SIGTERM: going down...
Jan  9 14:39:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:41:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:43:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:45:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:47:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:49:26 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:50:58 username gdm-simple-slave[5265]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jan  9 14:50:58 username NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 38)
Jan  9 14:50:58 username NetworkManager: <info>  (wlan0): deactivating device (reason: 38).
Jan  9 14:50:58 username acpid: client 3369[0:0] has disconnected
Jan  9 14:50:58 username acpid: client connected from 5276[0:0]
Jan  9 14:50:58 username NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 3719
Jan  9 14:50:58 username NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Jan  9 14:50:58 username avahi-daemon[1352]: Withdrawing address record for 192.168.0.190 on wlan0.
Jan  9 14:50:58 username avahi-daemon[1352]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.190.
Jan  9 14:50:58 username avahi-daemon[1352]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  9 14:50:58 username kernel: [10971.331632] wlan0: disassociating by local choice (reason=3)
Jan  9 14:50:58 username kernel: [10971.335221] wlan0: deauthenticated (Reason: 1)
Jan  9 14:50:58 username wpa_supplicant[1602]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  9 14:50:58 username wpa_supplicant[1602]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  9 14:51:00 username gdm-simple-greeter[5346]: WARNING: Unable to lookup user name solidsta: Success
Jan  9 14:51:14 username pulseaudio[5443]: pid.c: Stale PID file, overwriting.
Jan  9 14:51:17 username NetworkManager: <info>  Activation (wlan0) starting connection 'Auto <wireless>'
Jan  9 14:51:17 username NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jan  9 14:51:17 username NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  9 14:51:17 username NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  9 14:51:17 username NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  9 14:51:17 username NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  9 14:51:17 username NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  9 14:51:17 username NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan  9 14:51:17 username NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto <wireless>' has security, but secrets are required.
Jan  9 14:51:17 username NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan  9 14:51:17 username NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  9 14:51:17 username NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  9 14:51:17 username NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  9 14:51:17 username NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jan  9 14:51:17 username NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  9 14:51:17 username NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  9 14:51:17 username NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  9 14:51:17 username NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan  9 14:51:17 username NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto <wireless>' has security, and secrets exist.  No new secrets needed.
Jan  9 14:51:17 username NetworkManager: <info>  Config: added 'ssid' value '<wireless>'
Jan  9 14:51:17 username NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jan  9 14:51:17 username NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jan  9 14:51:17 username NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jan  9 14:51:17 username NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  9 14:51:17 username NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  9 14:51:17 username NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  9 14:51:17 username NetworkManager: <info>  Config: set interface ap_scan to 1
Jan  9 14:51:17 username NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan  9 14:51:19 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:51:19 username wpa_supplicant[1602]: WPS-AP-AVAILABLE 
Jan  9 14:51:19 username wpa_supplicant[1602]: Trying to associate with 00:21:91:0e:35:4f (SSID='<wireless>' freq=2412 MHz)
Jan  9 14:51:19 username wpa_supplicant[1602]: Association request to the driver failed
Jan  9 14:51:19 username NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan  9 14:51:19 username kernel: [10992.495629] wlan0: authenticate with AP 00:21:91:0e:35:4f
Jan  9 14:51:19 username wpa_supplicant[1602]: Associated with 00:21:91:0e:35:4f
Jan  9 14:51:19 username kernel: [10992.502987] wlan0: authenticated
Jan  9 14:51:19 username wpa_supplicant[1602]: WPA: Key negotiation completed with 00:21:91:0e:35:4f [PTK=CCMP GTK=TKIP]
Jan  9 14:51:19 username wpa_supplicant[1602]: CTRL-EVENT-CONNECTED - Connection to 00:21:91:0e:35:4f completed (reauth) [id=0 id_str=]
Jan  9 14:51:19 username kernel: [10992.502995] wlan0: associate with AP 00:21:91:0e:35:4f
Jan  9 14:51:19 username kernel: [10992.506142] wlan0: RX AssocResp from 00:21:91:0e:35:4f (capab=0x431 status=0 aid=1)
Jan  9 14:51:19 username kernel: [10992.506149] wlan0: associated
Jan  9 14:51:19 username NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jan  9 14:51:19 username NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Jan  9 14:51:19 username NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jan  9 14:51:19 username NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Jan  9 14:51:19 username NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '<wireless>'.
Jan  9 14:51:19 username NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  9 14:51:19 username NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan  9 14:51:19 username NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jan  9 14:51:19 username NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jan  9 14:51:19 username dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  9 14:51:19 username dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  9 14:51:19 username dhclient: All rights reserved.
Jan  9 14:51:19 username dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  9 14:51:19 username dhclient: 
Jan  9 14:51:19 username NetworkManager: <info>  dhclient started with pid 5625
Jan  9 14:51:19 username NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan  9 14:51:19 username NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan  9 14:51:19 username NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Jan  9 14:51:19 username NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jan  9 14:51:19 username NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan  9 14:51:19 username dhclient: Listening on LPF/wlan0/00:21:6a:7f:8b:8c
Jan  9 14:51:19 username dhclient: Sending on   LPF/wlan0/00:21:6a:7f:8b:8c
Jan  9 14:51:19 username dhclient: Sending on   Socket/fallback
Jan  9 14:51:21 username dhclient: DHCPREQUEST of 192.168.0.190 on wlan0 to 255.255.255.255 port 67
Jan  9 14:51:21 username dhclient: DHCPACK of 192.168.0.190 from 192.168.0.1
Jan  9 14:51:21 username dhclient: bound to 192.168.0.190 -- renewal in 35191 seconds.
Jan  9 14:51:21 username NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Jan  9 14:51:21 username NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan  9 14:51:21 username NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jan  9 14:51:21 username NetworkManager: <info>    address 192.168.0.190
Jan  9 14:51:21 username NetworkManager: <info>    prefix 24 (255.255.255.0)
Jan  9 14:51:21 username NetworkManager: <info>    gateway 192.168.0.1
Jan  9 14:51:21 username NetworkManager: <info>    nameserver '192.168.0.1'
Jan  9 14:51:21 username NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan  9 14:51:21 username NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan  9 14:51:21 username NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan  9 14:51:21 username avahi-daemon[1352]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.190.
Jan  9 14:51:21 username avahi-daemon[1352]: New relevant interface wlan0.IPv4 for mDNS.
Jan  9 14:51:21 username avahi-daemon[1352]: Registering new address record for 192.168.0.190 on wlan0.IPv4.
Jan  9 14:51:22 username NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Jan  9 14:51:22 username NetworkManager: <info>  Policy set 'Auto <wireless>' (wlan0) as default for routing and DNS.
Jan  9 14:51:22 username NetworkManager: <info>  Activation (wlan0) successful, device activated.
Jan  9 14:51:22 username NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan  9 14:51:23 username wpa_supplicant[1602]: CTRL-EVENT-SCAN-RESULTS 
Jan  9 14:51:32 username ntpdate[5689]: adjust time server 91.189.94.4 offset -0.021789 sec

---

### Post by 73ckn797 on 2010-01-09
If you installed anything with Synaptic you should be able to view the history in Synaptic under File/History.

---

### Post by conmat on 2010-01-10
Thanks for this info.

UPDATE:  System still crashes when the wireless card hardware switch is off.

I have read many web posts that indicate this problem may be caused by wireless drivers.  Is it safe to assume that if my system still crashes when the wireless switch is off that this is not a wireless driver problem?

When the system crashes the screen goes black and returns me to the user login screen.  It is not like a full restart which would return me to the encryption passphrase screen.

---

### Post by 73ckn797 on 2010-01-10
As you may eliminate certain running processes or programs and the system still experiences the problem, it would generally be that those items are not causing the problem.

You may want to go to System/Preferences/Startup Applications. In there you can turn off things that are started when you boot into Ubuntu. That could be a way to individually eliminate things that could be causing a problem.

You could search for other posts that may address you similar problem. I recommend using [http://www.uboontu.com](http://www.uboontu.com). The forum search feature can be difficult to single out specifics.

There are also other ways to produce a list of system logs that may show where the problem is. I do not have that info at hand right now.

---

### Post by 73ckn797 on 2010-01-10
> **conmat said:**
> Thanks for this info.

UPDATE:  System still crashes when the wireless card hardware switch is off.

I have read many web posts that indicate this problem may be caused by wireless drivers.  Is it safe to assume that if my system still crashes when the wireless switch is off that this is not a wireless driver problem?

When the system crashes the screen goes black and returns me to the user login screen.  It is not like a full restart which would return me to the encryption passphrase screen.


If you feel the wireless driver is causing the problem you could try installing the WIndows driver using "ndisgtk" found in Synaptic.

---

### Post by tedrogers on 2010-02-09
Hi there....this seems familiar!

I'm having weird crashing issues on my T500 and I'm certain that it's something to do with WPA Supplicant or something else wireless related.

My system crashes when I'm using Deluge or Transmission, and for no apparent reason (i.e. not input related, no other big programmes running except things like Ubuntu One etc).

I looked at my syslog and saw similar entries to you, i.e. CTRL-EVENT-SCAN-RESULTS...and then long gaps in time between the system hang and me restarting to laptop.

See my posts at these places:

[http://ubuntuforums.org/showthread.php?t=1395630](http://ubuntuforums.org/showthread.php?t=1395630)

[http://ubuntuforums.org/showthread.php?t=1388688](http://ubuntuforums.org/showthread.php?t=1388688)

...so for though I am not getting any joy.

Oh and I'm using 32-bit 9.10, rather than 64-bit, but I don't see why this would make our symptoms any different. They both seem wireless related. :(

Maybe we can help each other out.

---

### Post by conmat on 2010-02-19
> **tedrogers said:**
> Hi there....this seems familiar!

I'm having weird crashing issues on my T500 and I'm certain that it's something to do with WPA Supplicant or something else wireless related.

My system crashes when I'm using Deluge or Transmission, and for no apparent reason (i.e. not input related, no other big programmes running except things like Ubuntu One etc).

I looked at my syslog and saw similar entries to you, i.e. CTRL-EVENT-SCAN-RESULTS...and then long gaps in time between the system hang and me restarting to laptop.

See my posts at these places:

[http://ubuntuforums.org/showthread.php?t=1395630](http://ubuntuforums.org/showthread.php?t=1395630)

[http://ubuntuforums.org/showthread.php?t=1388688](http://ubuntuforums.org/showthread.php?t=1388688)

...so for though I am not getting any joy.

Oh and I'm using 32-bit 9.10, rather than 64-bit, but I don't see why this would make our symptoms any different. They both seem wireless related. :(

Maybe we can help each other out.


I wish I could help you but I can't even get my system to run for 30 minutes without crashing!!!!!!!!

I think Karmic 64-bit is strictly alpha release status.  This is the worst POS  OS   I have ever had the misfortune to try!  I am so pissed-off right now I am actually thinking of going back to windows.

As far as "community support"  BS!!!!!!!!!

I have never received any solution to a serious problem!!!  I really hope Lucid is a real OS!

---

### Post by 73ckn797 on 2010-02-19
> **conmat said:**
> I wish I could help you but I can't even get my system to run for 30 minutes without crashing!!!!!!!!

I think Karmic 64-bit is strictly alpha release status.  This is the worst POS  OS   I have ever had the misfortune to try!  I am so pissed-off right now I am actually thinking of going back to windows.

As far as "community support"  BS!!!!!!!!!

I have never received any solution to a serious problem!!!  I really hope Lucid is a real OS!

You never indicated whether there was wireless driver problem found. 

As for support, your misfortune is a result of your choice and not the OS. More info will help in finding a solution. You have only sought out 2 problems that I can find that you have started any threads on and you have not replied back on this one with results of the suggestions that have been made.

---

### Post by conmat on 2010-03-06
> **73ckn797 said:**
> You never indicated whether there was wireless driver problem found. 

As for support, your misfortune is a result of your choice and not the OS. More info will help in finding a solution. You have only sought out 2 problems that I can find that you have started any threads on and you have not replied back on this one with results of the suggestions that have been made.

Please see:
[http://ubuntuforums.org/showpost.php?p=8641646&postcount=3](http://ubuntuforums.org/showpost.php?p=8641646&postcount=3)

I feel (very) safe in assuming that if my network card is turned off in hardware the problem is not a wireless driver.

The suggestions posted specifically refer to Transmission.  I have crashes when Transmission is not running so why should I try those solutions?

Also, the solutions to the problems with Transmission involve installing backports!!!  This is not something that should be necessary with a properly functioning OS!

The only information I have not provided is that I ran memtest86+ (v2.11 because I couldn't get any later version to $#@$&*!  compile!) for 12 hours with no errors for 8GB of RAM.

The fact remains I have never received a solution to any problem I have posted.  The fact I have only posted a few problems  means: 1.  I know how to use Google and solve as many problems as possible by myself (I would like to thank everyone who has posted useful solutions), 2. the Ubuntu forums have not helped me solve the few problems I can not solve by myself.

I wil continue to use the Ubuntu forums because:  1: it is the only game in town, 2. it's free, 3. I might get lucky.

Have a nice day.

---

### Post by 73ckn797 on 2010-03-06
> **conmat said:**
> This is not something that should be necessary with a properly functioning OS!
In the Ubuntu world back ports are sometimes where solutions are remedied. That is just the nature of the beast. If a back port fixes an issue then it becomes a properly functioning OS.

---

### Post by tedrogers on 2010-03-08
Agreed!

Installing backports makes my computer work with my favourite open-source OS. :)

---

### Post by regiss on 2010-03-14
> **tedrogers said:**
> Agreed!

Installing backports makes my computer work with my favourite open-source OS. :)


Hi mate, 
could you tell me how did you install backports. I have a same problem as you had ;)

---

### Post by 73ckn797 on 2010-03-14
> **regiss said:**
> Hi mate, 
could you tell me how did you install backports. I have a same problem as you had ;)
They can be found in Synaptic Package Manager under "linux-backports-modules".

---

### Post by tedrogers on 2010-03-15
Yes, just use synaptic and install everything under that entry.

Should sort it out for you :)

Mines been running solidly now for months! ;)

---

### Post by regiss on 2010-03-16
> **tedrogers said:**
> Yes, just use synaptic and install everything under that entry.

Should sort it out for you :)

Mines been running solidly now for months! ;)

Hi there,
thank you for replay.

What I did:
uname -a 
Linux laptop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux

And in synaptic I've selected linux-backports-modules for this kernel 2.6.31-20

Is that right? Could you explain me a bit more what does the  linux-backports-modules do?

This crashes drives me nuts. Hopefully this will fix my problem.

Cheers regiss

---

### Post by 73ckn797 on 2010-03-17
> **regiss said:**
> Could you explain me a bit more what does the  linux-backports-modules do?

There are descriptions with each module in Synaptic. You may find a link in the lower panel.

---

### Post by regiss on 2010-03-18
System still keeps crashing. Only think I can see in syslog is 
wpa_supplicant[1397]: CTRL-EVENT-SCAN-RESULTS 

I've install backports, but now effect. Do you have any idea where could be the problem?

**Edit**: I haven't seen crash since I switched to Internal Graphic Card. Hope this helps.

Cheers regiss

---

### Post by regiss on 2010-07-08
Hi guys,

still no luck with ATI drivers. It's randomly crushing when ATI is in use. Could you post whole setup how to install drivers without no crushing.

It would be great to use ATI and not whole time Integrated graphic card.

Cheers

---

### Post by conmat on 2010-07-17
I now believe this is a hardware problem and not a problem with Ubuntu.

My T400 will also crash when running Puppy Linux live CD.

The only time the system does not crash is when I am running on AC power with the battery removed.

Sometimes the syslog shows the system reached critical temperature (127 C) and shut down but not every time.  I run GNOME Sensors Applet 2.2.3 and I have never seen the temperature go above ~80 C.  Sometimes the temperature will jump by ~15 C (up or down) which I do not understand.   It does not make sense to me for the temperature to make such a big jump.  I wonder if there is a sensor or heatsink problem.

Also I can restart the system immediately and the temperature is about 40 C.  It is possible for the temperture to drop from 127 C to 40 C in two minutes (with the fan off while rebooting)?

Someone said it may be a battery problem but this happens with two Denaq six-cell batteries.  Denaq is supposed to be very high quality.  LSHW says the batteries (internal cells) are Sanyo.

I have read a few posts that say this can be caused by a clogged or dirty heatsink but this started happening just four weeks after I bought the system.  I can see the heatsink fins and they look completely clean.

Are there any other Lenovo T400 users who have seen this problem?

Any suggestions appreciated.

---

### Post by conmat on 2010-09-13
Just received my T400 back from Lenovo depot service .  The service form said they replaced the fan.  The system still shuts down when the battery is installed and the AC power is connected.

One problem is Lenovo insists that the system can only have original components installed when the system is returned for service.  My original battery is a Lenovo 4-cell battery but I usually use a 6-cell Denaq battery.  I thought Denaq were supposed to be high quality batteries.

I called Lenovo service again and the only suggestion they had was to try to run the system on the 4-cell battery and see if it still shuts down.

Has anyone tried to check the attachment of the heatsink?  I'm wondering if installing a better heatsink compound might help?

Thanks

---

### Post by tedrogers on 2010-09-15
> **conmat said:**
> Just received my T400 back from Lenovo depot service .  The service form said they replaced the fan.  The system still shuts down when the battery is installed and the AC power is connected.

One problem is Lenovo insists that the system can only have original components installed when the system is returned for service.  My original battery is a Lenovo 4-cell battery but I usually use a 6-cell Denaq battery.  I thought Denaq were supposed to be high quality batteries.

I called Lenovo service again and the only suggestion they had was to try to run the system on the 4-cell battery and see if it still shuts down.

Has anyone tried to check the attachment of the heatsink?  I'm wondering if installing a better heatsink compound might help?

Thanks

This would be better off in a different thread, as it is now a different issues...i.e. a hardware fault / servicing enquiry.

---

