---
title: "Wireless network problem"
date: 2009-08-06
forum: General Help
---

### Post by razzer on 2009-08-06
Hello. i have a D-link DI-524 that i can connect to trough wireless in windows just fine, but in ubuntu i use a DWL-122 USB wireless connector since my wireless card cant be found in ubuntu. when i try to connect to my wireless network a windows pops up saying "authentication requierd" BUT here is the problem. i use WPA / WPA2 security on my router and in that windows i can only choose between WEP LEAP and dynamic WEP. why? how can i connect to my wireless???

---

### Post by synapsys on 2009-08-06
You should check and make sure wpa-supplicant is installed. If it is, chances are that the driver your using doesn't support wpa. In this case, you should use ndiswrapper with the correct driver for your wireless card.

---

### Post by razzer on 2009-08-06
> **synapsys said:**
> You should check and make sure wpa-supplicant is installed.

how do i do this and how do i install it if it's not ?

---

### Post by slakkie on 2009-08-06
aptitude search wpasupplicant

if you see i wpasupplicant it is installed, otherwise it is not.

or dpkg -l | grep wpasupplicant, you then need to see ii  wpasupplicant

---

### Post by synapsys on 2009-08-06
Or open up synaptic package manager and search for it

---

