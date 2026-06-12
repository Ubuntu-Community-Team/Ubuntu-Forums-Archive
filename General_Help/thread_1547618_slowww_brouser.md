---
title: "slowww brouser"
date: 2010-08-07
forum: General Help
---

### Post by Fred9020 on 2010-08-07
I was using Freespire but the version of Firefox was old and I read that Freespire was an old and obsolete OS  so I installed Ubuntu 10.4.   I like everything about it so far but Firefox brouser is very slow. It can take up to 30 seconds sometimes to load a web page. Just surfing the web is difficult, any thoughts Thanks......Oh I do have high speed internet service  and a router, I have an XP and a Vista system both are fine and even this system when it had Freespire was fine. It just started when I installed Ubuntu

---

### Post by lovinglinux on 2010-08-07
Disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]

---

### Post by darolu on 2010-08-07
You can fix it by stopping ipv6 from your Grub too, this will also solve the problem with Opera being extremely slow. Open gedit with super user powers and edit your /etc/default/grub file:
```
gksu gedit /etc/default/grub
```

There find the line that says **GRUB_CMDLINE_LINUX=""** and change it to:
```
GRUB_CMDLINE_LINUX="ipv6.disable=1"
```
Save the file and run:
```
sudo update-grub
```
Then reboot, your browsers should be working as fast as usual.

To prove that ipv6 is indeed disabled you can run:
```
lsmod | grep ipv6
```
and
```
ip a | grep inet6
```
It shouldn't print anything.

---

### Post by DeMus on 2010-08-07
What if I see this:

jan@Ultimate:~$ lsmod | grep ipv6
jan@Ultimate:~$ ip a | grep inet6
    inet6 ::1/128 scope host 
    inet6 fe80::21e:8cff:febd:f3ca/64 scope link 
jan@Ultimate:~$

Edit: Sorry, found it. Just did the disable IPV6 in Firefox an now it's okay.

---

### Post by lovinglinux on 2010-08-07
> **darolu said:**
> You can fix it by stopping ipv6 from your Grub too...

Yep, that will do too.

---

### Post by darolu on 2010-08-07
> **DeMus said:**
> What if I see this:

jan@Ultimate:~$ lsmod | grep ipv6
jan@Ultimate:~$ ip a | grep inet6
    inet6 ::1/128 scope host 
    inet6 fe80::21e:8cff:febd:f3ca/64 scope link 
jan@Ultimate:~$

Edit: Sorry, found it. Just did the disable IPV6 in Firefox an now it's okay.
The first part means your ipv6 modules are not being loaded, in theory (for what I understand) that should be enough to fix it, but for some reason (that is beyond my comprehension) browsers can still (try to) use ipv6; this is specially noticeable with Opera.
The second part means you're still running a collection of ipv6-centered protocols ([inet6]("http://www.manpagez.com/man/4/inet6/")), and in practical words you may still experience problems (specially with Opera), disabling ipv6 from your kernel boot should fix it though; if you did add the lines to your /etc/default/grub file and did run update-grub after and it is still showing that... then I have no idea how to stop it.

---

