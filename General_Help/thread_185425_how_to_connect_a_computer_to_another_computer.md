---
title: "how to connect a computer to another computer"
date: 2006-05-31
forum: General Help
---

### Post by tomslopez on 2006-05-31
I have an HP computer and I´m using ubuntu and I want to connect it to another computer that has windows xp installed, using an ethernet cable without having to connect either computer to the internet, how can I do that if its possible.

---

### Post by deja2004 on 2006-05-31
The easiest way is to purchase a crossover cable and connect them directly. Within Windows, be sure to set the IP to something along the lines of "192.168.1.x" with the default gateway at "255.255.255.0". On the linux machine, do the same, setting the IP, however, to "192.168.1.y". For x and y any number between 0 - 255 will be fine. From there, you should be able to ping the connected machine.

---

### Post by brsseb on 2006-05-31
You need either:

1x switch ($20 or so)
2x CAT5 cables (normal onces)

OR

1x crossed cat5-cable (two-way cable)

---

### Post by nanotube on 2006-05-31
[QUOTE=deja2004]The easiest way is to purchase a crossover cable and connect them directly. Within Windows, be sure to set the IP to something along the lines of "192.168.1.x" with the default gateway at "255.255.255.0". On the linux machine, do the same, setting the IP, however, to "192.168.1.y". For x and y any number between 0 - 255 will be fine. From there, you should be able to ping the connected machine.[/QUOTE]

well, that's the second easiest way. the first easiest it to plug them both into a router box (but not have router plugged to a net uplink, so it all stays local). the router will assign ip addresses via dhcp, and then you can go ahead and connect from one to the other.

but if you have no router box on hand, then the crossover cable is the way to go. and if you /really/ dont want to spend any money, take a regular ethernet cable that you can afford to "lose", cut it open, and splice the wires to make a crossover cable. you can find instructions for that on the net. that's how i came to have my crossover cable. ;)

---

### Post by nanotube on 2006-05-31
[QUOTE=brsseb]You need either:

1x switch ($20 or so)
2x CAT5 cables (normal onces)

OR

1x crossed cat5-cable (two-way cable)[/QUOTE]
maybe i'm missing something, but how would you do it with just two ethernet cables? or do you mean, 2 cables + switch, not 2 cables by themselves?

---

### Post by deja2004 on 2006-05-31
I stand corrected :-)

---

### Post by elamericano on 2006-05-31
[QUOTE=nanotube]maybe i'm missing something, but how would you do it with just two ethernet cables? or do you mean, 2 cables + switch, not 2 cables by themselves?[/QUOTE]

Clearly he means 2 normal cables and a switch or hub.

---

### Post by tomslopez on 2006-05-31
where do I go to set the IPs and the gateway? and does it matter which end of the cable I connect to the windows and the ubuntu? and when I connect the computers to each other does anything have to appear?

---

### Post by deja2004 on 2006-05-31
Within linux open a terminal prompt and type:
```
ifconfig eth0 192.168.1.1
```

---

### Post by 0MG on 2006-05-31
[QUOTE=deja2004]Within linux open a terminal prompt and type:
```
ifconfig eth0 192.168.1.1
```[/QUOTE]

also, he goofed when he said 255.255.255.0 should be the gateway. He meant subnet mask.

the syntax would be:

sudo ifconfig eth0 192.168.1.1 netmask 255.255.255.0

no gateway is needed if you aren't planning on going to the web.

if that is the IP you use for your ubuntu box, you can use 192.168.1.2 for your XP box. Also with a subnet mask of 255.255.255.0

---

### Post by 0MG on 2006-05-31
[QUOTE=tomslopez]where do I go to set the IPs and the gateway? and does it matter which end of the cable I connect to the windows and the ubuntu? and when I connect the computers to each other does anything have to appear?[/QUOTE]

you won't see anything, per se. Are you using a crossover cable? To test if the link is active, on your linux box go to a prompt and type:

mii-tool

this will either say 'no link' or give you info on your link.

---

### Post by deja2004 on 2006-06-02
Right, subnet, not gateway. I need to be more careful before posting...

---

### Post by tomslopez on 2006-06-06
If I change the IP and the netmask, will I be able to connect to internet using an ethernet cable later on without changing the settings again?

---

