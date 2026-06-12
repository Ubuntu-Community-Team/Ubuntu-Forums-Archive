---
title: "Problems with Wifi"
date: 2011-03-21
forum: General Help
---

### Post by hijiz on 2011-03-21
A few days  ago i noticed i couldnt connect to my own wifi network. surprisingly i found no problem conecting to my neighbors network. today the problem persisted so i decided to change my driver. to my suprise none of the two available drivers were activated so i tried activiting the one i was previusly using broadcom B43 wireless driver. however if i try to activate either it download only about 50% and then says> SystemError: installArchives() failed please help and fyi yes i am trying to activate the driver through a wired network.

---

### Post by pqwoerituytrueiwoq on 2011-03-21
if it works on another network i don't see how its the drivers fault
check your wifi settings (router/computer)

---

### Post by 5149.5 on 2011-03-21
Open a terminal and enter: nm-tool. Paste the output in a post.

---

### Post by hijiz on 2011-03-21
Maybe i'll check it out but how do you explain the fact that neither of my drivers are activated and cant be activated

---

### Post by hijiz on 2011-03-21
this is the out put of nm-tool
> NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        00:26:22:13:CF:C3

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.13
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             190.157.2.140
    DNS:             200.118.2.91


---

### Post by wojox on 2011-03-21
> **hijiz said:**
> Maybe i'll check it out but how do you explain the fact that neither of my drivers are activated and cant be activated

Do you have more than one package manager open?

---

### Post by hijiz on 2011-03-21
no only aditional drivers

---

### Post by 5149.5 on 2011-03-21
It doesn't look like wireless is running. What does the output of iwconfig look like?

---

### Post by hijiz on 2011-03-21
> lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.



However i turned it off myself after encountering the problem but now i cant turn it on

---

### Post by hijiz on 2011-03-21
i tried once more to install the driver and it finally worked:D however i still cant connect to my own network so can sombody explain me wats wrong and how to fix it.

---

### Post by hijiz on 2011-03-21
never mind aparently the password i used had a spelling mistake and i fixed i am so sorry i was ted your time.:(

---

