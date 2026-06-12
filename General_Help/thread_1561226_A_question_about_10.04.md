---
title: "A question about 10.04"
date: 2010-08-26
forum: General Help
---

### Post by markinmadison on 2010-08-26
I am just full of posts tonight. LOL Ok, I am running Ubuntu 9.10 and 10.04 side by side. I am on a wireless router for internet connection. Ubuntu 9.10 sees my wireless connection. When I reboot and go into the 10.04 Ubuntu, it doesn't see my wireless connection. Is there a setting that I am missing? :popcorn:

Thanx for all your help!!!

---

### Post by wojox on 2010-08-26
So do you have to click and connect the icon yourself to connect?

Does the icon show up?

Could you elaborate, please?

---

### Post by markinmadison on 2010-08-26
No, When I go to connect manually, there is nothing that says that I have wireless in 10.04. When I go back into 9.10 it connects automatically and when I click the icon, I can see all of the other wireless networks too. I live in a large apartment complex with alot of other people that have wireless also. :KS

---

### Post by wojox on 2010-08-26
You checked Hardware Drivers and you wireless driver is activated?

What does this tell you?

```
ifconfig
```

---

### Post by markinmadison on 2010-08-26
I am on the same computer with the 9.10 and 10.04. It is just that 10.04 doesn't see the wireless.

---

### Post by TheWeakSleep on 2010-08-26
Just because your wireless is working in 9.10 doesnt mean that you have the driver for your wireless card in 10.04.

Did you try opening 'Hardware Drivers' under System --> Administration?

if theres nothing there, could you post the output of
```
sudo lshw -C network
```

thanks

---

