---
title: "find out broadcast address"
date: 2012-02-10
forum: General Help
---

### Post by esbrinartot on 2012-02-10
I'm configuring an nfs server. "Portmap"

There is an step I have to introduce the IP broadcast address.

Which is my Broadcast address?

My submask is 255.255.255.0
Private IP range from 192.168.2.1 to 192.168.2.255

According to what I read should be 192.168.2.255 but later when I try to mount the partition I get an error.

If I use 192.168.2.0 then I can mount the folder I have lodged in my server.

CAn anyone let me know what I have to do to know my exact broadcast adress

---

### Post by Cheesemill on 2012-02-10
If your network range is  192.168.2.0/24 which I believe it is then:

IP Address Range:   192.168.2.1 - 192.168.1.254
Network:   192.168.2.0
Netmask:   255.255.255.0
Broadcast:   192.168.2.255

There are several on-line subnet calculators available to give you a hand, for example:
[http://www.subnet-calculator.com/subnet.php](http://www.subnet-calculator.com/subnet.php)

---

### Post by jonobr on 2012-02-10
Cheesemill is correct but from your post it looks like you tried putting in 192.168.2.255 which was correct , but you got the error.

What you entered and what worked was the  network number with the 0 at the end.

Seeing the error you got may help, but it sounds as if your software may have mixed up nomenclature in that it wanted the network address and not the broadcast address.

Could you post the error , maybe that may indicate something?

---

### Post by Khayyam on 2012-02-10
esbrianartot ..

The broadcast address 192.168.2.255 is correct for your subnet. 192.168.2.0 would be the 'network' address.

If you wanted to you could install ipcalc and do the math .. but its unnecessary. 

Does your client have /etc/hosts.allow and /etc/hosts.deny configured to deny "portmap : ALL" and "portmap : NFS server IP"?

HTH ...

---

### Post by esbrinartot on 2012-02-10
Thks to all. I will reply all your questions:

the configuration that gives me the error is:

To /etc/exports:
/mnt/intercambio 192.168.2.255/255.255.255.0(rw)

To /etc/host.allow
portmap:192.168.2.255/255.255.255.0
lockd:192.168.2.255/255.255.255.0
mountd:192.168.2.255/255.255.255.0
rquotad:192.168.2.255/255.255.255.0
statd:192.168.2.255/255.255.255.0

to /etc/hosts.deny
portmap:ALL
lockd:ALL
mountd:ALL
rquotad:ALL
statd:ALL
and then when I type:

sudo mount -t nfs 192.168.2.20:/mnt/intercambio /mnt


I get next error:
mount.nfs: requested NFS version or transport protocol is not supported

If instead 192.168.2.255 y Type 192.168.2.0 I can mount the partition

---

### Post by Cheesemill on 2012-02-10
That's the correct behaviour.

The exports file takes IP addresses in the form network/netmask not broadcast/netmask

You /etc/host.allow is also wrong, that should also be in the form network/netmask

---

### Post by esbrinartot on 2012-02-10
Then I understand that instead 192.168.2.255 I should write

192.168.2.0 (which is the same as write 192.168.2.1 + 192.168.2.2.... etc)

thks in advance for your explanations. If I used the broadcast address is because I've seen several tutorials using the broadcast address. I've seen more than one with broadcast address.... IT's weird!! But you must be correct because using networt/mask works

Once I mounted I can't find the hardisk icon on the desktop. Is it normal?

---

