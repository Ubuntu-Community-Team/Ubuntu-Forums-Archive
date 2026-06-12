---
title: "help please"
date: 2011-08-30
forum: General Help
---

### Post by aLiLSmurF on 2011-08-30
I`ve just installed Ubuntu on my Acer Extensa 5220 and i can`t find the driver to connect to wifi. I`m new to this and haven`t a clue how to solve it can anyone help?

Thank you.

---

### Post by decoherence on 2011-08-30
> **aLiLSmurF said:**
> I`ve just installed Ubuntu on my Acer Extensa 5220 and i can`t find the driver to connect to wifi. I`m new to this and haven`t a clue how to solve it can anyone help?

Thank you.

This is probably a common "you can't get there from here" type of situation. 

What is likely going on is that your wireless card uses a proprietary driver which can't be included in the distro. Ubuntu wants to find you a driver but it needs to connect to the internet to do so.

The solution is to hook your computer up using a cable and either wait for Ubuntu to offer you a wireless driver, or run the Hardware Drivers or Additional Drivers program (i forget what it's called) which should prompt you for it. Once that's installed, you should be able to get on your wifi.

---

### Post by bkratz on 2011-08-30
> **aLiLSmurF said:**
> I`ve just installed Ubuntu on my Acer Extensa 5220 and i can`t find the driver to connect to wifi. I`m new to this and haven`t a clue how to solve it can anyone help?

Thank you.



We need to find out what your wireless card is, please go to the terminal and enter in

```
lspci -nn | grep 0280
```

It should help us to find the correct path.

---

### Post by aLiLSmurF on 2011-08-30
I think that solved it. It`s downloading and installing Broadcom STA wireless driver on the other laptop now. 
Thank you :)

---

