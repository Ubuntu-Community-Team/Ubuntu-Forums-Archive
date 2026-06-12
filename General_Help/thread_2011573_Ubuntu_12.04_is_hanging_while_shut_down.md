---
title: "Ubuntu 12.04 is hanging while shut down"
date: 2012-06-27
forum: General Help
---

### Post by jsmanian on 2012-06-27
Dear All,

     I have ubuntu 12.04 X64 bit OS. My system hangs while shut down. But in restart, there is no issue. I removed Nvidia graphics card driver also. And I tried ACPI OFF/FORCE both. But my system still hangs. I know some of you have this issue and solved. Could anybody give some workaround to solve this. 
Auth.log
[HTML]Jun 27 08:46:26 jsm dbus[580]: [system] Rejected send message, 2 matched rules; type="error", sender=":1.6" (uid=0 pid=767 comm="NetworkManager ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.80" (uid=0 pid=2878 comm="/usr/sbin/pppd nodetach lock nodefaultroute ttyACM")
Jun 27 08:46:33  dbus[580]: last message repeated 4 times
Jun 27 08:46:33 jsm polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.46, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)[/HTML]

syslog

[HTML]Jun 27 08:17:01 jsm CRON[3319]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 27 08:46:26 jsm NetworkManager[767]: <info> (ttyACM0): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Jun 27 08:46:26 jsm NetworkManager[767]: <info> (ttyACM0): deactivating device (reason 'user-requested') [39]
Jun 27 08:46:26 jsm pppd[2878]: Terminating on signal 15
Jun 27 08:46:26 jsm pppd[2878]: Connect time 115.3 minutes.
Jun 27 08:46:26 jsm pppd[2878]: Sent 14939802 bytes, received 85913958 bytes.
Jun 27 08:46:26 jsm NetworkManager[767]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Jun 27 08:46:26 jsm NetworkManager[767]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Jun 27 08:46:26 jsm pppd[2878]: Connection terminated.
Jun 27 08:46:26 jsm avahi-daemon[677]: Withdrawing workstation service for ppp0.
Jun 27 08:46:26 jsm NetworkManager[767]: <info> DNS: starting dnsmasq...
Jun 27 08:46:26 jsm dnsmasq[2918]: exiting on receipt of SIGTERM
Jun 27 08:46:26 jsm NetworkManager[767]: <info> (ttyACM0): writing resolv.conf to /sbin/resolvconf
Jun 27 08:46:26 jsm dnsmasq[3362]: started, version 2.59 cache disabled
Jun 27 08:46:26 jsm dnsmasq[3362]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jun 27 08:46:26 jsm dnsmasq[3362]: warning: no upstream servers configured
Jun 27 08:46:26 jsm modem-manager[2864]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connected -> disconnecting)
Jun 27 08:46:26 jsm NetworkManager[767]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 27 08:46:26 jsm dbus[580]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 27 08:46:27 jsm dbus[580]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 27 08:46:29 jsm pppd[2878]: Exit.
Jun 27 08:46:31 jsm modem-manager[2864]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (disconnecting -> registered)
Jun 27 08:46:35 jsm kernel: Kernel logging (proc) stopped.
Jun 27 08:46:35 jsm rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="624" x-info="http://www.rsyslog.com"] exiting on signal 15.[/HTML]

---

### Post by jsmanian on 2012-06-27
No comments from anyone? If I cannot find the solution, I need to look for some other linux OS. There is no other choice for me

---

### Post by dcsoldschool53 on 2012-06-27
I don't have a solution,  but have you tried the shutdown command```
sudo shutdown -P now
```It just might work. Try it.

---

### Post by jsmanian on 2012-06-27
Hi,

   Thanks for your reply. I tried that also. It is not working for me. But sudo halt -p works randomly. 

   I am new to linux. I could not understand what causes this hanging issue.

---

### Post by kalkems on 2012-06-28
Maybe this is what you mean acpi force.  I put this in grub som acpi is switched off at startup.  Since doing I haven't had any more problems.

---

### Post by dino99 on 2012-06-28
Looks like you have more than one session running (aka Session2 into the first messages)

so it refuse to shutdown because a session is still opened; kill that process if its a zombie

---

### Post by Monotoko on 2012-06-28
Looks to me like Network Manager is having issues. What I'd do to test this is switch to a terminal (ctrl+alt+F1) then run "sudo service network-manager stop"

Then try to shutdown and see if it works...

EDIT: If that doesn't work, kill the entire session and try again (sudo killall Xorg)

---

### Post by Monotoko on 2012-06-28
Ohhh wonderful... spam, thanks for that. If you are serious about wanting help (and not just spamming the forum) there are three posts above.

---

### Post by jsmanian on 2012-06-29
Thanks for your comments. Sorry for the delayed reply.

It looks like there are three more work arounds to check for me:p
Hi kalkems,
> Maybe this is what you mean acpi force. I put this in grub som acpi is switched off at startup. Since doing I haven't had any more problems.
 
   I put acpi force in grub only (/etc/grub). This is mentioned in another thread. It is not helped me. Did you have nvidia graphics card in your system?

Hi dino99,
> Looks like you have more than one session running (aka Session2 into the first messages)

so it refuse to shutdown because a session is still opened; kill that process if its a zombie

I am not running zombie. I am not getting your point. Sorry. could you please tell what to do.

Hi Monotoko
> Looks to me like Network Manager is having issues. What I'd do to test this is switch to a terminal (ctrl+alt+F1) then run "sudo service network-manager stop"

Then try to shutdown and see if it works...

EDIT: If that doesn't work, kill the entire session and try again (sudo killall Xorg)
I will check and let you know the result.

> Ohhh wonderful... spam, thanks for that. If you are serious about wanting help (and not just spamming the forum) there are three posts above.

What do you mean? I didn't put any spam messages here.

---

### Post by kalkems on 2012-06-30
No.  My graphics card is an Intel 32 or 35 hundred something,  which is giving me problems when using an external monitor as this card doesn't have 1280x800 as standard but my external monitor wants that resolution.
I didn't really connect the problem to the graphics card at the time just tried out the methods others had tried to shutdown the computer.

---

### Post by jsmanian on 2012-06-30
Luckily I can shut down the system by using **sudo shutdown -P now**

  Just I have question that it might be corrupt the OS files and hardwares. Shall we use this command for daily?  Please clarify this.

I think my hanging issue is almost over.

---

