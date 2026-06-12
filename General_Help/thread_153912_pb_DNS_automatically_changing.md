---
title: "pb: DNS automatically changing"
date: 2006-04-02
forum: General Help
---

### Post by jude999 on 2006-04-02
Hi all
Since ever my internet was extremely slow, time-outing all the time making it a real pain to surf.
Thanks to this forum, i think I found what the problem was:
when I add the DNS addresses I find on my router to etc/resolv.conf, my internet flies and its great.
But after a minute or 2, my internet speed goes back to where it was, so I open my resolve.conf again... and the DNS I added dissapeared!

So my question is: how can I make the changes in my resolve.conf definitive?

My resolv.conf looks like this after I change it:
```
search domain
nameserver 202.106.0.20
nameserver 202.106.46.151
nameserver 202.96.128.68
nameserver 202.96.134.188
nameserver 202.96.134.133
nameserver 192.168.1.1
```

and it goes back to this after a short while:
```
search domain
nameserver 202.96.128.68
nameserver 202.96.134.188
nameserver 202.96.134.133
nameserver 192.168.1.1
```

I need those 2 DNS permanantly! Help!

---

### Post by dcstar on 2006-04-02
[QUOTE=jude999]Hi all
Since ever my internet was extremely slow, time-outing all the time making it a real pain to surf.
Thanks to this forum, i think I found what the problem was:
when I add the DNS addresses I find on my router to etc/resolv.conf, my internet flies and its great.
But after a minute or 2, my internet speed goes back to where it was, so I open my resolve.conf again... and the DNS I added dissapeared!
........
I need those 2 DNS permanantly! Help![/QUOTE]
If you use DHCP, then the DHCP server will overwrite you own DNS entries.

If that is the case, set up a Static IP with all the settings done manually.

---

### Post by jude999 on 2006-04-02
[QUOTE=dcstar]If you use DHCP, then the DHCP server will overwrite you own DNS entries.

If that is the case, set up a Static IP with all the settings done manually.[/QUOTE]

Ok, thanks.
How do I know what my gateway address is ?

---

### Post by dcstar on 2006-04-02
[QUOTE=jude999]Ok, thanks.
How do I know what my gateway address is ?[/QUOTE]
```
route -n
```

---

### Post by jude999 on 2006-04-02
[QUOTE=dcstar]```
route -n
```[/QUOTE]

Ya... I just found out that was probably the stupidest question I asked in a long time.
Thanks, it seems to be working like a charm.

---

