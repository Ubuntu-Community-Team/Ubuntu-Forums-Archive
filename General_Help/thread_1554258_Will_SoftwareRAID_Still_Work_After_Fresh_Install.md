---
title: "Will SoftwareRAID Still Work After Fresh Install?"
date: 2010-08-16
forum: General Help
---

### Post by hayhursm on 2010-08-16
[FONT=Times New Roman][SIZE=3]So apparently RAID configurations on desktops are pretty much worthless using the motherboard’s internal hardware and BIOS settings.  How reliable is the Ubuntu SoftwareRAID?  I have 3 HDD’s one that I install Ubuntu on and the other two are in a RAID 1 setup strictly for data backup.  Will SoftwareRAID be able to pick up where it left off if for some reason I need to do a fresh install of Ubuntu or will I risk losing the data on the RAID 1 drives?  I wasn’t sure about this since SoftwareRAID is obviously software driven and not hardware driven.
[/SIZE][/FONT]

---

### Post by hayhursm on 2010-08-17
> **hayhursm said:**
> [font=times new roman][size=3]so apparently raid configurations on desktops are pretty much worthless using the motherboard’s internal hardware and bios settings. How reliable is the ubuntu softwareraid? I have 3 hdd’s one that i install ubuntu on and the other two are in a raid 1 setup strictly for data backup. Will softwareraid be able to pick up where it left off if for some reason i need to do a fresh install of ubuntu or will i risk losing the data on the raid 1 drives? I wasn’t sure about this since softwareraid is obviously software driven and not hardware driven.[/size][/font]

 
bump

---

### Post by hayhursm on 2010-08-19
> **hayhursm said:**
> bump
 
Bump

---

### Post by Calash on 2010-08-19
A hardware RAID is much more reliable than a software RAID.  So if you are having reliability issues with the hardware one I would not put much hope in the software.

For moving I have never gone from hardware to software but anytime I have moved hardware to hardware (Motherboard to expansion card) I have had to wipe everything and rebuild the set.

---

### Post by aeiah on 2010-08-19
you can rebuild the array after reinstallation and all that stuff but it isnt fool proof. you'd probably need to use the mdadm tools on the command line, although you may find gui software that'll do it for you.

---

### Post by davrosuk on 2010-08-19
Hardware RAID is significantly better in both reliability and performance - to such a point that I wouldn't trust software RAID for anything (even data I didn't mind losing!)

---

### Post by hayhursm on 2010-08-23
> **davrosuk said:**
> Hardware RAID is significantly better in both reliability and performance - to such a point that I wouldn't trust software RAID for anything (even data I didn't mind losing!)
 
> **aeiah said:**
> you can rebuild the array after reinstallation and all that stuff but it isnt fool proof. you'd probably need to use the mdadm tools on the command line, although you may find gui software that'll do it for you.
 
> **Calash said:**
> A hardware RAID is much more reliable than a software RAID. So if you are having reliability issues with the hardware one I would not put much hope in the software.
 
For moving I have never gone from hardware to software but anytime I have moved hardware to hardware (Motherboard to expansion card) I have had to wipe everything and rebuild the set.
 
[FONT=Times New Roman][SIZE=3]Sorry for the late reply.  If a software RAID can be rebuilt after the software has been wiped clean then how is this not more reliable than a hardware RAID? Calash said that whenever he moved hardware to hardware it was necessary to wipe out everything and rebuild the RAID set…this seems like it would be more inconvenient than just simply using mdadm to rebuild the RAID.  Plus, with a RAID adapter you are just adding one more piece of hardware to the setup that has the potential to fail.  If the adapter fails, isn’t it necessary to move the HDD data somewhere else, replace the adapter, rebuild the RAID and then move the data back to the HDD’s?  Also, most desktop motherboards do not use a “true” RAID setup and the CPU still ends up doing all the work so I understand that I will not get an increase in performance using software RAID versus hardware RAID.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I think this article has some good pointers in it: [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]https://help.ubuntu.com/community/FakeRaidHowto#Introduction[/SIZE][/FONT]]("https://help.ubuntu.com/community/FakeRaidHowto#Introduction")
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Am I on the right track with these comparisons?[/SIZE][/FONT]

---

### Post by hayhursm on 2010-08-25
> **hayhursm said:**
> [font=times new roman][size=3]sorry for the late reply. If a software raid can be rebuilt after the software has been wiped clean then how is this not more reliable than a hardware raid? Calash said that whenever he moved hardware to hardware it was necessary to wipe out everything and rebuild the raid set…this seems like it would be more inconvenient than just simply using mdadm to rebuild the raid. Plus, with a raid adapter you are just adding one more piece of hardware to the setup that has the potential to fail. If the adapter fails, isn’t it necessary to move the hdd data somewhere else, replace the adapter, rebuild the raid and then move the data back to the hdd’s? Also, most desktop motherboards do not use a “true” raid setup and the cpu still ends up doing all the work so i understand that i will not get an increase in performance using software raid versus hardware raid.[/size][/font]
 
[font=times new roman][size=3]i think this article has some good pointers in it: [/size][/font][[font=times new roman][size=3]https://help.ubuntu.com/community/fakeraidhowto#introduction[/size][/font]]("https://help.ubuntu.com/community/fakeraidhowto#introduction")
 
[font=times new roman][size=3]am i on the right track with these comparisons?[/size][/font]
 
 
bump

---

### Post by hayhursm on 2010-08-26
> **hayhursm said:**
> [font=times new roman][size=3]sorry for the late reply. If a software raid can be rebuilt after the software has been wiped clean then how is this not more reliable than a hardware raid? Calash said that whenever he moved hardware to hardware it was necessary to wipe out everything and rebuild the raid set…this seems like it would be more inconvenient than just simply using mdadm to rebuild the raid. Plus, with a raid adapter you are just adding one more piece of hardware to the setup that has the potential to fail. If the adapter fails, isn’t it necessary to move the hdd data somewhere else, replace the adapter, rebuild the raid and then move the data back to the hdd’s? Also, most desktop motherboards do not use a “true” raid setup and the cpu still ends up doing all the work so i understand that i will not get an increase in performance using software raid versus hardware raid.[/size][/font]
 
[font=times new roman][size=3]i think this article has some good pointers in it: [/size][/font][[font=times new roman][size=3]https://help.ubuntu.com/community/fakeraidhowto#introduction[/size][/font]]("https://help.ubuntu.com/community/fakeraidhowto#introduction")
 
[font=times new roman][size=3]am i on the right track with these comparisons?[/size][/font]
 
> **davrosuk said:**
> hardware raid is significantly better in both reliability and performance - to such a point that i wouldn't trust software raid for anything (even data i didn't mind losing!)
 
> **calash said:**
> a hardware raid is much more reliable than a software raid. So if you are having reliability issues with the hardware one i would not put much hope in the software.
 
For moving i have never gone from hardware to software but anytime i have moved hardware to hardware (motherboard to expansion card) i have had to wipe everything and rebuild the set.
 
> **aeiah said:**
> you can rebuild the array after reinstallation and all that stuff but it isnt fool proof. You'd probably need to use the mdadm tools on the command line, although you may find gui software that'll do it for you.
 
bump

---

### Post by hayhursm on 2010-08-30
> **hayhursm said:**
> bump

Bump

---

