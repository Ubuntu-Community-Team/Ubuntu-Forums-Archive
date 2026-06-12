---
title: "rc.local and /etc/init.d/networking stop - not working"
date: 2010-09-06
forum: General Help
---

### Post by youbuntu on 2010-09-06
Hi guys. I am trying an experiment for my own education, which does not seem to work.
When I do:

```
sudo /etc/init.d/networking stop
```

and then ping google.com, *it still replies*, ergo networking hasn't been stopped. I also added:

```
/etc/init.d/networking stop
```

to /etc/init.d/rc.local, and the same thing happens - network interfaces *are still up*

Would someone be kind enough to shed some light on this for me, please? Oh, and this is running as a guest in VirtualBox on a Mac host, with the guest (virtual) network card "bridged" to the Airport card.

Thanks in advance :)

---

### Post by Ozymandias_117 on 2010-09-06
> **glossywhite said:**
> Hi guys. I am trying an experiment for my own education, which does not seem to work.
When I do:

```
sudo /etc/init.d/networking stop
```

and then ping google.com, *it still replies*, ergo networking hasn't been stopped. I also added:

```
/etc/init.d/networking stop
```

to /etc/init.d/rc.local, and the same thing happens - network interfaces *are still up*

Would someone be kind enough to shed some light on this for me, please? Oh, and this is running as a guest in VirtualBox on a Mac host, with the guest (virtual) network card "bridged" to the Airport card.

Thanks in advance :)

Most likely ```
sudo /etc/init.d/networkmanager stop && sudo /etc/init.d/networking stop
``` should do the trick.

---

### Post by youbuntu on 2010-09-06
Thanks, but you've just told me the same command as I originally commented that *didn't* work!. Obviously I don't put "sudo" in the rc.local file, do I?.

PS: there is no such thing as "networkmanager" on my box

:S

---

### Post by Ozymandias_117 on 2010-09-06
> **glossywhite said:**
> Thanks, but you've just told me the same command as I originally commented that *didn't* work!. Obviously I don't put "sudo" in the rc.local file, do I?

:S

The only thing you mentioned was /etc/init.d/networking I also added /etc/init.d/networkmanager as well.

And no, rc.local doesn't need sudo.

Post the output of ```
ls /etc/init.d/ | grep -i network
```

I'm not running ubuntu right now, perhaps network manager is labeled differently in ubuntu.

edit: forgot the -i in case there are capitals.

---

### Post by youbuntu on 2010-09-06
> **Ozymandias_117 said:**
> The only thing you mentioned was /etc/init.d/networking I also added /etc/init.d/networkmanager as well.

And no, rc.local doesn't need sudo.

Post the output of ```
ls /etc/init.d/ | grep network
```

I'm not running ubuntu right now, perhaps network manager is labeled differently in ubuntu.

```

networking
network-interface
network-interface-security
network-manager

```

---

### Post by Ozymandias_117 on 2010-09-06
```
sudo /etc/init.d/network-manager stop && sudo /etc/init.d/networking stop
```

---

### Post by youbuntu on 2010-09-06
> **Ozymandias_117 said:**
> ```
sudo /etc/init.d/network-manager stop && sudo /etc/init.d/networking stop
```

That gives...


```


Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop network-manager
 * Deconfiguring network interfaces...
   ...done.


```

---

### Post by Ozymandias_117 on 2010-09-06
Did it stop your networking?

All that's saying is that going through /etc/init.d and stopping the process itself is no longer considered the "right" way, but either way still works right now.

---

