---
title: "problem connecting to cisco device with gtkterm"
date: 2010-03-19
forum: General Help
---

### Post by Mia_tech on 2010-03-19
guys, this are my tty

```
dmesg | grep tty
[    0.002489] console [tty0] enabled
[    0.956262] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.956684] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

```

I configured /dev/ttyS0 in port setting in gtkterm, but I get error "Cannot open /dev/ttyS0 : No such device or address" yes I'm opening the terminal as ```
sudo gtkterm
```

any help appreciated

---

### Post by Mia_tech on 2010-03-19
I've also tried with miniterm with same results. So I booted off ubuntu livecd and installed minicom, and this time it worked... so I wonder what's wrong with my install?

---

