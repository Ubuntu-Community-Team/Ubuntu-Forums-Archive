---
title: "ATI drivers problem....!!!!!!"
date: 2009-07-06
forum: General Help
---

### Post by kuldeepsidhu on 2009-07-06
I am running 8.04 before and i hv installed ATI drivers in it..

now i am running 9.04 when i select hardware drivers from sysem menu..it says no drivers for hardware...

how can i install drivers for ATI card...??

---

### Post by b@sh_n3rd on 2009-07-06
Hi there, ATI seems to have a couple of probs when it comes to Linux, but then again it depends on the card. First, what's the card you use? Try the following code in a terminal to find out.
```
# lspci | grep VGA
```

---

### Post by chriskin on 2009-07-06
> **kuldeepsidhu said:**
> I am running 8.04 before and i hv installed ATI drivers in it..

now i am running 9.04 when i select hardware drivers from sysem menu..it says no drivers for hardware...

how can i install drivers for ATI card...??


try their site, you can get them from there.

---

### Post by kuldeepsidhu on 2009-07-06
```
sidhu@sidhu-desktop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
sidhu@sidhu-desktop:~$ 

```


this is the output for tthe above command..?how to insatll it...?


i hv checked the ati site..i dont find any drivers for this series..plz give me the link to download...

---

### Post by alphacrucis2 on 2009-07-06
> **kuldeepsidhu said:**
> ```
sidhu@sidhu-desktop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
sidhu@sidhu-desktop:~$ 

```


this is the output for tthe above command..?how to insatll it...?


i hv checked the ati site..i dont find any drivers for this series..plz give me the link to download...

Forget it. If ATI have sent your card to the legacy bin then you have no choice but to use one of the open source drivers (either radeonhd or ati depending on your card). ATI's Catalyst drivers older than 9.4 don't work with the version of X server in Jaunty.

[Explanation]("http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1")

---

### Post by kuldeepsidhu on 2009-07-06
now how can i insatll drivers....?

---

### Post by alphacrucis2 on 2009-07-06
> **kuldeepsidhu said:**
> now how can i insatll drivers....?

[This should help]("https://help.ubuntu.com/community/RadeonDriver")

---

