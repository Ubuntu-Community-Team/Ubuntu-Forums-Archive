---
title: "is it even possible to have a wireless usb connection?"
date: 2010-07-26
forum: General Help
---

### Post by FresnoFightFan on 2010-07-26
i have u-verse and there modem is wireless. i have a wireless usb adapter that works with my xp but not my 10.04. i plug it in and it doesn't detect anything. am i screwed  or is there hope?

---

### Post by Brannyh on 2010-07-26
YES! Just not all wireless USB's are supported, so you may need a driver which isn't included with 10.04.

---

### Post by Brannyh on 2010-07-26
so there is a slim amount of hope

---

### Post by FresnoFightFan on 2010-07-26
> **Brannyh said:**
> YES! Just not all wireless USB's are supported, so you may need a driver which isn't included with 10.04.

it's a Zonet ZEW2545 if that helps. i can't find anything yet.

---

### Post by Brannyh on 2010-07-26
Looks like you can try running some commands in the terminal, check out this link

[http://ubuntuforums.org/showthread.php?t=1313516termanal]("http://ubuntuforums.org/showthread.php?t=1313516")

---

### Post by MaxIBoy on 2010-07-26
Depends on the specific one. For example, the Dlink ones supposedly work but I couldn't get them to. 

I have no experience with the specific hardware you mention, but try ndiswrapper?
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by FresnoFightFan on 2010-07-27
> **MaxIBoy said:**
> Depends on the specific one. For example, the Dlink ones supposedly work but I couldn't get them to. 

I have no experience with the specific hardware you mention, but try ndiswrapper?
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)


i was looking into this method and there isn't a 10.04 supported ndiswrapper. am i sol or could 9.10 possibly work?

---

### Post by MaxIBoy on 2010-07-29
The older package will probably still work just fine.

---

