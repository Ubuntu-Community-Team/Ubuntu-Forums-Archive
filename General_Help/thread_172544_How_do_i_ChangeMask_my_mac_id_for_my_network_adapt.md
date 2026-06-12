---
title: "How do i Change/Mask my mac id for my network adapter"
date: 2006-05-08
forum: General Help
---

### Post by cowlikk on 2006-05-08
i was just wondering if anyone can help me mask my mac id!! i am in a motel and there router keeps blocking my mac id so i have to mask it to a new one for it to work right!! any help is apreciated!!

---

### Post by bobpaul on 2006-05-08
I know how to do it on my router and in windows, but not normally in linux. I would [start with google.]("http://www.google.com/search?q=linux+spoof+mac+address")

Actually, first I would probaby stop doing whatever you are doing that makes them want to block your access. Sure you aren't violating their TOS?

---

### Post by stoic jed on 2006-05-08
There is an easy command-line tool called macchanger.

```
sudo apt-get install macchanger
```

The following command would assign a random mac address to the interface ath0 (replace with your interface name).

```
macchanger -A ath0
```

---

### Post by cowlikk on 2006-05-13
Thank you all i also found this

```
sudo ifconfig eth0 hw ether xx:xx:xx:xx:xx:xx
```

---

