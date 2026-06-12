---
title: "How to check internet speed in the terminal?"
date: 2011-02-09
forum: General Help
---

### Post by newn on 2011-02-09
Hi everybody.
Is there a way to check your up/down speed using the terminal?
My internet connection seems to be limited at about 1MB/s, judging from how one program works, after reinstalling OS.

Thanks.

---

### Post by sikander3786 on 2011-02-09
One method would be to use nload.

[http://packages.ubuntu.com/lucid/net/nload](http://packages.ubuntu.com/lucid/net/nload)

---

### Post by newn on 2011-02-09
Yea, found that, but not really sure, what it says:
Incoming:
Curr: 49.53 kBit/s
Avg: 117.28 kBit/s
Min: 33.67 kBit/s
Max: 0.28 kBit/s
Ttl: 14.34 GByte
Outgoing:
Curr: 56.29 kBit/s
Avg: 56.24 kBit/s
Min: 44.77 kBit/s
Max: 79.67 kBit/s
Ttl: 982.78 MByte

---

### Post by sikander3786 on 2011-02-09
I am not sure either, what those numbers are saying but man page might give you a clue.

```
man nload
```

---

### Post by JC Cheloven on 2011-02-09
Incoming: [COLOR="Red"]data for incoming traffic[/COLOR]
Curr: 49.53 kBit/s[COLOR="Red"] current, speed right now[/COLOR]
Avg: 117.28 kBit/s[COLOR="Red"] average[/COLOR]
Min: 33.67 kBit/s[COLOR="Red"] minimum, in the observed period[/COLOR]
Max: 0.28 kBit/s[COLOR="Red"] maximum... idem[/COLOR]
Ttl: 14.34 GByte[COLOR="Red"] total volume transfered... [/COLOR]
Outgoing:[COLOR="Red"]outgoing traffic:[/COLOR]
Curr: 56.29 kBit/s [COLOR="Red"] (the rest as before)[/COLOR]
Avg: 56.24 kBit/s
Min: 44.77 kBit/s
Max: 79.67 kBit/s
Ttl: 982.78 MByte

---

### Post by newn on 2011-02-09
Thanks. The internet connection's upload speed seems to be VERY slow...

---

