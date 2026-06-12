---
title: "hostapd randomly dropping one client"
date: 2011-06-23
forum: General Help
---

### Post by ant2ne on 2011-06-23
Using hostapd 0.7.3

Here is a piece of my daemon.log
```
ant2ne@vmhost:/var/log$ cat daemon.log | grep hostapd
Jun 19 09:05:37 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 19 09:05:37 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 19 09:05:37 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-00000007
Jun 19 09:57:50 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 19 09:57:50 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 19 09:57:50 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-00000008
Jun 19 10:15:14 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 19 10:15:14 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 19 10:15:14 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-00000009
Jun 19 13:05:54 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 19 13:05:54 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: associated (aid 1)
Jun 19 13:05:54 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 RADIUS: starting accounting session 4DFBD09F-0000000A
Jun 19 13:29:58 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: disassociated due to inactivity
Jun 19 13:29:59 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: deauthenticated due to inactivity
Jun 19 14:35:14 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 19 14:35:14 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 19 14:35:14 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-0000000B
Jun 19 18:49:34 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 19 18:49:34 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: associated (aid 1)
Jun 19 18:49:34 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 RADIUS: starting accounting session 4DFBD09F-0000000C
Jun 19 20:09:46 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 19 20:09:46 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 2)
Jun 19 20:09:46 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-0000000D
Jun 19 21:09:24 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: disassociated due to inactivity
Jun 19 21:09:25 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: deauthenticated due to inactivity
Jun 19 22:03:24 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 19 22:03:24 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 19 22:03:24 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-0000000E
Jun 20 06:55:38 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 20 06:55:38 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 20 06:55:38 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 20 06:55:38 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-0000000F
Jun 20 08:44:23 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 20 08:44:23 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: associated (aid 1)
Jun 20 08:44:23 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 RADIUS: starting accounting session 4DFBD09F-00000010
Jun 20 09:47:46 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: disassociated due to inactivity
Jun 20 09:47:47 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: deauthenticated due to inactivity
Jun 20 20:26:46 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 20 20:26:46 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 20 20:26:46 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-00000011
Jun 20 21:16:33 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 20 21:16:33 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 20 21:16:33 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-00000012
Jun 20 23:15:51 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 20 23:15:51 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 20 23:15:51 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-00000013
Jun 21 06:57:41 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 21 06:57:41 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 21 06:57:41 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-00000014
Jun 21 12:48:08 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 21 12:48:08 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: associated (aid 1)
Jun 21 12:48:08 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 RADIUS: starting accounting session 4DFBD09F-00000015
Jun 21 13:29:03 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: disassociated due to inactivity
Jun 21 13:29:04 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: deauthenticated due to inactivity
Jun 21 16:36:27 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: did not acknowledge authentication response
Jun 21 16:36:43 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 21 16:36:43 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: associated (aid 1)
Jun 21 16:36:43 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 RADIUS: starting accounting session 4DFBD09F-00000016
Jun 21 16:51:30 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: disassociated due to inactivity
Jun 21 16:51:31 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: deauthenticated due to inactivity
Jun 21 16:59:59 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 21 16:59:59 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 21 16:59:59 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-00000017
Jun 21 17:38:06 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: disassociated due to inactivity
Jun 21 17:38:07 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: deauthenticated due to inactivity
Jun 21 17:45:38 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 21 17:45:38 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: associated (aid 1)
Jun 21 17:45:38 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 RADIUS: starting accounting session 4DFBD09F-00000018
Jun 21 17:52:08 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 21 17:52:08 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 2)
Jun 21 17:52:08 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-00000019
Jun 21 17:56:46 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: disassociated due to inactivity
Jun 21 17:56:47 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: deauthenticated due to inactivity
Jun 21 18:15:19 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 21 18:15:19 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 21 18:15:19 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-0000001A
Jun 21 19:13:07 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 21 19:13:07 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 21 19:13:07 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-0000001B
Jun 21 19:32:44 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 21 19:32:44 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 21 19:32:44 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-0000001C
Jun 21 20:30:07 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 21 20:30:07 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 21 20:30:07 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-0000001D
Jun 21 20:41:07 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 21 20:41:07 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 21 20:41:07 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-0000001E
Jun 21 21:24:53 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 21 21:24:53 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: associated (aid 1)
Jun 21 21:24:53 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 RADIUS: starting accounting session 4DFBD09F-0000001F
Jun 21 22:38:49 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: disassociated due to inactivity
Jun 21 22:38:50 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: deauthenticated due to inactivity
Jun 22 07:14:33 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 22 07:14:33 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 22 07:14:33 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-00000020
Jun 22 07:28:55 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: disassociated due to inactivity
Jun 22 07:28:56 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: deauthenticated due to inactivity
Jun 22 08:32:45 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 22 08:32:45 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: associated (aid 1)
Jun 22 08:32:45 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 RADIUS: starting accounting session 4DFBD09F-00000021
Jun 22 08:44:27 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 22 08:44:27 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 22 08:44:27 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 22 08:44:27 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: associated (aid 1)
Jun 22 08:44:27 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 RADIUS: starting accounting session 4DFBD09F-00000022
Jun 22 08:44:27 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: associated (aid 1)
Jun 22 08:44:27 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 RADIUS: starting accounting session 4DFBD09F-00000023
Jun 22 08:53:00 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: disassociated due to inactivity
Jun 22 08:53:01 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: deauthenticated due to inactivity
Jun 22 18:29:27 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 22 18:29:27 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: associated (aid 1)
Jun 22 18:29:27 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 RADIUS: starting accounting session 4DFBD09F-00000024
Jun 22 18:32:49 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 22 18:32:49 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 2)
Jun 22 18:32:49 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-00000025
Jun 22 18:39:42 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: disassociated due to inactivity
Jun 22 18:39:43 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: deauthenticated due to inactivity
Jun 22 19:00:45 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: did not acknowledge authentication response
Jun 22 19:00:46 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: associated (aid 1)
Jun 22 19:00:46 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 RADIUS: starting accounting session 4DFBD09F-00000026
Jun 22 19:00:46 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: associated (aid 1)
Jun 22 19:00:46 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 RADIUS: starting accounting session 4DFBD09F-00000027
Jun 22 19:06:54 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: disassociated due to inactivity
Jun 22 19:06:55 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: deauthenticated due to inactivity
Jun 23 00:17:18 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 23 00:17:18 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: associated (aid 1)
Jun 23 00:17:18 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 RADIUS: starting accounting session 4DFBD09F-00000028
Jun 23 01:08:00 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: disassociated due to inactivity
Jun 23 01:08:01 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: deauthenticated due to inactivity
Jun 23 01:30:04 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 23 01:30:20 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: did not acknowledge authentication response
Jun 23 01:30:43 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: did not acknowledge authentication response
Jun 23 01:30:43 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 23 01:30:53 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: did not acknowledge authentication response
Jun 23 01:30:57 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 23 01:30:57 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: associated (aid 1)
Jun 23 01:30:57 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 RADIUS: starting accounting session 4DFBD09F-00000029
Jun 23 01:42:27 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: disassociated due to inactivity
Jun 23 01:42:28 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: deauthenticated due to inactivity
Jun 23 07:14:40 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 23 07:14:40 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 23 07:14:40 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-0000002A
Jun 23 07:37:37 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 23 07:37:37 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 23 07:37:37 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-0000002B
Jun 23 07:37:37 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 23 07:37:37 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4DFBD09F-0000002C
Jun 23 08:11:28 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 23 08:11:28 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: authenticated
Jun 23 08:11:28 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: associated (aid 1)
Jun 23 08:11:28 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 RADIUS: starting accounting session 4DFBD09F-0000002D
Jun 23 08:33:30 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: did not acknowledge authentication response
Jun 23 08:38:31 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: disassociated due to inactivity
Jun 23 08:38:32 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: deauthenticated due to inactivity
Jun 23 12:09:57 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: authenticated
Jun 23 12:09:57 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 IEEE 802.11: associated (aid 1)
Jun 23 12:09:57 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 RADIUS: starting accounting session 4E0367ED-00000000
Jun 23 12:09:57 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 WPA: pairwise key handshake completed (RSN)
Jun 23 12:11:01 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 WPA: group key handshake completed (RSN)
Jun 23 12:21:01 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 WPA: group key handshake completed (RSN)
Jun 23 12:31:01 vmhost hostapd: wlan1: STA 00:22:fa:49:01:52 WPA: group key handshake completed (RSN)
```
You might notice that there are 2 devices connecting to that AP. one has a MAC that ends in 52 and on has a MAC that ends in 45. The 52 is a linux/mint laptop. The 45 is a Windows7 laptop.

The 45 device is the one that is getting random drops. As you can see below. 
```

ant2ne@vmhost:/var/log$ cat daemon.log | grep hostapd | grep acknowledge
Jun 21 16:36:27 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: did not acknowledge authentication response
Jun 22 19:00:45 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: did not acknowledge authentication response
Jun 23 01:30:20 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: did not acknowledge authentication response
Jun 23 01:30:43 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: did not acknowledge authentication response
Jun 23 01:30:53 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: did not acknowledge authentication response
Jun 23 08:33:30 vmhost hostapd: wlan1: STA 20:7c:8f:03:66:45 IEEE 802.11: did not acknowledge authentication response
ant2ne@vmhost:/var/log$

```

This person claims that they get stable connections on other WAPs. 

Here is my hostapd.conf file
```
interface=wlan1
driver=nl80211
ssid=Disabled
channel=5


logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2
debug=0
dump_file=/tmp/hostapd.dump
```
Unfortunately converting the Windows7 box to linux is not an acceptable solution.

---

