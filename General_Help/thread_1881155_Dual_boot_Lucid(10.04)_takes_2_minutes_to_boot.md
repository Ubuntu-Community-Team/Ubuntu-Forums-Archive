---
title: "Dual boot Lucid(10.04) takes 2 minutes to boot"
date: 2011-11-15
forum: General Help
---

### Post by rockymaxsource on 2011-11-15
Hey,

I used to have Ubuntu 11.04 installed on my ThinkPad SL510 laptop with Windows XP. After I upgraded the Ubuntu to 11.10. It takes me 30 minutes to boot after select Ubuntu from boot menu. After that I reinstalled Ubuntu 10.04. But it still takes about 2 minutes to book after select Ubuntu from boot menu. Windows XP could boot within 30 seconds. Can anyone tell me how could I trouble shoot this please?

---

### Post by BillyBoa on 2011-11-15
11.10 is heavier than it's predecessors. WinXP is a small OS of the 2001. You cannot compare them.

In your case I feel there is an Ubuntu problem with your hardware, means Ubuntu doesn't collaborate well with one aspect of your computer, usually the video card.

Try to see if there is a difference installing the proprietary drivers for your video card.

If you failed with Ubuntu try other OS like PuppyLinux which is a very light version of Ubuntu.

---

### Post by soryu on 2011-11-15
this was happening to me but after a couple of boots it fixed itself.
now it's like 45 sec.

shutdown was also taking forever around 3min 
now 30sec.

---

### Post by rockymaxsource on 2011-11-16
System->Administration->HardwareDivers tells me no proprietary drivers are in use with the system.

I installed the bootChart. The book time is around 4 minutes now. It shuts down quite quick within about 30 seconds. Please [see the bootChart image at here]("http://o-r-q.info/images/rocky-laptop-lucid-20111117-1.png"). Can any one helps to troubleshoot this please?

---

### Post by rockymaxsource on 2011-12-09
Hey,

