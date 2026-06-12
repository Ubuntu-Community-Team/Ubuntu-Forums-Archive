---
title: "unknow interface wlan0"
date: 2011-04-19
forum: General Help
---

### Post by vivek.pandey on 2011-04-19
hey  everyone
     i was trying an application through terminal but it returned following error
```

FATAL: SetIFFlags : Unknown interface wlan0 : Operations not possible due to RF-kill
done.

```
i typed iwconfig on terminal and i get besides other lines this line
```
  
wlan0   IEEE 802.11bg Mode:Monitor  Tx-Power=off
        Retry long limit :7  RTS thr:off  Fragment  thr:off
        Power Management :off

```
can anyone please suggest some solution .. i really need to solve it out... thanx to all

---

### Post by tredegar on 2011-04-19
```
wlan0   IEEE 802.11bg Mode:Monitor  [COLOR="Red"]Tx-Power=off[/COLOR]
        Retry long limit :7  RTS thr:off  Fragment  thr:off
        Power Management :off
```
The power is off. So it will not work.
Try turning it on - usually a little switch or a Fn-key combination.

---

### Post by vivek.pandey on 2011-04-19
ok the real problem was the wireless option in my network manager was not highlighted and hence not checked .. when i restarted it  i saw this time it was checked and i got a notification wireless networks available but now the point is how to enable the wireless when it is not highlighted? can someone help me with this?

---

