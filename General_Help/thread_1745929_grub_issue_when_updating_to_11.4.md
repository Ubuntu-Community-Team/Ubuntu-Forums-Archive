---
title: "grub issue when updating to 11.4"
date: 2011-05-01
forum: General Help
---

### Post by konos on 2011-05-01
hello,
i get the following messages and i do not know how to proceed.
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible devise/file completions.

sh:grub>

pls help

what should i do??
thank you in advance

---

### Post by Rubi1200 on 2011-05-01
Hi,
when you see the prompt type > ls and tell me what it lists there please.

---

### Post by nuevouser on 2011-06-21
> **Rubi1200 said:**
> Hi,
when you see the prompt type  and tell me what it lists there please.

!! I have the same problem!!!
It comes (hd0) (hd0,5) (hd0,1)
What do we do next???
Thank U for  your help

---

### Post by idoitprone on 2011-06-22
> **nuevouser said:**
> !! I have the same problem!!!
It comes (hd0) (hd0,5) (hd0,1)
What do we do next???
Thank U for  your help

op i am using nuevouser as an example. Adjust your commands accordingly

[https://help.ubuntu.com/community/Grub2#GRUB 2 Troubleshooting Preparation](https://help.ubuntu.com/community/Grub2#GRUB 2 Troubleshooting Preparation)


```
ls (hd0,5)/boot
ls (hd0,1)/boot
```

you finding with partition has the word vmlinuz and initrd.img

```
set root=(hdX,Y)
linux /vmlinuz root=/dev/sdXY ro
initrd /initrd.img
boot

```

replace sdxy with the correct partition found with the ls (hdx,y)/boot
(hd1,5) = sdb5
(hd0,7) = sda7

i guess you get it

for example it is on (hd0,5)
```
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
```

for example it is on (hd0,1)
```
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot
```

when you are able to boot

```
sudo grub-install /dev/sda
sudo update-grub
```

---

