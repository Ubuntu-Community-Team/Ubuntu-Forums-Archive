---
title: "Bash script"
date: 2012-01-14
forum: General Help
---

### Post by Xgen on 2012-01-14
I want to automate some startup programs in order, but not start until the wireless internet is connected.

For instance, keep waiting until the internet is connected, start conky next and then other programs last.

Edit: Sorry, this was supposed to go under the General Forum.

---

### Post by Xgen on 2012-01-14
I want to automate some startup programs in order, but not start until the wireless internet is connected.

For instance, keep waiting until the internet is connected, start conky next and then other programs last.

---

### Post by effenberg0x0 on 2012-01-14
Check /etc/NetworkManager/dispatcher.d/.

On your script, make sure to check the SSID, something like:

```
#!/bin/bash
# This is a horrible draft. Do not use it or judge me :)

main() {
   if [[ $# -ne 1 ]]; then
       printf "\nWrong number of args"  
       exit 1
   else
       local current_ssid=$1
       local my_ssid="my_access_point_name"
       if [[ ${my_ssid} != current_ssid ]]; then
         printf "\nI'm not connected to the right ap (%s)." "${my_ssid}"
         exit 1
       else
         doStuff
       fi
   fi
}

doStuff() {
 #Do your thing
}

case $1 in
  *)
  main ${CONNECTION_UUID}
  ;;
esac
```

---

### Post by cariboo on 2012-01-14
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Doug S on 2012-01-14
You could add a post-up option in the wireless interface section of your /etc/network/interfaces file. Below is my interfaces file, using the pre-up option to execute my iptables script before the looback interface is brought up (with credit to dangertux, as I learned this from one of his postings).```
# Smythies 2011.11.15 Can I execute my firewall script from here
#          instead of /etc/rc2.d? Add it.
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
[COLOR=red]pre-up /home/doug/init/doug_firewall[/COLOR]
# The primary interface (d-link PCI card)
auto eth1
iface eth1 inet dhcp
# Local network interface (uses built in ethernet port)
auto eth0
iface eth0 inet static
  address 192.168.111.1
  network 192.168.111.0
  netmask 255.255.255.0
  broadcast 192.168.111.255

```
Edit: When I wrote this I had not seen the other reply, which I assume was on the other thread pre-merger.

---

### Post by Xgen on 2012-01-14
Thanks for the fast response, guys but my skills are quite limited :). I will try your suggestions.

---

