---
title: "privoxy not starting after upgrade to Karmic"
date: 2009-10-30
forum: General Help
---

### Post by Lekensteyn on 2009-10-30
After a upgrade to Karmic (9.10), I cannot start privoxy.
When running /etc/init.d/privoxy start, I get an error message:
```
pc@pc:/etc/privoxy$ /etc/init.d/privoxy start
Oct 30 11:56:24.584 b77248d0 Fatal error: Cannot setgid(): Insufficient permissions.

```
But, if I run it as root, it starts up well:
```
sudo /etc/init.d/privoxy start
```

---

### Post by Lekensteyn on 2009-10-30
Did some tests, the problem is caused by:
```
/usr/sbin/privoxy --pidfile /var/run/privoxy.pid --user privoxy /etc/privoxy/config
```
which can be shortened to:
```
/usr/sbin/privoxy --user privoxy /etc/privoxy/config
```

While this is working:
```
/usr/sbin/privoxy /etc/privoxy/config
```
This doesn't:
```
/usr/sbin/privoxy --user privoxy /etc/privoxy/config
```

---

### Post by Lekensteyn on 2009-10-30
Still having this problem :s

---

### Post by Lekensteyn on 2009-10-30
Still have the problem after another reboot :/

---

### Post by rubinstein on 2009-11-01
I've got the same problem. Is there a bug report about it? Looking... Ah, yes, there is: [https://bugs.launchpad.net/ubuntu/+source/privoxy/+bug/427625](https://bugs.launchpad.net/ubuntu/+source/privoxy/+bug/427625)

Will try some of the workarounds.

---

### Post by HolyJoe on 2009-11-03
> **Lekensteyn said:**
> Did some tests, the problem is caused by:
```
/usr/sbin/privoxy --pidfile /var/run/privoxy.pid --user privoxy /etc/privoxy/config
```
which can be shortened to:
```
/usr/sbin/privoxy --user privoxy /etc/privoxy/config
```

While this is working:
```
/usr/sbin/privoxy /etc/privoxy/config
```
This doesn't:
```
/usr/sbin/privoxy --user privoxy /etc/privoxy/config
```

Good post!
But privoxy can't auto start after reboot, so what is a correct way to do it?

---

### Post by Lekensteyn on 2009-11-11
And I'm still having this problem :/
The only way to start is, is doing it manually with "sudo /etc/init.d/privoxy start".

---

### Post by glibdud on 2009-11-22
After reading through the bug report that Rubinstein linked above, I made the following two changes, which fixed this issue for me.

In /etc/privoxy/config, line 741, I changed

```
listen-address  localhost:8118
```

to

```
listen-address  127.0.0.1:8118
```

...and in /etc/sysctl.conf, I added the line

```
net.ipv6.conf.all.disable_ipv6=1
```

The second one requires a reboot.

I'm not sure if it was one, the other, or a combination of the two that fixed it, but privoxy is now starting properly on boot-up for me.

---

### Post by Geoff918 on 2009-11-28
I changed line 741 from localhost to 127.0.0.1 as in the above post by gildbud. It worked perfectly! I made no change to the IPv6 settings.

The second part which gildbud performed I'm not sure if that would apply to me. I have IPv6 disabled on some of my systems, and others not. It looks like the code itself (if I'm interpreting right) sets IPv6 disable=true (basically turn it off). That could be superfluous depending on your setup. Anyway, SOLVED!  :popcorn:

---

### Post by bodhi.zazen on 2010-08-07
> **geoffconn said:**
> sudo /etc/init.d/privoxy start

This is an old thread. The solution I believe is to change the listen address in the config file from localhost:8118 to 127.0.0.1:8118 (privoxy apparently does not understand localhost).

```
sudo sed -i -e 's_localhost:8118_127.0.0.1:8118_g' /etc/privoxy/config
```

To manually start privoxy, use

```
sudo service privoxy start
```

But privoxy should start automatically.

Otherwise, this thread is almost a year old ...

---

### Post by joao82 on 2010-10-01
Thanks, changing localhost solved it.

---

