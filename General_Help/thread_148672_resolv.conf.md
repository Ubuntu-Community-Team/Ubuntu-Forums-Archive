---
title: "resolv.conf"
date: 2006-03-22
forum: General Help
---

### Post by shiznatix on 2006-03-22
Hello.

Ok so at work I used my laptop and the admin manually edited my resolv.conf file to get my internet working. Well now I come home and the internet wont work. When I do

ifconfig up wlan0

it says:

wlan0: Host name lookup failure

I don't know how to fix that and I can't all tech support because they don't speak English ever. Any ideas?

Edit: I don't know if it helps but my other computer (the one i am on now) has windows xp installed so maybe I can get somthing from there?

---

### Post by seoatway on 2006-03-22
post a copy of the resolv.conf and we can see if it has a problem

---

### Post by shiznatix on 2006-03-22
uhhh, its empty. He edited it to look like

domain exent-tech
nameserver 192.168.1.19

but i dont know what it was originally. i trusted he knew what he was doing

---

### Post by seoatway on 2006-03-22
you need to replace the nameserver entry with a valid public DNS, he has set it to use a DNS server in your office so it will not resolve external addresses.

Try 
nameserver 158.152.1.43
nameserver 158.152.1.58
 These are the DNS servers at Demon.co.uk which I use.

---

### Post by nanotube on 2006-03-22
the command is supposed to be "ifconfig wlan0 up", not ifconfig up wlan0. that might help. :)
its even easier to use command "ifup wlan0" (ifup is a shortcut for ifconfig xxx up).

---

### Post by shiznatix on 2006-03-22
nice suggestions but neither worked. the ifconfig up wlan0 gave no error messages but thats it.

I always just get a 'server not found' error or the page will try to load for a half hour.

---

### Post by claes on 2006-03-22
[QUOTE=seoatway]you need to replace the nameserver entry with a valid public DNS, he has set it to use a DNS server in your office so it will not resolve external addresses.
[/QUOTE]

If the internal dns server have access to the internet it will resolve external names just fine. If it doesn't the internal dns is either configured wrong or configured so internal users shouldn't be using internet.

Claes

---

### Post by hajk on 2006-03-22
What is the OP's home network setup? Is he connected to a DSL router? In that case the router may be the nameserver...

---

### Post by noswal on 2006-03-22
From my limited time with ubuntu you use

sysctl -a | fgrep tcp

to see what the current settings are and only edit the file if you want to change any.

The only settings I found which may need changing are
# Turn on the tcp_timestamps
net.ipv4.tcp_timestamps = 0
#
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
#Turn on the tcp_windowscaling
net.ipv4.tcp_window_scaling = 1

see  [http://syntest.psc.edu/](http://syntest.psc.edu/)

---