I have been trying to solve this problem. But without luck](*,) The bootchart image is [http://o-r-q.info/images/rocky-laptop-lucid-20111210-1.png](http://o-r-q.info/images/rocky-laptop-lucid-20111210-1.png). I interpret it as most of 7 minutes are spending on I/O waiting. Could anyone help me out please?

---

### Post by rockymaxsource on 2011-12-09
Hey,

/var/log/messages lines with the big gime gap are below:
```

Dec 10 10:58:15 rocky-laptop kernel: [  248.777768] rtl819xSE 0000:05:00.0      : firmware: requesting RTL8192SE/rtl8192sfw.bin
10502 Dec 10 10:58:17 rocky-laptop kernel: [  250.722053] rtl8192_SetWirelessMod      e(), wireless_mode:10, bEnableHT = 1
10503 Dec 10 10:58:17 rocky-laptop kernel: [  250.731699] ===>rtllib_start_scan(      )
10504 Dec 10 10:58:17 rocky-laptop kernel: [  250.732349] ADDRCONF(NETDEV_UP): w      lan0: link is not ready
10505 Dec 10 10:58:17 rocky-laptop kernel: [  250.735090] r8169: eth0: link down
10506 Dec 10 10:58:17 rocky-laptop kernel: [  250.735240] ADDRCONF(NETDEV_UP): e      th0: link is not ready
10507 Dec 10 10:58:34 rocky-laptop kernel: [  267.534605] rtl8192_SetWirelessMod      e(), wireless_mode:10, bEnableHT = 1
10508 Dec 10 10:58:36 rocky-laptop kernel: [  269.078598] rtl8192_SetWirelessMod      e(), wireless_mode:10, bEnableHT = 1
Dec 10 10:58:44 rocky-laptop kernel: [  277.132499] rtl8192_SetWirelessMod      e(), wireless_mode:10, bEnableHT = 1
10510 Dec 10 10:58:52 rocky-laptop kernel: [  285.964225] __ratelimit: 6 callbac      ks suppressed
10511 Dec 10 10:58:52 rocky-laptop kernel: [  285.964228] type=1505 audit(132348      5932.983:17):  operation="profile_replace" pid=1074 name="/usr/sbin/mysqld      "
10512 Dec 10 10:58:59 rocky-laptop kernel: [  292.004476] MgntActSet_RF_State():       RF Change in progress! Wait to set..StateToSet(0).
10513 Dec 10 10:58:59 rocky-laptop kernel: [  292.123194] rtl8192_SetWirelessMod      e(), wireless_mode:10, bEnableHT = 1
10514 Dec 10 10:59:30 rocky-laptop kernel: [  323.120610] rtl8192_SetWirelessMod      e(), wireless_mode:10, bEnableHT = 1
10515 Dec 10 10:59:50 rocky-laptop kernel: [  343.587618] ppdev: user-space para      llel port driver
10516 Dec 10 11:00:11 rocky-laptop kernel: [  364.002925] MgntActSet_RF_State():       RF Change in progress! Wait to set..StateToSet(0).
Dec 10 11:00:11 rocky-laptop kernel: [  364.123606] rtl8192_SetWirelessMod      e(), wireless_mode:10, bEnableHT = 1
10518 Dec 10 11:00:19 rocky-laptop backintime (rocky): INFO: Lock
10519 Dec 10 11:00:19 rocky-laptop backintime (rocky): INFO: Include folders: ['      /home/rocky', '/etc/apache2/sites-available', '/etc/bind']
10520 Dec 10 11:00:19 rocky-laptop backintime (rocky): INFO: Ignore folders: []
10521 Dec 10 11:00:19 rocky-laptop backintime (rocky): INFO: Last snapshots: {}
10522 Dec 10 11:00:19 rocky-laptop backintime (rocky): WARNING: Can't find snaps      hots folder !
10523 Dec 10 11:00:21 rocky-laptop backintime (rocky): INFO: Unlock
10524 Dec 10 11:01:02 rocky-laptop kernel: [  415.117957] rtl8192_SetWirelessMod      e(), wireless_mode:10, bEnableHT = 1
10525 Dec 10 11:02:03 rocky-laptop kernel: [  476.003205] MgntActSet_RF_State():       RF Change in progress! Wait to set..StateToSet(0).
10526 Dec 10 11:02:03 rocky-laptop kernel: [  476.122900] rtl8192_SetWirelessMod      e(), wireless_mode:10, bEnableHT = 1
10527 Dec 10 11:02:55 rocky-laptop kernel: [  528.388221] rtl8192_SetWirelessMod      e(), wireless_mode:10, bEnableHT = 1
10546 Dec 10 11:03:48 rocky-laptop kernel: [  581.997055] rtl8192_hw_sleep_down(      ): RF Change in progress!
10547 Dec 10 11:04:04 rocky-laptop kernel: [  598.005967] LPS leave: notify AP w      e are awaked ++++++++++ SendNullFunctionData
10548 Dec 10 11:04:04 rocky-laptop kernel: [  598.006043] ===>rtl8192se_link_cha      nge():ieee->iw_mode is 2
10549 Dec 10 11:04:05 rocky-laptop kernel: [  599.527026] ===>rtl8192se_link_cha      nge():ieee->iw_mode is 2
10550 Dec 10 11:04:45 rocky-laptop kernel: [  639.001683] LPS leave: notify AP w      e are awaked ++++++++++ SendNullFunctionData
10551 Dec 10 11:04:45 rocky-laptop kernel: [  639.001769] ===>rtl8192se_link_cha      nge():ieee->iw_mode is 2
10552 Dec 10 11:04:46 rocky-laptop kernel: [  640.523023] ===>rtl8192se_link_cha      nge():ieee->iw_mode is 2
10553 Dec 10 11:05:46 rocky-laptop kernel: [  700.003643] LPS leave: notify AP w      e are awaked ++++++++++ SendNullFunctionData
10554 Dec 10 11:05:46 rocky-laptop kernel: [  700.003717] ===>rtl8192se_link_cha      nge():ieee->iw_mode is 2
10555 Dec 10 11:05:47 rocky-laptop kernel: [  701.522024] ===>rtl8192se_link_cha      nge():ieee->iw_mode is 2

```

I think it says wireless are wasting a lot of time. Am I right? How could I trouble shoot it please?

---

