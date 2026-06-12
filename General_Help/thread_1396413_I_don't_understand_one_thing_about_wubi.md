---
title: "I don't understand one thing about wubi"
date: 2010-02-02
forum: General Help
---

### Post by aviramof on 2010-02-02
when i install ubuntu via windows it easily create a dual boot but when i do a full installion it doesn't is it possible for me to install normal and then use easy bcd to create a dual boot via wubi option?
 
thanks in advance.
 
and by the way why does the ubuntu installer doesn't download updates to the installer i know that at least the translation files are not updated 
so why doesn't the installer download them and everything eles before installing the os?

---

### Post by J V on 2010-02-02
> I don't understand one thing about wubiYep!> when i install ubuntu via windows it easily create a dual boot but when i do a full installion it doesn't is it possible for me to install normal and then use easy bcd to create a dual boot via wubi option?Grammar... confusing hehe... I think you want to migrate wubi to full install? You can, but shouldn't. Full install *alongside* windows, will give you dual boot menu. If it doesn't, fix that before resorting to wubi> and by the way why does the ubuntu installer doesn't download updates to the installer i know that at least the translation files are not updated 
so why doesn't the installer download them and everything eles before installing the os?Lets see:
1. Your HD woulden't be big enough
2. It only runs the liveCD, which doesn't contain them
3. Why do something twice that was already done right?

---

### Post by Ordes on 2010-02-02
> **aviramof said:**
>  when i do a full installion it doesn't
What problems are you running into? But your way should work. Never used easy bcd or wubi. But when u move your ubu to another partition you probably need to reconfigur youre boot-loader. 

 
> so why doesn't the installer download them and everything eles before installing the os?
1. You mean the liveISO? becuase they would always need to rebuild a new one
2. Installing and downloading all updates can take some time, depending how far behind you are from the release time of the ISO. And the install wouldnt be able to finish before downloading updates. So no running OS for maybe hours...
3. Better to have the OS installed and running, and than patch it up...

---

### Post by aviramof on 2010-02-02
my problem is that full install don't create dual boot menu not ubuntu 9.10 any way.
but 9.10 wubi does but i have problem connecting to the internet in this version so
i'm trying to install 8.10 now because i was told it's more stable and when i tried it live
now i did managed to connect to the internet and she does look much better i have to say.
 
let's hope that full install of 8.10 will create dual boot menu and if not that i can create one using easy bcd and wubi.
 
but i have noticed one big annoying bug in bote 8.10 and 9.10 when i choose the option to create partitions manually it doesn't show my empty partition and i don't 
understand why it shows all partition but all of them are seen as if there are files in 
them which i know that at least one partition is completly empty in order to recognize
this partition in your installer i need to go back to windows delete the partition completly and then your installer show it as an empty space if not he show it as if it has some 4GB of information which is not true very strange bug.

---

### Post by Ordes on 2010-02-02
>> my problem is that full install don't create dual boot menu not ubuntu 9.10 any way.

> How did u install? Did you uncheck the option to create bootloader? Did you try to set the bootloader manually, or by default? Never heart about this problem

>> but i have noticed one big annoying bug in bote 8.10 and 9.10 when i choose the option to create partitions manually it doesn't show my empty partition and i don't
understand why it shows all partition but all of them are seen as if there are files in 

> hard to say. perhaps you are just reading it wrong. in the beginning of your ubuntu experienc, it is easier to partition everything ahead, e.g in windows, or gparted in liveISO. and than run the installer. the manual partitioner during install can be confusing.
tipp: create two pars if you have the space. one for "/" root where the system goes, and one for /home. where your settings files go.
"/" 10-15gb should be enough
if you want to you can also create an extra swap-parition (2-4gb) -> virtual ram

---

### Post by 3rdalbum on 2010-02-02
A partition is only empty if it is unformatted. If it's just an NTFS or fat32 filesystem that doesn't have any files in it, then it is NOT an empty partition.

---

