---
title: "Drivers for graphics card / chipset"
date: 2012-08-25
forum: General Help
---

### Post by Robert R on 2012-08-25
Hi all,
           I currently have a  dell vostro 1510 running ubuntu 12.04 lts, what command or tool can i use to find out what graphics card/chipset (most likely intel) i am running and how can i get ubuntu drivers for this. 

I am asking because my display fails terribly at times when running anything requiring intense graphics. i know its not the chipset because it runs fine under windows. 

But dell only provides drivers for windows. 

Any suggestions? 
Thanks.

---

### Post by bogan on 2012-08-25
Hi!,** Robert R**,

In a Terminal enter:```
 lspci -nnk |grep -iA3 VGA
```This will tell you the Video card and the driver & kernal module in use.

How to get other drivers depends on the card, but System Settings>Additional Hardware may tell you what is available. Post the output of the above command and more detailed advice will, I am sure, be forthcoming.

For the chipset you probably need to use:```
 sudo lshw
```But which bit of the mass of output is what you want, I can not tell you.
[B]
Edit:[/B] Running:> /usr/lib/nux/unity_support-test -pWill tell if your graphics capabilty is OK with the drivers you have installed.

Chao!, **bogan.**

---

### Post by Robert R on 2012-08-25
Thanks bogan,
This is the piece of output that i required 

Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller

Can you tell me how one would go about installing a driver for this.

---

### Post by bogan on 2012-08-25
Hi!, **Robert R**,

I edited my Post: Please post the lspci output.

There should be a default driver included in the 12.04 installation, check Additional Hardware for any others available.

Chao!. **bogan.**

---

### Post by Robert R on 2012-08-25
This is the output: 

lspci -nnk |grep -iA3 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
    Subsystem: Dell Device [1028:0273]
    Kernel modules: intelfb, i915
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)

This is what happened with the other command

rob@robuntu:~$  /usr/lib/nux/unity_support-test -p 
bash: /usr/lib/nux/unity_support-test: No such file or directory
rob@robuntu:~$ cd /usr/lib/nux/unity_support-test -p 
bash: cd: /usr/lib/nux/unity_support-test: No such file or directory
rob@robuntu:~$ cd /usr/lib/nux/
rob@robuntu:/usr/lib/nux$ unity_support-test -p 
unity_support-test: command not found
rob@robuntu:/usr/lib/nux$

---

### Post by bogan on 2012-08-25
Hi!,** Robert R,**

Right, as far as I am aware, the i915 driver is the correct one for your card.

Does Additional Drivers show anything else?

You might try Intel download center, which has an auto scan function, though I do not know if it has any support for Linux installations.
[http://downloadcenter.intel.com/](http://downloadcenter.intel.com/)

It shows a Linux graphics driver for your card but does not state a version number. I have not tried to download it, and have no idea what procedure would be needed to install it. Good Luck!

EDit: Sorry for the typo, the test cmd should be :
 > /usr/lib/nux/unity_suppo[COLOR=Black]r[/COLOR][COLOR=Red][COLOR=Black]t[/COLOR]_[/COLOR]test -p  

Chao!, **bogan**

---

### Post by Cheesemill on 2012-08-25
You already have the correct driver installed (i915), it comes with Ubuntu.

If there are any updates to it they will be installed as part of the normal system update process.

---

### Post by Robert R on 2012-08-25
ok thanks will take a look at the documentation

---

