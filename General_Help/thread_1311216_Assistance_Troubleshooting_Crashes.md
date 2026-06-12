---
title: "Assistance Troubleshooting Crashes"
date: 2009-11-02
forum: General Help
---

### Post by jpshortstuff on 2009-11-02
Hi all,

Since installing 9.04 on my Desktop a few weeks back, I've been getting unexpected crashes/freezing/hanging at completely random points during a session. I am still getting this since upgrading to 9.10. I used to have 8.something on this Desktop and never had this issue with that, so don't *think* its a hardware issue.

There doesn't seem to be any correlation between what I'm doing and when it happens, sometimes happens when I'm not doing anything, or just logged in. Sometimes the screen messes up for a little before it crashes completely.

To get out of it, I've been using SysReq+REISUB.

I'm new to troubleshooting this sort of thing, so bear with me if I haven't provided enough info. I've had a little look through my /var/log/messages* files, but I'm not getting much idea of what the problem is. There does seem to be some common lines around the time I can see the SysReq:SAK that I fire, but again, not entirely sure what I'm looking at/for.

> Nov  2 15:15:22 PaniniPC kernel: [  211.792017] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 119
Nov  2 15:16:42 PaniniPC kernel: [  291.788530] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 119
Nov  2 15:16:46 PaniniPC kernel: [  296.142042] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Nov  2 15:16:51 PaniniPC kernel: [  301.247020] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 119
Nov  2 15:18:22 PaniniPC kernel: [  391.792511] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 119
Nov  2 15:18:28 PaniniPC kernel: [  398.135973] SysRq : SAK

> Oct 28 06:54:59 PaniniPC kernel: [   65.317471] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
Oct 28 06:55:09 PaniniPC kernel: [   75.069809] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 119
Oct 28 06:55:44 PaniniPC kernel: [  110.487571] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 28 06:55:49 PaniniPC kernel: [  115.036908] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 119
Oct 28 06:56:49 PaniniPC kernel: [  175.044399] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 119
Oct 28 06:57:33 PaniniPC kernel: [  219.489201] SysRq : SAK

> Oct 26 09:09:46 PaniniPC kernel: [ 1955.259431] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
Oct 26 09:11:00 PaniniPC kernel: [ 2028.536425] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 119
Oct 26 09:13:00 PaniniPC kernel: [ 2148.535962] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 119
Oct 26 09:15:00 PaniniPC kernel: [ 2268.536077] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 119
Oct 26 09:17:00 PaniniPC kernel: [ 2388.535772] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 119
Oct 26 09:19:00 PaniniPC kernel: [ 2508.536408] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 119
Oct 26 09:21:00 PaniniPC kernel: [ 2628.536183] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 119
Oct 26 09:23:00 PaniniPC kernel: [ 2748.536727] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 119
Oct 26 09:25:00 PaniniPC kernel: [ 2868.536790] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 119
Oct 26 09:27:00 PaniniPC kernel: [ 2988.536235] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 119
Oct 26 09:28:45 PaniniPC kernel: [ 3094.349529] SysRq : SAK

As I say, apologies if I haven't provided the right info, but any help with this would be greatly appreciated.

Thanks.

---

