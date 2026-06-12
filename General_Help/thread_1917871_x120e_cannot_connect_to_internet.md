---
title: "x120e cannot connect to internet"
date: 2012-01-30
forum: General Help
---

### Post by squelchy451 on 2012-01-30
Hi. I have a Lenovo x120e and i just installed xubuntu on it. Xubuntu recognizes the wifi card and shows the wireless network at my house as within range with good signal. However, it cannot connect.

I tried installing the Realtek driver, but failed because I don't know how to install the .sh files.

What should i do?

---

### Post by Jose Catre-Vandis on 2012-02-01
Assuming the realtek driver is installed via a .sh file and is in your home directory, open a terminal from your home directory and type as follows:

```
sudo ./driver.sh
```
(enter password as required and replace "driver" with name of .sh file)

---

