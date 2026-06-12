---
title: "network driver, card not loading"
date: 2010-08-05
forum: General Help
---

### Post by ryadav on 2010-08-05
i had put my kubuntu to sleep on ram, when i powered up again i lot power, now when i boot into kubuntu i have no network

if i do an ifconfig i don't see eth0 anymore

also sudo ifup eth0 returns an error saying, 'ignoring unknown interface'

how can i fix this?

---

### Post by Ozymandias_117 on 2010-08-05
Try ```
lspci | grep net
``` and see if your network card is there.

---

### Post by ryadav on 2010-08-05
yes it returns
[B]
00:0a.0 Ethernet controller" nVidia Corporation MCP67 Ethernet (rev a2)[/B]

I got a dual boot system and network is working for my WinXP

so what do I need to do to get network working again? did the network somehow get disabled?

---

### Post by Ozymandias_117 on 2010-08-05
The only advice I can offer, is to try ```
sudo /etc/init.d/networking restart
```
then see if ```
sudo ifconfig eth0 up
``` works.

---

### Post by ryadav on 2010-08-05
i now see eth0, but only for inet6, nothing for inet so still no network access, but looks promising

for the lo interface i see inet set to 127.0.0.1

so the next step is to get an inet addy for eth0 i am guessing, i am connected to a route using dhcp

still i can't log into router 192.168.1.1 either

---

### Post by ryadav on 2010-08-05
[B]i ran the following command 

sudo ifconfig eth0 192.168.1.103 netmask 255.255.255.0 broadcast 192.168.1.255

but still i get no network access? 

i can ping 192.168.1.1 but i can't ping other PC on the LAN? also I cannot log into 192.168.1.1 using a web browser??
[/B]

---

### Post by Ozymandias_117 on 2010-08-05
You'll still need to set up the gateway to access websites. 

```
sudo route add default gw 192.168.1.1
```

---

### Post by ryadav on 2010-08-06
i have network access again, however i had to reinstall firefox and now the browser is working, thank you for your help, it was awesome, you are awesome :)

seems like my DVD is really dead i can't see it from my WinXP, however using synaptic i would like to reinstall the core system do you have any suggestion what I should do just to repair any damages

thanks again!

---

### Post by ryadav on 2010-08-06
alright something is really messed up bad, no thanks to the sleep to ram crash, i've managed to get my DVD back to life...firefox stops working after each reboot and needs to be reinstalled to work!

i am going to reinstall kubuntu 10.04 again, but thanks for your help i learned new networking admin so not all was lost...in the end i was not able to save my system and i don't feel right not knowing what else is messed up

i will give rescue a broken system a go first, i hope that fixes the issues i am seeing

---

### Post by Ozymandias_117 on 2010-08-06
Either try opening firefox from a terminal so it will give you some output, or, after trying to open it type ```
dmesg
``` into a terminal. Give me a few minutes and I'll see if I can find a firefox log file somewhere.

---

### Post by Ozymandias_117 on 2010-08-06
Another thing to try is ```
firefox -safe-mode
``` in a terminal. This will verify that the problem isn't caused by an extension theme etc.

---

