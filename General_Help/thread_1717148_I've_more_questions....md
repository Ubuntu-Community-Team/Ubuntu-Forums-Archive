---
title: "I've more questions..."
date: 2011-03-29
forum: General Help
---

### Post by PCaddicted on 2011-03-29
Hello,
[LEFT]I've managed to solve that problem where Ubuntu didn't allow me to install anything(see[http://ubuntuforums.org/showthread.php?t=1714424&highlight=can%27t+install+anything%2CUbuntu+app+untrusted!!!) ]("http://ubuntuforums.org/showthread.php?t=1714424&highlight=can%27t+install+anything%2CUbuntu+app+untrusted%21%21%21")but I have more questions to ask about the Maverick Meerkat.
1.This OS seems to be equiped with some kind of IPS(intrusion-prevention system) because it prompts for the administrator password when someone/something tries to do an important change to the system.This thing is useful,but how effective is it against Linux viruses?
2.Are there any standalone Linux firewalls compatible with Ubuntu 10.10?Or does this OS need a firewall?
3.I set 2 keyboard configurations(by language):the USA configuration and another one(I'd like to keep it secret,so I'll call it the X configuration).I usually keep the USA config turned on(I rarely use the second configuration,but not never),but sometimes the X config turns on automatically,which is very annoing.I press a key on the keyboard to get a specific character,but I see another character in the field!Then I turn the USA config on again,but later the X config turns on without my consent!Again and again!How do you explain this?Any solution?
Please answer all my questions.
[/LEFT]

---

### Post by seawolf167 on 2011-03-29
> **PCaddicted said:**
> 1.This OS seems to be equiped with some kind of IPS(intrusion-prevention system) because it prompts for the administrator password when someone/something tries to do an important change to the system.This thing is useful,but how effective is it against Linux viruses?
[LEFT] 
There are no linux virsus' in the wild to worry about. The password is to ensure that you know what that you are doing is something that could decrease functionality of your computer if you set it incorrectly.


> **PCaddicted said:**
> 2.Are there any standalone Linux firewalls compatible with Ubuntu 10.10?Or does this OS need a firewall?

Ubuntu's firewall (IPTables) is disabled (has no entries) by default. You can add IPTables entries manually or use a GUI to help you. I recommend

```
sudo apt-get install gufw
```> **PCaddicted said:**
> 3.I set 2 keyboard configurations(by language):the USA configuration and another one(I'd like to keep it secret,so I'll call it the X configuration).I usually keep the USA config turned on(I rarely use the second configuration,but not never),but sometimes the X config turns on automatically,which is very annoing.I press a key on the keyboard to get a specific character,but I see another character in the field!Then I turn the USA config on again,but later the X config turns on without my consent!Again and again!How do you explain this?Any solution?
Please answer all my questions.


[/LEFT]
 Not sure about the specific solution to this, but it sounds as if the default keyboard is set to your other language, so you login in by selecting the English layout, the whenever x-config restarts you get your default keyboard layout. You might start by ensuring you have the correct entries under

```
gedit /etc/X11/xorg.conf.d/30-keyboard.conf
```

---

