---
title: "changing serial port speed"
date: 2010-04-16
forum: General Help
---

### Post by madaptive on 2010-04-16
Hi,

Could you please tell me how to change the speed for my serial port.  My stty output is:

speed 38400 baud; line = 0;
eol = M-^?; eol2 = M-^?; swtch = M-^?;
ixany iutf8

and I would like to change the speed to 9600.

Thanks,

---

### Post by HermanAB on 2010-04-16
Minicom or Cutecom.

---

### Post by dcstar on 2010-04-17
> **madaptive said:**
> Hi,

Could you please tell me how to change the speed for my serial port.  My stty output is:

speed 38400 baud; line = 0;
eol = M-^?; eol2 = M-^?; swtch = M-^?;
ixany iutf8

and I would like to change the speed to 9600.

Thanks,

```
man stty
```

---

### Post by wirelessmonkey on 2010-04-17
What Herman said, plus gtkterm.

---

