---
title: "Sudden wifi connectivity problem"
date: 2009-11-11
forum: General Help
---

### Post by joshua neff on 2009-11-11
I have a Dell Inspiron 1420.

I upgraded to Karmic last week & besides my sound going away, I've had no problems. But last night, my wifi suddenly started to drop off. It shows I'm picking up the wifi signal fine, but after 1-5 minutes of logging in, all internet connection stops. If I restart the computer, it connects fine, but suddenly stops again 1-5 minutes later. Connecting to the router with an ethernet cable works fine, and I've check the wifi signal & it's fine, so it must be my laptop. I have no idea why this would suddenly start happening. The last change I made to the computer was installing alsamixer yesterday afternoon. Otherwise, there's been no change, so I can't imagine why I'm suddenly losing wifi connectivity.

Any help?

---

### Post by fargle on 2009-11-11
When it drops off, open a command prompt and run "tail -f /var/log/syslog", which is where Network Manager logs things - if something looks interesting, attach it here.

---

### Post by joshua neff on 2009-11-11
OK, I ran that as you suggested right after I lost connectivity this most recent time. Here's what came up:

> Nov 11 15:56:54 dell-desktop kernel: [ 2554.530281] Registered led device: iwl-phy0::TX

Nov 11 15:56:57 dell-desktop wpa_supplicant[1423]: Failed to initiate AP scan.

Nov 11 15:57:07 dell-desktop wpa_supplicant[1423]: Failed to initiate AP scan.

Nov 11 15:57:08 dell-desktop kernel: [ 2567.799615] iwl3945 0000:0c:00.0: Microcode SW error detected. Restarting 0x82000008.

Nov 11 15:57:08 dell-desktop kernel: [ 2567.799634] iwl3945 0000:0c:00.0: Error Reply type 0x00000000 cmd REPLY_TX (0x1C) seq 0x0000 ser 0x00000000

Nov 11 15:57:08 dell-desktop kernel: [ 2567.877728] Registered led device: iwl-phy0::radio

Nov 11 15:57:08 dell-desktop kernel: [ 2567.877768] Registered led device: iwl-phy0::assoc

Nov 11 15:57:08 dell-desktop kernel: [ 2567.877802] Registered led device: iwl-phy0::RX

Nov 11 15:57:08 dell-desktop kernel: [ 2567.877833] Registered led device: iwl-phy0::TX

Nov 11 15:57:17 dell-desktop wpa_supplicant[1423]: Failed to initiate AP scan.

Nov 11 15:57:27 dell-desktop wpa_supplicant[1423]: Failed to initiate AP scan.

Nov 11 15:57:34 dell-desktop kernel: [ 2594.036758] iwl3945 0000:0c:00.0: Microcode SW error detected. Restarting 0x82000008.

Nov 11 15:57:34 dell-desktop kernel: [ 2594.036780] iwl3945 0000:0c:00.0: Error Reply type 0x00000000 cmd REPLY_TX (0x1C) seq 0x0000 ser 0x00000000

Nov 11 15:57:34 dell-desktop kernel: [ 2594.111068] Registered led device: iwl-phy0::radio

Nov 11 15:57:34 dell-desktop kernel: [ 2594.111147] Registered led device: iwl-phy0::assoc

Nov 11 15:57:34 dell-desktop kernel: [ 2594.111181] Registered led device: iwl-phy0::RX

Nov 11 15:57:34 dell-desktop kernel: [ 2594.111214] Registered led device: iwl-phy0::TX

Nov 11 15:57:37 dell-desktop wpa_supplicant[1423]: Failed to initiate AP scan.

Nov 11 15:57:47 dell-desktop wpa_supplicant[1423]: Failed to initiate AP scan.

Nov 11 15:57:48 dell-desktop kernel: [ 2608.385075] iwl3945 0000:0c:00.0: Microcode SW error detected. Restarting 0x82000008.

Nov 11 15:57:48 dell-desktop kernel: [ 2608.385094] iwl3945 0000:0c:00.0: Error Reply type 0x00000000 cmd REPLY_TX (0x1C) seq 0x0000 ser 0x00000000

Nov 11 15:57:48 dell-desktop kernel: [ 2608.465269] Registered led device: iwl-phy0::radio

Nov 11 15:57:48 dell-desktop kernel: [ 2608.465350] Registered led device: iwl-phy0::assoc

Nov 11 15:57:48 dell-desktop kernel: [ 2608.465385] Registered led device: iwl-phy0::RX

Nov 11 15:57:48 dell-desktop kernel: [ 2608.465416] Registered led device: iwl-phy0::TX

Nov 11 15:57:57 dell-desktop wpa_supplicant[1423]: Failed to initiate AP scan.

Nov 11 15:58:07 dell-desktop wpa_supplicant[1423]: Failed to initiate AP scan.

