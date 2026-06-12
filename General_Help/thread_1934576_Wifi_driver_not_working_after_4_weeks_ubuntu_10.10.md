---
title: "Wifi driver not working after 4 weeks ubuntu 10.10"
date: 2012-03-02
forum: General Help
---

### Post by muhammed irshad on 2012-03-02
I have installed ubuntu 10.10 in ma dell laptop and i have 

Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] wireless card .After few weeks ma wifi is not working. I have'nt done anything which effects my driver. Why it happens anybody  please reply

---

### Post by BJCV86 on 2012-03-02
> **muhammed irshad said:**
> I have installed ubuntu 10.10 in ma dell laptop and i have 

Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] wireless card .After few weeks ma wifi is not working. I have'nt done anything which effects my driver. Why it happens anybody  please reply

Does your network card work in other computers? Is I think one of the first questions to ask and is a way to make sure the card is functional. And if functional, maybe someone else can help. I am not a Linux Pro.

---

### Post by josephmills on 2012-03-02
> **muhammed irshad said:**
> I have installed ubuntu 10.10 in ma dell laptop and i have 

Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] wireless card .After few weeks ma wifi is not working. I have'nt done anything which effects my driver. Why it happens anybody  please reply
most the time with the broadcom cards it is the firmware that messes up could you please open your terminal (ctrl+alt+t) 
and enter in 

```
dmesg | grep b43 
```

then 
```
lsmod
```
then 
```
rfkill list all 
```

then paste here thanks

---

### Post by muhammed irshad on 2012-04-10
I have changed my ubuntu to 10.04 lts to solve this. In this i have installed b43 driver via its additional driver utility.It was working fine.But recently it shows the wireless network available.But cant connect to ma wireless network.Help me please.

---

### Post by jadtech on 2012-04-10
make sure your wirless is not disabled  usually f2 key toggle enable disable

---

### Post by muhammed irshad on 2012-04-11
thanx all for the reply
f2key is not the problem.When i start ubuntu it shows connection established,But i cant use it.After some time it keeps loading and asking the security key again and again.I cant connect to ma network even though i have entered it correct.

---

### Post by josephmills on 2012-04-11
> **josephmills said:**
> most the time with the broadcom cards it is the firmware that messes up could you please open your terminal (ctrl+alt+t) 
and enter in 

```
dmesg | grep b43 
```

then 
```
lsmod
```
then 
```
rfkill list all 
```

then paste here thanks

 LP-PHY   low powered card I am betting that you have the wrong firmware loaded ?  This is a common thing.




you can read more about b43 drivers here make sure you check out the section LP-PHY 
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by muhammed irshad on 2012-04-20
Thanks Josephmills for your reply i will paste the output here
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

