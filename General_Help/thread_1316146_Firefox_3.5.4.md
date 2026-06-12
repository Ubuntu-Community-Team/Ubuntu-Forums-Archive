---
title: "Firefox 3.5.4"
date: 2009-11-05
forum: General Help
---

### Post by bob brazie on 2009-11-05
Is anyone having trouble with Firefox finding some pages but not others?

I can hit some pages just fine.

If I even type in the address bar google.com it says it cannot connect.

Most pages are loading real slow.

My wife's Explorer through Vista is connecting to the sites Firefox can't on the same dsl connection.

Any ideas? Thanks, Bob.

---

### Post by Crafty Kisses on 2009-11-05
Hmmm, have you tried disabling IPv6? This is fairly easy to do, so you need to run the following:
```
nano /etc/default/grub
```
Then change the following:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
To the following:
```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"
```
Then of course you need to update grub, so run:
```
update grub
```
Then you need to reboot, then check and see if IPv6 is working, you can do this by running:
```
cat /proc/sys/net/ipv6/conf/all/disable_ipv6
```
I'd also like to see the results of the following:
```
/etc/resolv.conf
```

---

### Post by cariboo on 2009-11-05
Unfortunately [s]Co[/s] Crafty Kisses the above doesn't work with Grub2. I would suggest you are having a dns problem. Open a terminal and type 

```
ping www.google.com
```

If that doesn't work, try:

```
ping 74.125.53.104
```

If that works, you have a dns problem.

To fix the problem right click Network-Manager and select Edit Connections, highlight your network device, then click the Edit button. Next click the IPv4 tab,Click the Method drop down and select Automatic (DHCP) Addresses Only. Enter your dns address in the dns test box and click apply, enter your password and you should be good to go.

---

### Post by bob brazie on 2009-11-05
It pinged just fine so I changed the settins to Automatic (DHCP) Addresses Only.

Not sure what dns setting is to type in.

Also I am replying on another machine running Firefox 3.0.14 as now the Firefox at fault is not letting me click the quick reply button. I click it and nothing happens.

---

### Post by lswb on 2009-11-05
Sometimes this is the culprit.

[http://ubuntuforums.org/showthread.php?t=1229334&page=3#25](http://ubuntuforums.org/showthread.php?t=1229334&page=3#25)

---

### Post by lovinglinux on 2009-11-05
See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

---

