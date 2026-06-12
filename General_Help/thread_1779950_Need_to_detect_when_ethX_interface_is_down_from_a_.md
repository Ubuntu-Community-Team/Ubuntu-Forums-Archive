---
title: "Need to detect when ethX interface is down from a bash script."
date: 2011-06-11
forum: General Help
---

### Post by s.v.z on 2011-06-11
Hi guys! I'm trying to write a small script and there's one part of it that makes me sick:

```
ifconfig eth$num down
sleep 6
ifconfig eth$num hw ether $mac
ifconfig eth$num up
```

The problem is that the ethX interface doesn't go down immediately after the first line is executed. So sometimes the change of MAC is called while ethX is up, no matter how big is the sleep time, which results in an error. Is there a way to make this work right?

---

### Post by tredegar on 2011-06-11
Try ```
cat /sys/class/net/eth0/operstate
```

---

