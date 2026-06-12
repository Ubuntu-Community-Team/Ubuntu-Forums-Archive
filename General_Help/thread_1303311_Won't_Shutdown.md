---
title: "Won't Shutdown"
date: 2009-10-28
forum: General Help
---

### Post by gareththegeek on 2009-10-28
My copy of Xubuntu 8.04 often won't shut-down at my first attempt.

It hangs at the point where it is processing the shut-down script.  There is no code inside the shut-down script and I have never edited it.

Once the system hangs I have to press Ctrl+Alt+F1, log in and run 
```
sudo shut-down -P now
```
After this it shuts-down fine.

Any way I can find out what its hanging on? Are there logs somewhere I can look at?

Cheers
G!

---

### Post by gareththegeek on 2009-10-28
*bump* no one?

---

### Post by jeffus_il on 2009-10-28
try > sudo poweroff

---

### Post by P4man on 2009-10-28
have a look in /var/log/messages

---

### Post by gareththegeek on 2009-10-28
```
Oct 27 17:37:32 greyfloyd syslogd 1.5.0#1ubuntu1: restart.
Oct 27 17:37:55 greyfloyd kernel: [  670.102376] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 118
Oct 27 17:41:19 greyfloyd kernel: [  874.439326] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 118
Oct 27 17:44:45 greyfloyd kernel: [ 1079.677808] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 118
Oct 27 17:48:10 greyfloyd kernel: [ 1285.015714] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 118
Oct 27 17:51:35 greyfloyd kernel: [ 1490.253947] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 118
Oct 27 17:54:59 greyfloyd kernel: [ 1693.495758] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 118
Oct 27 17:58:25 greyfloyd kernel: [ 1899.830377] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 118
Oct 27 17:59:45 greyfloyd kernel: [ 1978.894795] rtc: lost 4 interrupts
Oct 27 18:01:49 greyfloyd kernel: [ 2103.069328] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 118
Oct 27 18:05:10 greyfloyd kernel: [ 2304.319317] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 118
Oct 27 18:06:32 greyfloyd kernel: [ 2386.441842] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 231
Oct 27 18:06:33 greyfloyd kernel: [ 2387.375483] r8169: eth0: link down
Oct 27 18:06:33 greyfloyd kernel: [ 2387.379330] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 27 18:06:33 greyfloyd kernel: [ 2387.448483] RX DESC dfb3b000  size = 2048
Oct 27 18:06:33 greyfloyd kernel: [ 2387.448851] <-- RTMPAllocTxRxRingMemory, Status=0
Oct 27 18:06:33 greyfloyd kernel: [ 2387.452710] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
Oct 27 18:06:33 greyfloyd kernel: [ 2387.452749] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
Oct 27 18:06:33 greyfloyd kernel: [ 2387.452787] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
Oct 27 18:06:33 greyfloyd kernel: [ 2387.452826] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
Oct 27 18:06:33 greyfloyd kernel: [ 2387.453462] 1. Phy Mode = 9
Oct 27 18:06:33 greyfloyd kernel: [ 2387.453464] 2. Phy Mode = 9
Oct 27 18:06:33 greyfloyd kernel: [ 2387.471000] 3. Phy Mode = 9
Oct 27 18:06:33 greyfloyd kernel: [ 2387.474350] RTMPSetPhyMode: channel is out of range, use first channel=1 
Oct 27 18:06:33 greyfloyd kernel: [ 2387.475398] MCS Set = ff ff 00 00 01
Oct 27 18:06:33 greyfloyd kernel: [ 2387.476964] <==== RTMPInitialize, Status=0
Oct 27 18:06:33 greyfloyd kernel: [ 2387.477027] 0x1300 = 00064300
Oct 27 18:06:33 greyfloyd kernel: [ 2387.534782] RX DESC f502a000  size = 2048
Oct 27 18:06:33 greyfloyd kernel: [ 2387.535529] <-- RTMPAllocTxRxRingMemory, Status=0
Oct 27 18:06:33 greyfloyd kernel: [ 2387.539972] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
Oct 27 18:06:33 greyfloyd kernel: [ 2387.540268] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
Oct 27 18:06:33 greyfloyd kernel: [ 2387.540564] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
Oct 27 18:06:33 greyfloyd kernel: [ 2387.540970] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
Oct 27 18:06:33 greyfloyd kernel: [ 2387.541993] 1. Phy Mode = 9
Oct 27 18:06:33 greyfloyd kernel: [ 2387.541995] 2. Phy Mode = 9
Oct 27 18:06:33 greyfloyd kernel: [ 2387.559688] 3. Phy Mode = 9
Oct 27 18:06:34 greyfloyd kernel: [ 2387.563052] RTMPSetPhyMode: channel is out of range, use first channel=1 
Oct 27 18:06:34 greyfloyd kernel: [ 2387.564277] MCS Set = ff ff 00 00 01
Oct 27 18:06:34 greyfloyd kernel: [ 2387.565865] <==== RTMPInitialize, Status=0
Oct 27 18:06:34 greyfloyd kernel: [ 2387.565929] 0x1300 = 00064300
Oct 27 18:06:34 greyfloyd kernel: [ 2387.648674] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
Oct 27 18:06:37 greyfloyd kernel: [ 2390.738473] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 231
Oct 27 18:06:37 greyfloyd kernel: [ 2390.738709] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
Oct 27 18:06:38 greyfloyd kernel: [ 2391.687004] Rcv Wcid(1) AddBAReq
Oct 27 18:06:38 greyfloyd kernel: [ 2391.687012] Start Seq = 00000000
Oct 27 18:06:49 greyfloyd kernel: [ 2402.573881] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 231
Oct 27 18:06:49 greyfloyd kernel: [ 2402.583247] wicd[7325]: segfault at 00000004 eip b7ac0f76 esp b783a3b8 error 6
Oct 27 18:15:54 greyfloyd kernel: [ 2948.087167] ams[7063]: segfault at 00000004 eip b790d4aa esp bfc62500 error 4
Oct 27 18:27:26 greyfloyd -- MARK --
Oct 27 18:47:26 greyfloyd -- MARK --
Oct 27 19:07:26 greyfloyd -- MARK --
Oct 27 19:27:26 greyfloyd -- MARK --
Oct 27 19:38:08 greyfloyd kernel: [ 7878.190102] usb 3-1: USB disconnect, address 3
Oct 27 19:38:10 greyfloyd kernel: [ 7879.938725] usb 3-2: USB disconnect, address 4
Oct 27 19:39:41 greyfloyd kernel: [ 7970.807079] usb 3-2: new full speed USB device using uhci_hcd and address 5
Oct 27 19:39:41 greyfloyd kernel: [ 7970.956084] usb 3-2: configuration #1 chosen from 1 choice
Oct 27 19:39:43 greyfloyd kernel: [ 7972.570940] usb 3-1: new full speed USB device using uhci_hcd and address 6
Oct 27 19:39:43 greyfloyd kernel: [ 7972.735320] usb 3-1: configuration #1 chosen from 1 choice
Oct 27 19:43:46 greyfloyd kernel: [ 8215.923906] usb 3-1: USB disconnect, address 6
Oct 27 19:43:47 greyfloyd kernel: [ 8216.673315] usb 3-2: USB disconnect, address 5
Oct 27 20:07:26 greyfloyd -- MARK --
Oct 27 20:27:26 greyfloyd -- MARK --
Oct 27 20:43:48 greyfloyd kernel: [11814.297702] usb 3-2: new full speed USB device using uhci_hcd and address 7
Oct 27 20:43:48 greyfloyd kernel: [11814.446681] usb 3-2: configuration #1 chosen from 1 choice
Oct 27 20:43:50 greyfloyd kernel: [11816.541936] usb 3-1: new full speed USB device using uhci_hcd and address 8
Oct 27 20:43:50 greyfloyd kernel: [11816.706493] usb 3-1: configuration #1 chosen from 1 choice
Oct 27 20:55:58 greyfloyd kernel: [12544.512181] usb 3-1: USB disconnect, address 8
Oct 27 20:55:59 greyfloyd kernel: [12545.011789] usb 3-2: USB disconnect, address 7
Oct 27 20:58:06 greyfloyd kernel: [12671.627977] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 118
```

Then loads of 
```
Oct 27 20:58:14 greyfloyd kernel: [12679.623675] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 118
```

lines at the point when I'd asked it to shutdown and left the room, then at the time I came back and noticed it was still running

```
Oct 27 21:53:49 greyfloyd exiting on signal 15
```

And that's it for yesterday

Does this mean anything to anyone?

Cheers

---

