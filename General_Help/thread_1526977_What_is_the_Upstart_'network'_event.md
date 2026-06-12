---
title: "What is the Upstart 'network' event?"
date: 2010-07-08
forum: General Help
---

### Post by xfcmb on 2010-07-08
Hi all,

I'm writing an Upstart script which would run in the event a network cable is connected (i.e., the network interface get's an IP address.) However, I am having trouble figuring out which event I should use for the 'start on' directive.

Output of 'initctl list | grep network' shows the following networking related events: 

```
network-manager start/running, process 843
network-interface (lo) start/running
network-interface (eth0) start/running
network-interface (wlan0) start/running
network-interface-security start/running
networking stop/waiting

```network-manager starts at boot and doesn't change after that if the cable is disconnected so taht won't work. Also the network-interface* events stay started once the system is booted. 

The description for 'networking' states "This task causes virtual network devices that do not have an associated kernel object to be started on boot." So I'm not sure that is an option. 

I'm thinking perhaps there is a udevmonitor event I can use, but again, I'm not sure which one? 

Does anyone have any experience with this?

---

### Post by NCLI on 2010-07-08
Scripts which need to run when a connection has been established should be placed in "/etc/network/if-up.d", and scripts which need to run if the computer is disconnected should be placed in "/etc/network/if-down.d" ;)

---

### Post by xfcmb on 2010-07-08
I appreciate the reply, but I'm not sure that is going to help. The scenario I am envisioning is where a network cable is plugged in and then unplugged. Or the cable is plugged in but connectivity goes down. So the interface stays up but the connection is terminated and the host looses it's IP. I then want to run a script when that connection is re-established. 

It dosn't look like the interface actually goes down in the scenario above. I did a quick test by putting a script in if-up.d which would write a file to disk if it ran. I then unplugged the cable, waited to loose the IP and reconnected. Doesn't look like the file was written to disk.

---

### Post by kjohri on 2010-11-05
Try this link,

[Starting a network server after communication interface is up]("http://www.softprayog.in/troubleshooting/linux/starting-network-server-after-interface-is-up.shtml")

---

