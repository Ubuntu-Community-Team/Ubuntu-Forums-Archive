---
title: "after upgrade to lynx none of of my external drives cd drive or flash drives are pick"
date: 2010-05-09
forum: General Help
---

### Post by shantiq on 2010-05-09
[B][COLOR="Blue"]upgraded from karmic through update manager

AND


none of of my external drives cd drive or flash drives are picked up

 any ideas?


had to go back to karmic and will remain there for a while





 any ideas?[/COLOR][/B]

---

### Post by unplugged23 on 2010-05-09
[http://ubuntuforums.org/showthread.php?t=1473874&highlight=auto+mount+usb+drive&page=3](http://ubuntuforums.org/showthread.php?t=1473874&highlight=auto+mount+usb+drive&page=3)

that post contains many different solutions to your problem

---

### Post by shantiq on 2010-05-09
**[COLOR="Blue"]thanx [/COLOR]**

---

### Post by shantiq on 2010-05-26
[B][COLOR="Blue"]i posted this 2 weeks ago and not too much info so far

i simply updated from the update manager and then again from a clean install from disc and when i reloaded after upgrade **[COLOR="Sienna"]none of the the disc drive flashdrives or external drives show up when i click on Places[/COLOR]**


any suggestions as to what one could do where one could look     all of these are/were fine on karmic


could it be to do with permissions/   where would i look for that?

reading around i see gparted is mentioned as a powerful tool could it be of use here?

I have had to return to karmic   but would like to try again sometime soon any suggestions at all


it is such a crucial element to have these recognized by the system

all clever help welcome    shan[/COLOR][/B]

---

### Post by dino99 on 2010-05-26
manage your devices and partitions with mountmanager

---

### Post by timgood on 2010-05-26
I had the same problem. I solved it by uninstalling pmount, and then re-installing it together with libpmount0.0

Hope this helps.

---

### Post by R Smit on 2010-05-26
> **shantiq said:**
> [B][COLOR="Blue"]i posted this 2 weeks ago and not too much info so far

i simply updated from the update manager and then again from a clean install from disc and when i reloaded after upgrade **[COLOR="Sienna"]none of the the disc drive flashdrives or external drives show up when i click on Places[/COLOR]**


any suggestions as to what one could do where one could look     all of these are/were fine on karmic


could it be to do with permissions/   where would i look for that?

reading around i see gparted is mentioned as a powerful tool could it be of use here?

I have had to return to karmic   but would like to try again sometime soon any suggestions at all


it is such a crucial element to have these recognized by the system

all clever help welcome    shan[/COLOR][/B]

Do you have a floppy drive? If not, disable support for floppy in the BIOS. I read this solution somewhere, and it worked for me although I do not understand why BIOS would influence this problem

---

### Post by dino99 on 2010-05-26
> **R Smit said:**
> Do you have a floppy drive? If not, disable support for floppy in the BIOS. I read this solution somewhere, and it worked for me although I do not understand why BIOS would influence this problem

pci irq conflicts

---

### Post by shantiq on 2010-05-26
> **timgood said:**
> I had the same problem. I solved it by uninstalling pmount, and then re-installing it together with libpmount0.0

Hope this helps.



[B][COLOR="Blue"]thanx guys good tips

Tim do you mean none of your drives were picked up either?

and the pmount/libpmount fixed it totally?

the tip about mount manager sounds like a good route too

so at some point i will brace myself and try again

the floppy bios uncheck route seems cool too


any other advice welcome too[/COLOR][/B]

---

### Post by timgood on 2010-05-26
> **shantiq said:**
> [B][COLOR="Blue"]thanx guys good tips

Tim do you mean none of your drives were picked up either?

and the pmount/libpmount fixed it totally?

the tip about mount manager sounds like a good route too

so at some point i will brace myself and try again

the floppy bios uncheck route seems cool too


any other advice welcome too[/COLOR][/B]

That's right - none of my removable drives or USB keys were being automounted and did not show up in Computer. The uninstall/re-install worked 1st time. Think it's something to do with stuff not being updated during the upgrade.

---

### Post by shantiq on 2010-05-26
[B][COLOR="Blue"]well tim neither of these were ticked in automatically i did and then my USB got picked up


but disc drive and external still not

i also installed mountmanager but got no joy there either

back to karmic is where i went[/COLOR][/B]

---

### Post by shantiq on 2010-06-20
a

---

### Post by shantiq on 2010-06-20
[COLOR=Blue][B]ok finally cracked it


all i had to do the whole time was to [SIZE=2]disable the floppy drive

[SIZE=1]then everything else is reestablished


someone ( R smit)has suggested it a long time ago thanx man[/SIZE][/SIZE][/B][/COLOR]> Do you have a floppy drive? If not, disable support for floppy in the BIOS. I read this solution somewhere, and it worked for me although I do not understand why BIOS would influence this problem[COLOR=Blue][B][SIZE=2][SIZE=1] 

[SIZE=2]and it works!!!!!!!![/SIZE]
[/SIZE][/SIZE][/B][/COLOR]

---

