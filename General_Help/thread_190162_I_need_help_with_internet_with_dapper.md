---
title: "I need help with internet with dapper"
date: 2006-06-05
forum: General Help
---

### Post by novik420 on 2006-06-05
Hi i have jsut recently upgrading to the recent dapper version of ubuntu and i use a lynksys router and a cable one modem and dapper is not recoognizing my ethernet card can anyone help me with this?

---

### Post by kb3hkg on 2006-06-05
to start can you run ifconfig and post the results

---

### Post by HankB on 2006-06-05
It would probaly help to know what kind of ethernet hardware you have and perhaps what kind of computer.

Can you run ```
dmesg|grep eth
```
and paste the output here?

Also check "System -> Administration -> Networking" and see what interfaces your configuration thinks it has.

Also the output of ```
ifconfig
``` might be useful.

Is this WiFi?

-hank

---

