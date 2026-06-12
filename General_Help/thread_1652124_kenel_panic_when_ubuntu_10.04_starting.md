---
title: "kenel panic when ubuntu 10.04 starting"
date: 2010-12-24
forum: General Help
---

### Post by same.500 on 2010-12-24
Hi guys!                               Iam sorry i try to search on some one have the same problem but i couldn't .                        My problem start when i had amessege  from update manager saying some packages couldn't be installed so i restart the computer and then  i couldn't start ubuntu and amessege on splash screen saying  ( kernal panic ) and if you need more information just aske me  . Any one can help?

---

### Post by djeikyb on 2010-12-24
1. In the grub menu, can you choose the second option, that says something like Ubuntu Safe Mode? Do any of the older kernel entries work?

2. In the grub menu, highlight the entry you normally choose, press e, delete the line that says quiet, then hit b to boot. Hopefully now you'll be able to see some information that is useful rather than a stupid splash screen.

---

### Post by same.500 on 2010-12-25
Thanks! I try the recovery mode but it's not working and that what i had from removing the line :

---

### Post by same.500 on 2010-12-25
I wish if you answer me as fastes as possipole.

---

### Post by matt_symes on 2010-12-25
Hi

Maybe you need to rebuild initramfs... Might be worth a try.

You will need to have a LiveCD/USB handy. Boot into LiveCD and start a terminal. 

Type this.

```
sudo mkdir /mnt/drive
```

enter your password. Nothing will be echoed to the screen. This is normal. The mount you Ubuntu partition on the hard drive.

```
sudo mount /dev/sd**XY** /mnt/drive
```

where, in the command above, X is your drive (a,b,c etc) and Y is your partition number).

```
sudo update-initramfs -k all -u -b /mnt/drive/boot
```

This should recreate the initramfs.

Maybe that's the problem. Good luck.

BTW: do you have an old kernel to boot into?

Kind regards

---

### Post by same.500 on 2010-12-25
I'm sorry! this is not working and i had this line ; update-initramfs is disabled since running on read-only media

---

### Post by matt_symes on 2010-12-25
Hi

> I'm sorry! this is not working and i had this line ; update-initramfs is disabled since running on read-only media

Alright lets try a file system check on the partition. You will need the LiveCD again. 

Boot into the LiveCD and, after making sure the parition is _not_ mounted type

```
sudo e2fsck /dev/sd**XY** -y -f -v -c
```

where, as before, X and Y are drive and partition. 

Hopefully, that should fix the filing system and then try the previous post again.

Post back any errors.

Kind regards

---

### Post by same.500 on 2010-12-25
Hi
I had the same line (update-initramfs is disabled since running on read-only media) and this is what i see when i use the last command line you sent :

---

### Post by matt_symes on 2010-12-25
Hi

Sorry mate. I, for one, am out of ideas then.

Hopefully some one else will have some ideas.

I have to spend some time with my family.

Kind regards

---

### Post by same.500 on 2010-12-25
Thank you any why matt_symes!

---

### Post by same.500 on 2010-12-26
I had grub 1.96 screen but i steel can't inter my ubuntu . 
Any idea!

---

### Post by amsterdamharu on 2010-12-26
Can you try booting from the live CD and try the same commands again, then copy and paste the output from the terminal to the forum? (you can start the terminal by pressing alt + F2, type gnome-terminal and then click run)

```
sudo e2fsck /dev/sda1 -y -f -v -c
sudo mkdir /mnt/drive
sudo mount /dev/sda1 /mnt/drive
sudo update-initramfs -k all -u -b /mnt/drive/boot
```

I am guessing the /boot directory is in sda1 but to be sure we'll need the output of the [boot info script]("http://sourceforge.net/projects/bootinfoscript/").

---

### Post by same.500 on 2010-12-26
Hi!
I thing your suggestion not going to fix the problem I'm already try this.

---

### Post by amsterdamharu on 2010-12-26
> Can you try booting from the live CD [COLOR=Red]and try the same commands again[/COLOR],  [COLOR=Red]then copy and paste the output from the terminal to the forum?[/COLOR] (you can  start the terminal by pressing alt + F2, type gnome-terminal and then  click run)> I thing your suggestion not going to fix the problem I'm already try this.     Yes but after running the commands you never posted the output of it. Getting an error for read only filesystem sounds a bit strange and I think when mounting it there should be an error.

[COLOR=Red]I am guessing the /boot directory is in sda1 but to be sure we'll need the output of the [boot info script]("http://sourceforge.net/projects/bootinfoscript/").[/COLOR]
The text "boot info script" is a link you can click on.

---

### Post by same.500 on 2010-12-26
Thanks  aloot for give some of your time to help me.
I find this problem taking aloots of time from me so i find it is bater to reinstall ubuntu again .:)

---

### Post by OzzyFrank on 2011-01-17
Hi. This is marked as [SOLVED], so can you please share the solution with the rest of us?

---

### Post by matt_symes on 2011-01-17
Hi

> **OzzyFrank said:**
> Hi. This is marked as [SOLVED], so can you please share the solution with the rest of us?

> **same.500 said:**
> Thanks  aloot for give some of your time to help me.
I find this problem taking aloots of time from me so i find it is bater to reinstall ubuntu again .:)

I think the OP reinstalled Ubuntu.

Kind regards

---

### Post by OzzyFrank on 2011-01-17
Oh, I see... stretching the definition of [SOLVED], hehe. Oh well, I was hoping to help someone, but there seems to be many different causes, so the more possible solutions, the better.

I'm glad when people take the time to mark a thread as [SOLVED], but prefer it if it is actually solved, hehe!

---

