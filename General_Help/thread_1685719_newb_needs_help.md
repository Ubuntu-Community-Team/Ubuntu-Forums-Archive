---
title: "newb needs help"
date: 2011-02-11
forum: General Help
---

### Post by northwestsupra on 2011-02-11
ok so i downloaded the desktop version and went ahead and installed kubuntu over windows 7. i chose 30GB as my space to use and followed the instructions through the installer, when it finished i was asked to reboot so i went ahead and rebooted, on reboot i got the option to boot windows 7 or unbuntu so i selected unbuntu of course :) it sat there for about 5 minutes with my tv "monitor" saying no signal, but i could see my little HD activity LED going crazy so i figured it was doing somthing, after 5 minutes it restarted itself and then I was led back to the option to choose OS's. again i selected linux and thats when i had the option to choose between different boot loaders "i dont know the official name" but i had a list

unbuntu 10.x
unbuntu 10.x recovery
i dont remember what this was
windows 7 boot

so i picked unbuntu 10.x and then it acted like it was gonna do somthing then all i have is a blue screen saying no signal. so i have a feeling its got somthing to do with my video card driver possibly??

here is my computer specs.
Pentium 4 3.2GHZ HT
EVGA Nvidia 9500 GT
2 GB corsair extreme

also wanna note when i went to boot into windows 7 the first time i got a blue screen, came back and tried it a second time and got the "there was an issue with windows boot file. repair boot or start windows normally" i went ahead and tried it normally again and it booted the second time. its probably not important i just thought i would mention that though. 

any help would be great thanks guys :) :popcorn: show me your magic

---

### Post by PeteUK on 2011-02-11
[COLOR=black][FONT=Verdana]Have you tried booting off an Ubuntu install disk to see if you can produce a signal from your graphics card. If not I would check all of your BIOS settings regarding video output. If you still can’t see what’s happing I would try swapping (temporally) your graphics card so you can access the Ubuntu GUI and make the needed changes for your graphics card.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]If you can boot into Ubuntu you may need to install the appropriate files/drivers for your graphics car see    [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) for help. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Please note I’m pretty new myself to this community but there is my suggestions there will no doubt be a way of installing the required files without having to boot into the Ubuntu GUI but atm that is beyond me. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Hope that helps good luck. [/FONT][/COLOR]
8-[

---

### Post by 3Miro on 2011-02-11
In order to use a TV monitor you probably have to install the proprietary Nvidia drivers. Try booting with a regular monitor, then go to System -> Hardware Manager (I am not 100% sure where the things is in KDE, you can use the Konsole to run "jockey"). Then select the Nvidia drivers. You should be able to set things up from the Nvidia Control Center.

---

### Post by grahammechanical on 2011-02-11
Here is a question: to quote you

> went ahead and installed kubuntu over windows 7

If you actually did that you would not be able to boot into Windows 7, would you?

Regards.

---

### Post by northwestsupra on 2011-02-11
> **grahammechanical said:**
> Here is a question: to quote you



If you actually did that you would not be able to boot into Windows 7, would you?

Regards.

sorry, dual boot windows is on a different hard drive then unbuntu

---

### Post by northwestsupra on 2011-02-11
> **PeteUK said:**
> [COLOR=black][FONT=Verdana]Have you tried booting off an Ubuntu install disk to see if you can produce a signal from your graphics card. If not I would check all of your BIOS settings regarding video output. If you still can’t see what’s happing I would try swapping (temporally) your graphics card so you can access the Ubuntu GUI and make the needed changes for your graphics card.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]If you can boot into Ubuntu you may need to install the appropriate files/drivers for your graphics car see    [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) for help. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Please note I’m pretty new myself to this community but there is my suggestions there will no doubt be a way of installing the required files without having to boot into the Ubuntu GUI but atm that is beyond me. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Hope that helps good luck. [/FONT][/COLOR]
8-[

i dont have a cd/dvd drive :P felt the need for another hard drive was more important because i run virtual disk's more than a real cd.

are you talking about the bios of the motherboard right, there isnt a special bios for unbuntu? 

i dont have another video card, the motherboard is picky with them in the first place.

---

### Post by northwestsupra on 2011-02-11
> **3Miro said:**
> In order to use a TV monitor you probably have to install the proprietary Nvidia drivers. Try booting with a regular monitor, then go to System -> Hardware Manager (I am not 100% sure where the things is in KDE, you can use the Konsole to run "jockey"). Then select the Nvidia drivers. You should be able to set things up from the Nvidia Control Center.

im literally so new to this i have no idea how to access konsole at all.

---

