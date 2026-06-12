---
title: "Grub loader error..."
date: 2010-10-09
forum: General Help
---

### Post by tajiknomi on 2010-10-09
[SIZE=2][I]I have seen **Grub loader error** when i on my pc..

actually i had formated that drive (on which kubuntu was installed) .now i see Grub error message..
i have my ubuntu on another Drive..

can some1 tell me what should i do in order to install my **Grub again**,,
My **partion pic** is attached herewith..
i want to install my Grub in **Gnome-drive**(see in attached pic)
what should i write in terminal..?

sorry 4 my bad english...
[/I][/SIZE]

---

### Post by clrg on 2010-10-09
As far as I can tell, you didn't attach a picture.

To install GRUB2, run

```
sudo grub-install [OPTION] install_device
```

for example

```
sudo grub-install /dev/hda1
```

_Be careful when using those commands, if applied wrong, they could lead to data loss._

---

### Post by tajiknomi on 2010-10-09
[SIZE=2]oh..sorry,..i forgot.

pic is here...
[/SIZE]

---

### Post by clrg on 2010-10-09
Run

```
sudo umount /dev/sda1
```

that will unmount your hard disk.

Then do a

```
sudo grub-install /dev/sda
```

which installs grub to your hard drive.

---

### Post by tajiknomi on 2010-10-09
[I][SIZE=2]i got the following error...

[B]Unique input/output error,
Couldn't find the device for /boot: Not found or not a blocked device[/B]
:(
[/SIZE][/I]

---

### Post by sendblink23 on 2010-10-09
> **tajiknomi said:**
> [SIZE=2]oh..sorry,..i forgot.

pic is here...
[/SIZE]

sorry for the random question... is that 8.10? if it is... I miss it

---

### Post by clrg on 2010-10-09
I think your boot partition (/ or /boot) needs to be primary. Did this partition layout work before?

---

### Post by tajiknomi on 2010-10-09
[SIZE=2][I]now i am from live-cd,,,,and in the given pic (My ubuntu-lucid is installed in Gnome-drive(Sda8

what can i do now>??

i never faced grub error in future,,moreover i m new to linux
[/I][/SIZE]

---

### Post by tajiknomi on 2010-10-09
[SIZE=2][I]My ubuntu is installed in sda8,
what can i do now...?what type of command should i write..?
[/I][/SIZE]

---

### Post by clrg on 2010-10-09
> **tajiknomi said:**
> [I]
what can i do now...?
[/I]

[QUOTE=clrg]I think your boot partition (/ or /boot) needs to be primary. Did this partition layout work before?[/QUOTE]

You could answer my question, if you like.

---

### Post by tajiknomi on 2010-10-09
[SIZE=2][I]sda8 is not primary...

and yes ,it works be4...you can guess from the pic
[/I][/SIZE]

---

### Post by tajiknomi on 2010-10-09
[SIZE=2][I]The drive (where ubuntu) is installed is not primary...

it is in Sda8..have a look at the pic above
[/I][/SIZE]

---

### Post by clrg on 2010-10-09
> **tajiknomi said:**
> [SIZE=2][I]sda8 is not primary...
[/I][/SIZE]

I know that. 

> **tajiknomi said:**
> [SIZE=2][I]
and yes ,it works be4...you can guess from the pic
[/I][/SIZE]

Actually, I can't. It doesn't say if Ubuntu booted before.

What happens if you run 

> grub-setup /dev/sda

---

### Post by tajiknomi on 2010-10-09
> **tajiknomi said:**
> [SIZE=2][I]The drive (where ubuntu) is installed is not primary...

it is in Sda8..have a look at the pic above
[/I][/SIZE]
a

---

### Post by tajiknomi on 2010-10-09
*[SIZE=2]it says **the program currently is not installed**...[/SIZE]*

---

### Post by tajiknomi on 2010-10-09
[SIZE=2]yes it works before..
[/SIZE]

---

### Post by The Cog on 2010-10-09
This article takes you through reinstalling grub. I know that it wasn't installing windows that broke your grub, but the recovery method is the same whatever the reason for the breakage.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by tajiknomi on 2010-10-09
[SIZE=2][I]thanks to all of you..:P
i got it...
[/I][/SIZE]

---

### Post by oldfred on 2010-10-09
No Ubuntu partitions have to be primary, but windows does have to have a primary to boot from.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Nevermind I see it is solved.

---

