---
title: "lxc, rose and nr"
date: 2012-08-17
forum: General Help
---

### Post by Fatman_UK on 2012-08-17
Morning forumites.

Searched for this but didn't find, etc.

I've been messing around with LXC on my Lucid LTS Server. Created a few Lucid containers, struggling to get them to work (apparently LXC doesn't work too well with LXC as a guest or as a host... anyway, today I happened to do "ifconfig -a" on the host and I found an excess of interfaces.

(I'll post the list of interfaces when I get home, pastebinit doesn't seem to be working. It's a load of nr and rose interfaces.)

What I want to know is, where the hell did all those come from?

=== pasting manually ===

```

nr0       Link encap:AMPR NET/ROM  HWaddr
          NOARP  MTU:236  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nr1       Link encap:AMPR NET/ROM  HWaddr
          NOARP  MTU:236  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nr2       Link encap:AMPR NET/ROM  HWaddr
          NOARP  MTU:236  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nr3       Link encap:AMPR NET/ROM  HWaddr
          NOARP  MTU:236  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

rose0     Link encap:AMPR ROSE  HWaddr 0000000000
          NOARP  MTU:249  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

rose1     Link encap:AMPR ROSE  HWaddr 0000000000
          NOARP  MTU:249  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

rose2     Link encap:AMPR ROSE  HWaddr 0000000000
          NOARP  MTU:249  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[... identical interfaces all the way up to ...]

rose9     Link encap:AMPR ROSE  HWaddr 0000000000
          NOARP  MTU:249  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by Fatman_UK on 2012-08-21
Bump. No one knows where these rogue interfaces come from?

---

### Post by Fatman_UK on 2012-08-24
Bump.

---

### Post by Fatman_UK on 2012-08-28
Oops, I meant Lucid as a host or guest, not LXC. Too late to edit now.

Oh, and bump. ;)

---

