---
title: "bcm43xx_microcode4.fw not loading"
date: 2006-05-08
forum: General Help
---

### Post by cvmostert on 2006-05-08
Hi there,

I installed the updates as usual in Dapper and had to restart, but then my wlan would not work.

I did a lsmod and saw that my broadcom modules did not load completely.

i got the error that bcm43xx_microcode4.fw was not found or could not be loaded? what file is a .fw and how do n start to solve the problem

Any help would be greatly appreciated.

I will try to unprobe and reprobe the bcm43xx modules.

Thank you in advance!

---

### Post by the_tiger on 2006-05-08
A .fw file is a firmware file. They can be found in /lib/firmware.

There is a wiki for the bcm43xx drivers here

[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?highlight=%28bcm43xx%29]("https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?highlight=%28bcm43xx%29")

---

### Post by cvmostert on 2006-05-08
thank you will try it.. am trying with ndiswrapper aswell..

i think that there must have gone something wrong with my update this morning.

dont know. thanx anyway

Edit: I used ndiswrapper and it seems to work. now i must just make the bcm43xx NOT startup when i boot! :-)

---

### Post by the_tiger on 2006-05-08
This used to be in the wiki. For some reason it has disappeared but I am going to put it back.

If you've upgraded and your internet is broken, and you use a broadcom 43xx card, and you would like to still use ndiswrapper (because it was working, and you want it to remain working), simply do:

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

---

