---
title: "Netgear wg111v2 usb wireless network interface"
date: 2006-05-19
forum: General Help
---

### Post by aoberoi on 2006-05-19
im having some problems gettin a wireless network connection working correctly...

i have a USB wireless nic... Netgear WG111v2
Im running Ubuntu 5.10 amd64
there is an existing wired NIC on my MB that works when im wired (incase that matters)

I've been follwoing this tutorial on setting the connection up.. [link]("https://wiki.ubuntu.com/WifiDocs/Device/NetgearWG111")

> 
root@ankurpc:~# ndiswrapper -l
No drivers installed
root@ankurpc:~# pwd
/home/ankur
root@ankurpc:~# cd Driver/
root@ankurpc:~/Driver# cd WIN2000
root@ankurpc:~/Driver/WIN2000# ls
Net111v2.inf  WG111V2.sys
root@ankurpc:~/Driver/WIN2000# ndiswrapper -i Net111v2.inf
Installing net111v2
root@ankurpc:~/Driver/WIN2000# ndiswrapper -l
Installed ndis drivers:
net111v2        driver present, hardware present
root@ankurpc:~/Driver/WIN2000# modprobe ndiswrapper
root@ankurpc:~/Driver/WIN2000# tail /var/log/syslog
May 19 11:28:48 localhost dhclient: No working leases in persistent database - s leeping.
May 19 11:31:53 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 4
May 19 11:31:57 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 5
May 19 11:32:00 localhost kernel: [  672.180978] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
May 19 11:32:00 localhost loadndisdriver: *** glibc detected *** free(): invalid  pointer: 0x00002aaaaaaf4000 ***
May 19 11:32:00 localhost kernel: [  672.191509] ndiswrapper (check_nt_hdr:145):  Windows driver is not 64-bit; bad magic: 010B
May 19 11:32:00 localhost kernel: [  672.191516] ndiswrapper (load_sys_files:456 ): unable to prepare driver 'net111v2'
May 19 11:32:00 localhost kernel: [  672.197291] ndiswrapper (ndiswrapper_load_d river:92): loadndiswrapper failed (6); check system log for messages from 'loadn disdriver'
May 19 11:32:00 localhost kernel: [  672.197308] usbcore: registered new driver ndiswrapper
May 19 11:32:02 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 12
root@ankurpc:~/Driver/WIN2000# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

root@ankurpc:~/Driver/WIN2000#


i dont have any information about wlan0 like it says i should... there is some information about eth0 tho..

is there something im doing wong or a way i can go back to troubleshoot what the problem is being caused by?

i did the exact same thign with the winxp drivers too... same stuff happened.. any other ideas?

any help is much appreciated.

---

