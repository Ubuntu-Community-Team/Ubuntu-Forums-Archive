---
title: "Nothing happens when I plug in my phone."
date: 2009-10-05
forum: General Help
---

### Post by Kitty_Rose7673 on 2009-10-05
Where can I go to locate my phone? (I am trying to copy files to it) it doesnt show up automatically and it doesnt show up under places. PLZ HELP?!:(

---

### Post by khelben1979 on 2009-10-05
How is the phone connected? By [the usb port]("http://en.wikipedia.org/wiki/Usb")?

---

### Post by Kitty_Rose7673 on 2009-10-05
yes

---

### Post by khelben1979 on 2009-10-05
What's the model of the phone?

---

### Post by Kitty_Rose7673 on 2009-10-06
Motorola ROKR. It works just fine on my boyfriend's computer.

---

### Post by dhughes on 2009-10-06
Open up Terminal by going here Applications>Accessories>Terminal

Type ```
sudo fdisk -l
```  That's a small L on the end after fdisk

You can probably see it in the list that appears.

---

### Post by Kitty_Rose7673 on 2009-10-06
ok... then what? Sorry I am like really Ubuntu stupid my bf just installed it for me

---

### Post by dhughes on 2009-10-06
Do you see something like this?

 ```
/dev/sdd
```

or it's probably going to look like this

```
Disk /dev/sdd: 8119 MB, 8119123968 bytes
1 heads, 62 sectors/track, 255768 cylinders
Units = cylinders of 62 * 512 = 31744 bytes
Disk identifier: 0x00000000

```

---

### Post by Kitty_Rose7673 on 2009-10-06
Disk /dev/sda: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001b3f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3478    27937003+  83  Linux
/dev/sda2            3479        3739     2096482+  82  Linux swap / Solaris


That's what I see.

---

### Post by dhughes on 2009-10-06
> **Kitty_Rose7673 said:**
> Disk /dev/sda: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001b3f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3478    27937003+  83  Linux
/dev/sda2            3479        3739     2096482+  82  Linux swap / Solaris


That's what I see.

 Weird, I don't see it.

 /dev/sda and /dev/sda1 and /dev/sda2 are the partitions of the main hard drive in the computer system you're using, it's not the phone.

 Do other USB devices work when plugged into that same USB port, does a USB thumbdrive work?

edit: in the same Terminal window you could try ```
 sudo lspci 
``` to see if it is being seen there.

---

### Post by Kitty_Rose7673 on 2009-10-06
Arent the sda things external drives? Well anywho what do I do now?

---

### Post by dhughes on 2009-10-06
> **Kitty_Rose7673 said:**
> Arent the sda things external drives? Well anywho what do I do now?

No they can be internal too, they used to be hda but it changed recently to sda, external drives will show up as sda too.

 Well from what I can see on Google there seems to be ongoing issues with Linux and Motorola, although most of the articles say they have been fixed.

 Did you try the ```
sudo lspci
```  command?

---