Nov 11 15:58:12 dell-desktop kernel: [ 2632.023012] iwl3945 0000:0c:00.0: Microcode SW error detected. Restarting 0x82000008.

Nov 11 15:58:12 dell-desktop kernel: [ 2632.023029] iwl3945 0000:0c:00.0: Error Reply type 0x00000000 cmd REPLY_TX (0x1C) seq 0x0000 ser 0x00000000

Nov 11 15:58:12 dell-desktop kernel: [ 2632.092949] Registered led device: iwl-phy0::radio

Nov 11 15:58:12 dell-desktop kernel: [ 2632.092990] Registered led device: iwl-phy0::assoc

Nov 11 15:58:12 dell-desktop kernel: [ 2632.093068] Registered led device: iwl-phy0::RX

Nov 11 15:58:12 dell-desktop kernel: [ 2632.093102] Registered led device: iwl-phy0::TX

Nov 11 15:58:17 dell-desktop wpa_supplicant[1423]: Failed to initiate AP scan.

Nov 11 15:58:27 dell-desktop wpa_supplicant[1423]: Failed to initiate AP scan.

Nov 11 15:58:30 dell-desktop kernel: [ 2650.464338] iwl3945 0000:0c:00.0: Microcode SW error detected. Restarting 0x82000008.

Nov 11 15:58:30 dell-desktop kernel: [ 2650.464357] iwl3945 0000:0c:00.0: Error Reply type 0x00000000 cmd REPLY_TX (0x1C) seq 0x0000 ser 0x00000000

Nov 11 15:58:30 dell-desktop kernel: [ 2650.537299] Registered led device: iwl-phy0::radio

Nov 11 15:58:30 dell-desktop kernel: [ 2650.537325] Registered led device: iwl-phy0::assoc

Nov 11 15:58:30 dell-desktop kernel: [ 2650.537345] Registered led device: iwl-phy0::RX

Nov 11 15:58:30 dell-desktop kernel: [ 2650.537366] Registered led device: iwl-phy0::TX

I don't know what this shows, though.

---

### Post by fargle on 2009-11-11
Wow, this is a nasty one - I found a Launchpad bug reported, and the latest fix seems to be to reconfigure your wireless router (link to Launchpad bug report [[COLOR="Blue"]here[/COLOR]]("https://bugs.launchpad.net/linux/+bug/185470?comments=all")):

```


I had never had this problem, but I recently bought a new wireless router which offers different security settings, and bumped into the "Microcode SW error" problem -- this consists in a lost connection after a few minutes (if that) of activity, which can be regained by simply asking for a reconnection in nm-applet.

In the router, if I set (according to Belkin):

 Security: WPA/WPA2-Personal(PSK)
 Authentication: WPA2-PSK
 Encryption: AES

I get the problem, whereas if I switch to:

 Security: WPA/WPA2-Personal(PSK)
 Authentication: WPA-PSK + WPA2-PSK
 Encryption: TKIP + AES

where the third option is forced by the second, the connection works fine. Hopefully this is useful info...

```

So I'm thinking this has to do with using AES encryption on some versions of the 3945ABG?  I know I don't have this problem with mine, but I bet I have WPA/TKIP enabled at home, and I know our corporate wireless still supports TKIP encryption as well, in corporate mode with client certificates.

So, in short, it appears to be a problem with WPA2/AES being required on your wireless router, but it appears also that the bug has been fixed with new microcode available [[COLOR="Blue"]here[/COLOR]]("http://www.intellinuxwireless.org/?n=Downloads").  I don't have my laptop with me which has an iwl3945 in it, sadly, but if you can find the location of the microcode (/usr/lib somewhere, I think) and save the current and replace it with this downloaded code, that might fix the problem as well without reconfiguring the router.

That's definitely a highly technical solution, though, so let me know if you can't get resolution and I'll try the new microcode on mine to make sure it doesn't break things and write up a better solution with what files to replace and how.

---

### Post by joshua neff on 2009-11-11
Weird that it's suddenly happening. I'll fiddle around & see if I can get it fixed. Thanks for your help!

---

### Post by fargle on 2009-11-12
No problem, hope I did help!  FYI I checked my home router (Asus WL-500GP) and it has WPA-PSK/WPA2-PSK set, but with AES encryption, and my 3945ABG in this laptop has always been rock solid with a default install and continues that way on Karmic.  YMMV.

---

### Post by zuke on 2009-11-12
I'm having a similar problem, 

I noticed this line in dmesg output 

"WARNING: at /build/buildd/linux-backports-modules-2.6.31-2.6.31/debian/build/build-generic/compat-wireless-2.6/net/wireless/core.c:614 wdev_cleanup_work+0x9f/0xc0 [cfg80211]()"

---

