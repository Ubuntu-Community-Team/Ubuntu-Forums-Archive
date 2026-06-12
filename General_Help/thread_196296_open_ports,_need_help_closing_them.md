---
title: "open ports, need help closing them"
date: 2006-06-14
forum: General Help
---

### Post by erimar77 on 2006-06-14
I have a few open ports and would like to know either what they're used for, or how I can close them.. I know the hplip is for the printing, but the others for my user i have no clue..


```
$ cat /proc/net/tcp |perl -lane '(undef,$p)=split ":",$F[1]; print hex($p)."\t".getpwuid($F[7]) if $p'|sort -n|uniq -c
      1 631     root
      1 1002    root
      1 33058   hplip
      1 33796   hplip
      1 34414   eric
      1 38803   eric
      1 41263   eric
      2 50438   hplip
      1 52157   eric
```

---

### Post by DarthMandeep on 2006-06-14
Are these ports open to the network, or only to the localhost? If you're running a firewall like Firestarter and no ports are open in that, then nobody outside your computer is going to connect.

If you're really concerned about open ports, setup a firewall and run an nmap port scan from another computer on the network to test it.

Things like X use the localhost connection, and I'm sure other apps do too, so you'll always have used ports on the localhost.

---

