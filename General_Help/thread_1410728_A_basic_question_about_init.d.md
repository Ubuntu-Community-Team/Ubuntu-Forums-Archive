---
title: "A basic question about init.d"
date: 2010-02-19
forum: General Help
---

### Post by satnelav on 2010-02-19
Sorry I'm asking it here, but I was unable to google an answer in 20 minutes. 

I can start cups with 

sudo/etc/init.d/cups start,

but cups does not start at startup. Probably I have disabled it some point in the past. What should I do to make it autostart?

THANKS

---

### Post by sisco311 on 2010-02-19
What's the output of:
```
ls /etc/rc*.d/*cups
```
?

---

### Post by satnelav on 2010-02-19
```
/etc/rc1.d/K80cups  /etc/rc3.d/S50cups  /etc/rc4.d/S50cups  /etc/rc5.d/S50cups

```

So I just did

```
sudo ln -s ../init.d/cups S50cups 
```

in /etc/rc2.d 
and I hope this is it?

---

### Post by chuina on 2010-02-19
I'm using this with **sysv-rc-conf**

To install it
```
sudo apt-get install sysv-rc-conf
```

To see the services
```
sudo sysv-rc-conf --list
```

To turn on **cups**
```
sudo sysv-rc-conf cups on
```

Similarly use **off** to turn off any unwanted service.

---

### Post by sisco311 on 2010-02-19
> **satnelav said:**
> ```
/etc/rc1.d/K80cups  /etc/rc3.d/S50cups  /etc/rc4.d/S50cups  /etc/rc5.d/S50cups

```

So I just did

```
sudo ln -s ../init.d/cups S50cups 
```

in /etc/rc2.d 
and I hope this is it?

Yep, that should work.

---

### Post by cong06 on 2010-02-19
> **sisco311 said:**
> What's the output of:
```
ls /etc/rc*.d/*cups
```
?

I'm sorry, this is a bit off topic. I'm just amazed I only now realized I could do double *'s in an ls command...
It's like a whole new world of possibilities are open.

---

