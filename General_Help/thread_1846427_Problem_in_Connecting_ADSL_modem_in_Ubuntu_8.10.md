---
title: "Problem in Connecting ADSL modem in Ubuntu 8.10"
date: 2011-09-19
forum: General Help
---

### Post by arka.sharma on 2011-09-19
Hi,

 I am using ubuntu 8.10 and I'm having a broadband connection of airtel which provides a wired ADSL modem.I connect my modem in windows 7 with lan cable and dhcp.I tried to do the same in ubuntu by connecting the lan cable to serial port and then tried to run dhclient.After a while it shows "no working leases in persistent database sleeping".Then I discovered that no light is blinking in the serial port where I connect the lan cable.Please provide any solution.

Thanks & Reards,
Arka

---

### Post by uncontrolable™ on 2011-09-19
8.10 is no longer supported. Have your tried installing a newer version such as 10.04 Long Term Support? Chances are that it may offer better support for your hardware.

---

### Post by arka.sharma on 2011-09-19
I only have 8.10.Once I successfully connect to internet I will upgrade it.Now at this point my goal is to connect my pc with internet.I also have windows 7 installed.In windows 7 my modem connects fine without any issue.

---

### Post by uncontrolable™ on 2011-09-19
You won't be able to upgrade. The next two subsequent releases(9.04 & 9.10) have hit end of life as well, but best of luck to you if you prefer to use 8.10.:)

---

### Post by arka.sharma on 2011-09-19
Previously I used to connect with bsnl dsl modem using ppp without any problem.However since now I'm facing this issue what are suggestions are you providing ?

---

### Post by dineshs on 2011-09-19
Please post the result of the following command (applications-accessories-terminal)```
sudo lshw -C network
```When your cable is connected

---

### Post by arka.sharma on 2011-09-20
Problem is that the modem is not being connected via lan.It is not blinking any light in the lan port of my laptop.

---

