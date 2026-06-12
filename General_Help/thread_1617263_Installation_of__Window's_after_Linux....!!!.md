---
title: "Installation of  Window's after Linux....!!!"
date: 2010-11-09
forum: General Help
---

### Post by tajiknomi on 2010-11-09
[SIZE=2]I know this is a Common thread...

i had currently installed Ubuntu & Kubuntu(Dual-boot), both are Lucid.

I am using Linux for about 2 months and now i want to Replace Kubuntu With Win-7(So that i can use only **Ubuntu & WIN7**), i want to know the **easiest** way to install Win after Linux as i had install **ubuntu before window's**...i know that installation of window's will **effect my MBR**, and in most of the thread i have seen that User just have to **repair their MBR **after installing window's(**after Linux**).

Honestly saying, using grub or Configuring MBR is quite horrible for me as i am the beginner :confused:,
Well, now i want to install win-7 and don't want to remove my **Ubuntu**,therefore i need a **simplest** an easy method to **repair my MBR** after that....
1)How can i **repair my MBR** after installing Window..?
2) As i have mentioned that i have installed Kubuntu on another Partition,after **removing Kubuntu** it i can use just use "**update-grub**" or any think else needed..?

Sorry for my bad English,
Any simplest method will be Appreciated...:P
[/SIZE]

---

### Post by WorMzy on 2010-11-09
It's not that difficult to reinstall grub. Read this: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

As for your other query, yes, update-grub should remove Kubuntu from the list. It should also add Windows.

---

### Post by dcstar on 2010-11-09
> **tajiknomi said:**
> [SIZE=2]
.........
Well, now i want to install win-7 and don't want to remove my **Ubuntu**,therefore i need a **simplest** an easy method to **repair my MBR** after that....
.........
Sorry for my bad English,
Any simplest method will be Appreciated...:P
[/SIZE]

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by tajiknomi on 2010-11-09
[SIZE=2]Thanks To Both :P

I was thinking 5min ago that i have to use some of the code's(Provided by other's for repairing of mbr) for that, and i will not bother my self to read **Grub-2** ;), but i was wrong :(....

well i had to read it now,.....

thnkx
[/SIZE]

---

### Post by dcstar on 2010-11-09
> **tajiknomi said:**
> [SIZE=2]Thanks To Both :P

I was thinking 5min ago that i have to use some of the code's(Provided by other's for repairing of mbr) for that, and i will not bother my self to read **Grub-2** ;), but i was wrong :(....

well i had to read it now,.....

thnkx
[/SIZE]
You can just repair the MBR by firstly saving it with the following (assuming your boot drive is /dev/sda):
```
sudo dd **if**=/dev/sda **of**=/mbr-backup bs=446 count=1
```

And when you have installed Windows you restore the original MBR (use a Live CD to mount the place where you have saved the **mbr-backup** file):
```
sudo dd **of**=/dev/sda **if**=/mbr-backup bs=446 count=1
```

Reboot the system and you should have the pre-Windows Grub menu, then this should add the Windows to the Grub menu:
```
sudo update-grub
```

---

### Post by WorMzy on 2010-11-09
Of course, the above assumes you have been using Ubuntu's grub, and didn't install grub when you installed Kubuntu.

If you installed grub when you installed Kubuntu, then you've probably been using it's grub installation. If you put back the MBR that looks for Kubuntu's grub, and it can't find it (because you've deleted the partition), you'll end up at a grub rescue prompt.

---

### Post by tajiknomi on 2010-11-10
*[SIZE=2]Thanks to all of you:guitar:[/SIZE]*

---

