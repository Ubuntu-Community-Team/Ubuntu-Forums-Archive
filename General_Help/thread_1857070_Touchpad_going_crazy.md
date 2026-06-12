---
title: "Touchpad going crazy"
date: 2011-10-09
forum: General Help
---

### Post by black.sfcro on 2011-10-09
I am using Ubuntu 11.04 (dual boot Vista/Ubuntu) on Acer 5310.

Touchpad is going crazy. Pointer just jumps arround the screen. I tried many things, nothing works. This problem is only present on ubuntu.

I would appreciate any help. I am new to ubuntu so thanks in advance.

---

### Post by matt_symes on 2011-10-09
Hi 

What is the output of

```
xinput --list
```

Is this a synchronization issue; the touchpad losing synchronization?

After it happens again, open a terminal and type

```
dmesg | grep sync
```

Post results back here.

Kind regards

---

### Post by black.sfcro on 2011-10-09
[QUOTE=matt_symes;11325734]Hi 

What is the output of

```
xinput --list
```Is this a synchronization issue; the touchpad losing synchronization?

The output is:

:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]


Also, I have installed Synaptiks and made some configuration. For now I don't have problems using touchpad atm. I am not sure if this can solve the problem, i will see if it will happen again.

Regards

---

### Post by matt_symes on 2011-10-09
Hi

> AlpsPS/2 ALPS GlidePoint                    id=12    [slave  pointer  (2)]

I believe that is a Synaptics device. Post back if you get problems.

Kind regards

---

### Post by mikejonesey on 2011-10-09
reduce the touchpad sensitivity via system>pref>mouse... you will find the problem occurs when the touch pad is hot? and posibily a little greasy... reduce sensitivity and give a clean...

---

### Post by black.sfcro on 2011-10-16
Thank you for help guys, but nothing seems to work. 
  Synaptiks did not solve the problem. I tried to change sensitivity settings, etc. I cleaned the touchpad (I do it regularly) and nothing changed. 
  The problem repeats randomly, from the moment I log in. It happens in 8 out of 10 times I use UBUNTU. 
  I upgraded to 11.10, because I was hoping this might solve the problem. No luck.
  It is so annoying that it forced me to use only Vista on laptop for last days. The sad part is things like this are reason for not moving all the way to Ubuntu in last few years.

---

