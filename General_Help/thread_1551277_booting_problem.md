---
title: "booting_problem"
date: 2010-08-12
forum: General Help
---

### Post by mmabdallah on 2010-08-12
Hi everybody......I really indeed need for ur help :S
 
I've installed Ubuntu 10.6 on my pc inside windows XP unfortuynately the booting environment of xp has been disappeared and i cant open xp now 
 
to be more clear I've windows XP and 7. windows 7 still availabe but not for XP
 
waiting for ur reply...
THANKS IN ADVANCE..............

---

### Post by viralmeme on 2010-08-12
> **mmabdallah said:**
> I've installed Ubuntu 10.6 on my pc inside windows XP

Do you mean you installed Ubuntu as a guest OS inside Windows XP using the [Wubi installer]("http://wubi-installer.org/") ? Or did you install Ubuntu side-by-side with Windows by resizing Windows to make room for Ubuntu. If so what did you use to resize the Windows partition? Else you could try [Triple Boot]("http://lifehacker.com/193474/hack-attack-how-to-triple+boot-windows-xp-vista-and-ubuntu")ing. Fireup [Disk Manager]("http://hubpages.com/hub/Using-Disk-Management-in-Windows-7-Vista") in Windows and post the results here.

---

### Post by mmabdallah on 2010-08-12
first i intended to install it as guest OS but after restarting the pc it started as side by side installation.
but sorry i didnt get ur answer clearly and i dont know these applications or software

---

### Post by jerenept on 2010-08-12
Quite honestly, I don't have the slightest clue what you are talking about. We need more information to be able to help you.

---

### Post by ranch hand on 2010-08-12
Boot to your Live CD and then get this script and post it here.  This should give us some clues.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You should get a "results" file on the desktop.  We need the whole thing.

---

### Post by mmabdallah on 2010-08-14
[SIZE=4]Sorry ...im really sorry[/SIZE]
[SIZE=4]now i figured out that i have alot of booting options under GNU GRUB :[/SIZE]
[SIZE=4]-2 memory check bootings[/SIZE]
[SIZE=4]-2 ubuntu bootings[/SIZE]
[SIZE=4]-windows 7[/SIZE]
[SIZE=4] and when i choose windows 7 it open new loader in it: [/SIZE]
[SIZE=4]-windows XP[/SIZE]
[SIZE=4]-windows 7[/SIZE]
[SIZE=4]-ubuntu[/SIZE]
[SIZE=4][/SIZE] 
[SIZE=4]but windows XP also contains two options:[/SIZE]
[SIZE=4]-windows Xp[/SIZE]
[SIZE=4]-ubuntu[/SIZE]
[SIZE=4][/SIZE] 
[SIZE=4]i dont know whats happen and how can i solve this problem. it is not about xp disappearance it is now multiple nested booting options.[/SIZE]
[SIZE=4][/SIZE] 
[SIZE=4]sorry for wasting ur time and really thanks for ur concern.[/SIZE]

---

### Post by ranch hand on 2010-08-14
It would still be good for you t orun taht boot info script.  It will let you know what is going on pretty clearly.

---

### Post by mmabdallah on 2010-08-15
but i dont like this...plz if u have any way to help plz im waiting for ur reply :)

---

### Post by ranch hand on 2010-08-15
Boot to the live CD and run the boot info script and post it here.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Karl1982 on 2010-08-15
> **mmabdallah said:**
> [SIZE=4]Sorry ...im really sorry[/SIZE]
[SIZE=4]now i figured out that i have alot of booting options under GNU GRUB :[/SIZE]
[SIZE=4]-2 memory check bootings[/SIZE]
[SIZE=4]-2 ubuntu bootings[/SIZE]
[SIZE=4]-windows 7[/SIZE]
[SIZE=4] and when i choose windows 7 it open new loader in it: [/SIZE]
[SIZE=4]-windows XP[/SIZE]
[SIZE=4]-windows 7[/SIZE]
[SIZE=4]-ubuntu[/SIZE]
 
[SIZE=4]but windows XP also contains two options:[/SIZE]
[SIZE=4]-windows Xp[/SIZE]
[SIZE=4]-ubuntu[/SIZE]
 
[SIZE=4]i dont know whats happen and how can i solve this problem. it is not about xp disappearance it is now multiple nested booting options.[/SIZE]
 
[SIZE=4]sorry for wasting ur time and really thanks for ur concern.[/SIZE]
 
This comes from the order and method you used to multiboot your system.  The first loader you mentioned (and from the sound of it, what loads first) is GRUB.  When you select Windows 7, what it does is loads BOOTMGR from your Windows 7 partition (or system reserved partition, where applicable).  When you select Windows XP, it loads NTLDR's boot.ini from your XP partition.  Each of these three is a separate and standalone boot menu.  You see, GRUB is not able to directly load Windows, so instead it chainloads Windows' boot loader.  That's why the menus appear to be nested, but it's really more of a lateral movement in that sense.

---

### Post by ranch hand on 2010-08-15
The only one that bothers me is the XP one.  If you would run that boot info script it would tell us all we need to know.

If that is just too hard you could at least tell us what kind of install you did with Ubuntu.  Was it a wubi install?

---

