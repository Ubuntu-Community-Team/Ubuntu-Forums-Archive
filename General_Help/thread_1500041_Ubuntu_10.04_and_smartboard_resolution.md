---
title: "Ubuntu 10.04 and smartboard resolution"
date: 2010-06-02
forum: General Help
---

### Post by Jforce93 on 2010-06-02
High everyone,

I am trying to get my ibook running ubuntu to work with a smartboard projector. The projectors resolution is 768x1024. How would I get this to work? I already tried this:

```
jforce@ubuntu:~$ cvt 768 1024
# 768x1024 59.94 Hz (CVT) hsync: 63.72 kHz; pclk: 65.25 MHz
Modeline "768x1024_60.00"   65.25  768 816 896 1024  1024 1027 1037 1063 -hsync +vsync
jforce@ubuntu:~$ xrandr --newmode "768x1024_60.00"   65.25  768 816 896 1024  1024 1027 1037 1063 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  25
  Current serial number in output stream:  25
jforce@ubuntu:~$ 

```

Thanks,

Jordan

---

