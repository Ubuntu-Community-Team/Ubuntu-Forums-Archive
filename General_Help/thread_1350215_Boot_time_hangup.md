---
title: "Boot time hangup"
date: 2009-12-09
forum: General Help
---

### Post by rajkhand on 2009-12-09
I have been using this machine for the past 2 years and suddenly today Ubuntu 9.10 will not boot. It stops at starting NTP ntpd line and then nothing happens.

This system was working perfectly till yesterday evening when I shut it down properly.

I do not know how to solve this problem, can someone please help me by pointing out what I should do to resolve the issue.

TIA
Raj

---

### Post by Achilles124 on 2009-12-09
Well, I have an issue with bootup myself. So maybe we can help each other out. Have you tried the Live CD? If your computer boots well from the live CD, then you know it is not the hardware. 

You can also check your harddisk with the LiveCD. 

If you have checked these things out, then come back to the forum.

---

### Post by rajkhand on 2009-12-09
I have been upgrading from earlier versions so do not have the boot cd but will download one.

I don't think that there is a problem with the hardware as window xp wich is on a different hard disk is working perfectly

---

### Post by Achilles124 on 2009-12-09
I don't know what the Ntpd line is, but if the LiveCD works well, you could go into BIOS. There is an option there called: Load Fail-Safe Defaults.

For more information: [http://www.buildeasypc.com/sw/bios_setup.htm#fail_safe]("http://www.buildeasypc.com/sw/bios_setup.htm#fail_safe")

Disclaimer: I am an newbie, and I cannot guarantee success.

---

### Post by AlexDudko on 2009-12-12
It may be a bug in **ntpd** demon. I had "keep synchronized with internet servers" option in **System -> Time and Date Settings** inabled and several days ago noticed sudden freezes both during startup and even while working. In the latter case computer after some time of a freeze just rebooted.
In any case the last log before system went into reboot was:
> Dec 12 19:19:22 alex-laptop ntpd[2444]: sendto(130.149.17.8) (fd=22): Invalid argument
Dec 12 19:19:23 alex-laptop gdm-simple-slave[4789]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Dec 12 19:19:23 alex-laptop NetworkManager: <info>  Policy set 'Wired connection 1' (eth0) as default for routing and DNS.
Dec 12 19:19:23 alex-laptop NetworkManager: <info>  (eth0): device state change: 8 -> 3 (reason 38)
Dec 12 19:19:23 alex-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 38).
Dec 12 19:19:23 alex-laptop NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Dec 12 19:19:23 alex-laptop avahi-daemon[823]: Withdrawing address record for 192.168.0.xxx on eth0.
Dec 12 19:19:23 alex-laptop avahi-daemon[823]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.xxx.
Dec 12 19:19:23 alex-laptop avahi-daemon[823]: Interface eth0.IPv4 no longer relevant for mDNS.
Dec 12 19:19:23 alex-laptop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 12 19:19:23 alex-laptop acpid: client 1314[0:0] has disconnected
Dec 12 19:19:23 alex-laptop acpid: client connected from 4790[0:0]
Dec 12 19:19:23 alex-laptop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Dec 12 19:19:25 alex-laptop ntpd[2444]: sendto(213.222.193.35) (fd=22): Invalid argument
Dec 12 19:19:36 alex-laptop NetworkManager: <debug> [1260638376.002018] ensure_killed(): waiting for vpn service pid 2446 to exit
Dec 12 19:19:36 alex-laptop NetworkManager: <debug> [1260638376.002366] ensure_killed(): vpn service pid 2446 cleaned up
Dec 12 19:20:15 alex-laptop wpa_supplicant[1277]: CTRL-EVENT-SCAN-RESULTS 
Dec 12 19:20:22 alex-laptop ntpd[2444]: sendto(130.149.17.21) (fd=22): Invalid argument
Dec 12 19:20:26 alex-laptop ntpd[2444]: sendto(130.149.17.8) (fd=22): Invalid argument
Dec 12 19:20:30 alex-laptop ntpd[2444]: sendto(213.222.193.35) (fd=22): Invalid argument
Dec 12 19:21:15 alex-laptop wpa_supplicant[1277]: CTRL-EVENT-SCAN-RESULTS 
Dec 12 19:21:27 alex-laptop ntpd[2444]: sendto(130.149.17.21) (fd=22): Invalid argument
Dec 12 19:21:30 alex-laptop ntpd[2444]: sendto(130.149.17.8) (fd=22): Invalid argument
Dec 12 19:21:34 alex-laptop ntpd[2444]: sendto(213.222.193.35) (fd=22): Invalid argument
Dec 12 19:22:15 alex-laptop wpa_supplicant[1277]: CTRL-EVENT-SCAN-RESULTS 
Dec 12 19:22:31 alex-laptop ntpd[2444]: sendto(130.149.17.21) (fd=22): Invalid argument
Dec 12 19:22:33 alex-laptop ntpd[2444]: sendto(130.149.17.8) (fd=22): Invalid argument
Dec 12 19:22:39 alex-laptop ntpd[2444]: sendto(213.222.193.35) (fd=22): Invalid argument
Dec 12 19:22:40 alex-laptop ntpd[2444]: Deleting interface #5 eth0, 192.168.0.xxx#123, interface stats: received=0, sent=20, dropped=0, active_time=27301 secs
Dec 12 19:22:40 alex-laptop ntpd[2444]: Deleting interface #6 ppp0, 10.0.30.9xxx#123, interface stats: received=715, sent=829, dropped=11, active_time=27000 secs


Try to disable NTP.

---

### Post by rajkhand on 2009-12-15
I edited the menu.lst file and removed the quiet splash vga=798 after ro 
so that now it is like follows

title		Ubuntu 9.10, kernel 2.6.31-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=48552043-0086-4ec1-a89a-2c906adc9b52 ro  
initrd		/boot/initrd.img-2.6.31-16-generic


now it boots perfectly all the time. But frankly I don't know the reason why it is working now!! Can some Guru enlighten me?

Raj

---

