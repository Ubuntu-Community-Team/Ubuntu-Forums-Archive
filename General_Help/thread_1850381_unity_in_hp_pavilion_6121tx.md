---
title: "unity in hp pavilion 6121tx"
date: 2011-09-26
forum: General Help
---

### Post by sarathsnair on 2011-09-26
i am here to get a fast help for my problem. i have an HP pavilion notebook pc DV6 6121tx. i installed ubuntu 11.04 in it. but when i restarted it says that their is no hardware to get unity so default classical desktop will appear. i didnt get unity.
my laptop has 2 graphics cards one internal and other one dedicated. how can i get unity in ma laptop and also want to know how to install proper graphics driver for my laptop. ?
i cant install visual effects such as compiz fusion in my lap because of this problem. whenevr i check for additional drivers in administration menu it says that their is no proprietary drivers are in use on this system. please help me.

---

### Post by realzippy on 2011-09-28
Guess you need to update your kernel.
Show output from

```
uname -r
```

---

### Post by sarathsnair on 2011-09-28
> **realzippy said:**
> Guess you need to update your kernel.
Show output from

```
uname -r
```

2.6.38-8-generic

---

### Post by realzippy on 2011-09-28
Run
```
gksudo software-properties-gtk
```

enable "proposed" in "updates" tab

then run those commands
```
sudo apt-get purge nvidia-current
sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
Reboot!Then:
```
sudo apt-get install bumblebee
sudo usermod -a -G bumblebee *yourusername*
```
replace yourusername in last command.
Reboot again,
then run:
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by sarathsnair on 2011-10-01
i have intel HD 3000 internal graphics and ATI 6770M dedicated graphics.
how can i install drivers for this ? is it solve my problem ?

---

### Post by realzippy on 2011-10-02
Sorry,I thought it was Nvidia.My mistake.
You have a switch in the BIOS for the graphics?

---

### Post by sarathsnair on 2011-10-02
yes dynamic and fixed. my laptop is hp pavilion dv6 6121tx and bios version is F.1A. i got visual effects in KNOPPIX when i used. but in ubuntu it does not show.

---

