---
title: "System hangs in ubuntu"
date: 2011-03-11
forum: General Help
---

### Post by vat with tux on 2011-03-11
Hello friends.

I installed ubuntu 10.04 in one of my friends pc.
but the problem is that just after few seconds after starting ubutnu it hangs. I just can't even move my mouse & i have to restart the system using hardware restart button.

System hardwares are as follows:
 
Processor :intel core 2 duo
Motherboard:Mercury
RAM: 1 GB DDR2

Please someone tell me that what can i do?
Thanking in advance.

---

### Post by Hippytaff on 2011-03-11
What graphics card does it have?
 
Have you tried logging into recovery mode and disabling compiz and all the pointless graphics magic?

---

### Post by vat with tux on 2011-03-11
Well there is no graphic card in his PC.

But i would like to point out one thing that windows 7 is working perfectly on his PC. 
One more thing is that apart from mother board we both are having same hardwares & ubuntu is working perfectly fine on my PC.
I'm having intel motherboard while he is having mercury.

And i haven't try anything else yet.

---

### Post by Hippytaff on 2011-03-11
There will be a graphics device...so when you next go to try to fix it the results of the following command can be used to find the graphics device name. The you can look into it.
```

lscpi

```

It might be worth googling "mercury motherborad ubuntu" to look for any known issues, but I think it's a graphics device issue, or the iso, CD is corrupt.

---

### Post by Rubi1200 on 2011-03-11
As Hippytaff pointed out, it might be worth doing some searches about that particular MB.

If you just want to find information on the graphics card rather than all PCI devices, use this:

```
lspci | grep VGA
```

---

### Post by Hippytaff on 2011-03-11
> **Rubi1200 said:**
> As Hippytaff pointed out, it might be worth doing some searches about that particular MB.

If you just want to find information on the graphics card rather than all PCI devices, use this:

```
lspci | grep VGA
```

Rubi - I sometimes leave grep out when posting here because finding | is annoying for people sometimes. :-)

but this will make things easier.

---

### Post by vat with tux on 2011-03-12
> **Hippytaff said:**
> Rubi - I sometimes leave grep out when posting here because finding | is annoying for people sometimes. :-)

but this will make things easier.

well '|' is not anoying for me b'coz i'm knowing basic shell script.:)

---

### Post by vat with tux on 2011-03-12
Thanks Ruby & Hippytaff. I'll try out ur suggestions next time i'll go to his home for installing ubuntu.:) but it could not the problem of corrupted cd b'coz i hv installed ubunut in my pc from the same cd.:)

---

### Post by runeh76 on 2011-03-12
Hi

-Boot ur PC
-Check ur clock when its hang
-Boot with LiveCD and run terminal:
```
dmesg
```

-post hang-time output here

---

