---
title: "KVPNC Dropping out after 4min 15 seconds"
date: 2010-11-08
forum: General Help
---

### Post by damien_d on 2010-11-08
Since upgrading to 10.10, I am having some difficulties with KVPNC. It used to work well.

It seems to disconnect after precisely 4min 15 seconds.  The log from the window is shown below with the sensitive bits redacted.

```

info: Reconnect after connection lost enabled, reconnecting...
debug: vpnc: /usr/sbin/vpnc
info: Gateway hostname (<redacted>) resolved to "<redacted>".
debug: vpnc version (major): "0"
debug: vpnc version (minor): "5"
debug: vpnc version (subminor): "3"
debug: Some account data which was needed was obtained from a password dialog.
info: Profile "<redacted>" saved.
debug: Default interface: "eth0".
debug: IP address of default interface: "192.168.1.3".
debug: VpncScript: /root/.kde/share/apps/kvpnc/vpnc-script.<redacted>
debug: Support for TUN/TAP found (compiled into kernel or kernel module already loaded).
debug: Using NAT-T mode "natt".
debug: Using UDP.
info: Trying to connect to server "<redacted>" (<redacted>) with user "dud" and IPSec ID "lgs_all"... 
debug: Setting DNS_UPDATE "Yes".
debug: Vpnc has started
debug: "vpnc" started.
debug: [vpnc] Group password requested, send it... 
debug: vpnc version (major): "0"
debug: vpnc version (minor): "5"
debug: vpnc version (subminor): "3"
debug: [vpnc] User password requested, send it... 
debug: [vpnc] Connect banner received
info: 
success: [vpnc] Connection established.
success: 
debug: [vpnc] Tunnel IP: 10.67.3.50
debug: setFirewallAfterConnectScript: /root/.kde/share/apps/kvpnc/firewall_after_connect_script.leica_sui 
debug: "SetFirewallAfterConnectScript" started.
debug: "SetFirewallAfterConnectScript" finished.
debug: Use gateway address (<redacted>) for connection status check.
debug: "ping_check.sh" started.
error: Ping to <redacted> within 10 checks every 20s has failed.
debug: Disconnect requested
debug: Disconnect requested, status connected
debug: SetFirewallBeforeDisconnect: /root/.kde/share/apps/kvpnc/firewall_after_connect_script.<redacted> 
debug: "setFirewallBeforeDisconnect" started.
debug: "setFirewallBeforeDisconnect" finished.
debug: Vpnc pid file found, killing process 3690
success: Successful disconnected.
info: Connection duration was 00 hours, 04 minutes, 15 seconds
debug: Disconnected.

```

The 4min 15 seconds (or 14 seconds) is consistent:

```

info: Connection duration was 00 hours, 04 minutes, 14 seconds
info: Connection duration was 00 hours, 04 minutes, 14 seconds
info: Connection duration was 00 hours, 04 minutes, 15 seconds
info: Connection duration was 00 hours, 04 minutes, 15 seconds
info: Connection duration was 00 hours, 04 minutes, 15 seconds

```

Does anyone know the significance as to why it wants to drop out after this time? And, of course, if there is anything I can do about it.

  -- Damien

---

### Post by purct on 2010-12-08
> **damien_d said:**
> Since upgrading to 10.10, I am having some difficulties with KVPNC. It used to work well.

It seems to disconnect after precisely 4min 15 seconds.  The log from the window is shown below with the sensitive bits redacted.

