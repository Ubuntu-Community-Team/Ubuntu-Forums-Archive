---
title: "lirc mode2 not working"
date: 2011-07-02
forum: General Help
---

### Post by satish_j on 2011-07-02
mode2,used for testing remotes is not working at my end
I ran 
```

sudo modprobe lirc_serial

```
this creates file /dev/lirc0
If i now run
```

sudo mode2 -d /dev/lirc0

```
it just gives me a blinking cursor..pressing buttons on remote does not spit anything at command.
THis same remote is working fine in Windows..
i learned that mode2 is the basic test to check remotes.if it is not working,any further tries with tvtime/mythtv is of no use.
Any ideas ho do i get it working??

---