```

info: Reconnect after connection lost enabled, reconnecting...
debug: vpnc: /usr/sbin/vpnc
info: Gateway hostname (<redacted>) resolved to "<redacted>".
debug: vpnc version (major): "0"
debug: vpnc version (minor): "5"
debug: vpnc version (subminor): "3"
debug: Some account data which was needed was obtained from a password dialog.
info: Profile "<redacted>" saved.
debug: Default interface: "eth0".
debug: IP address of default interface: "192.168.1.3".
debug: VpncScript: /root/.kde/share/apps/kvpnc/vpnc-script.<redacted>
debug: Support for TUN/TAP found (compiled into kernel or kernel module already loaded).
debug: Using NAT-T mode "natt".
debug: Using UDP.
info: Trying to connect to server "<redacted>" (<redacted>) with user "dud" and IPSec ID "lgs_all"... 
debug: Setting DNS_UPDATE "Yes".
debug: Vpnc has started
debug: "vpnc" started.
debug: [vpnc] Group password requested, send it... 
debug: vpnc version (major): "0"
debug: vpnc version (minor): "5"
debug: vpnc version (subminor): "3"
debug: [vpnc] User password requested, send it... 
debug: [vpnc] Connect banner received
info: 
success: [vpnc] Connection established.
success: 
debug: [vpnc] Tunnel IP: 10.67.3.50
debug: setFirewallAfterConnectScript: /root/.kde/share/apps/kvpnc/firewall_after_connect_script.leica_sui 
debug: "SetFirewallAfterConnectScript" started.
debug: "SetFirewallAfterConnectScript" finished.
debug: Use gateway address (<redacted>) for connection status check.
debug: "ping_check.sh" started.
error: Ping to <redacted> within 10 checks every 20s has failed.
debug: Disconnect requested
debug: Disconnect requested, status connected
debug: SetFirewallBeforeDisconnect: /root/.kde/share/apps/kvpnc/firewall_after_connect_script.<redacted> 
debug: "setFirewallBeforeDisconnect" started.
debug: "setFirewallBeforeDisconnect" finished.
debug: Vpnc pid file found, killing process 3690
success: Successful disconnected.
info: Connection duration was 00 hours, 04 minutes, 15 seconds
debug: Disconnected.

```

The 4min 15 seconds (or 14 seconds) is consistent:

```

info: Connection duration was 00 hours, 04 minutes, 14 seconds
info: Connection duration was 00 hours, 04 minutes, 14 seconds
info: Connection duration was 00 hours, 04 minutes, 15 seconds
info: Connection duration was 00 hours, 04 minutes, 15 seconds
info: Connection duration was 00 hours, 04 minutes, 15 seconds

```

Does anyone know the significance as to why it wants to drop out after this time? And, of course, if there is anything I can do about it.

  -- Damien

I had a similar problem.  I found that it was best to disabled the connection status check in the KVPNC profile....

click on settings menu --> configure VPNC

then click on Network - General 

untick Check Connection Status

hope that helps!

---

### Post by berserkergang on 2010-12-22
> **purct said:**
> I had a similar problem.  I found that it was best to disabled the connection status check in the KVPNC profile....

click on settings menu --> configure VPNC

then click on Network - General 

untick Check Connection Status

hope that helps!
I registered just to thank you for this answer. Ive been trying to fix this for two weeks now and couldn't find any relevant information anywhere.
Your advice helped me anyway- although I'm running Debian Sid- so thank you very much! :D

---

### Post by notam42 on 2011-05-09
Thanks for the information, this problem has been driving me nuts for a while.  Some additional information on this issue which hopefully will help others seeing the same issue.  

In my environment at least, the problem was due to the fact that the ping_check.sh script generated by kvpnc was using the external hostname of the Cisco VPN server.  Due to the firewall rules in place with my employer, once you connected to the VPN you could no longer ping that address via the VPN tunnel.  The connection check would fail after timing out and voila, connection lost.  

Solution: Change Ping hostname/IP address in the Network-General settings to the name or IP address of a  server on the internal network that is only accessible once the VPN tunnel was established.

---

### Post by ntg on 2011-06-01
> **notam42 said:**
> Due to the firewall rules in place with my employer, once you connected to the VPN you could no longer ping that address via the VPN tunnel.

Thanx for both advices. Solution worked, and knowing what was (and still is - i m not administering) helps.

---

### Post by jmenbell on 2012-07-10
Thaks for your post, it fixed my problem with disconnections every 4 minutes. I untick "Check Connection Status" and no more disconnections.
Regards

---

