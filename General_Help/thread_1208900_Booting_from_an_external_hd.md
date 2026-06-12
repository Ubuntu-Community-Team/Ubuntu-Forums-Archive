---
title: "Booting from an external hd"
date: 2009-07-09
forum: General Help
---

### Post by touchdownjesus4 on 2009-07-09
I have ubuntu Jaunty installed on my desktop computer and I wanted to test out windows 7 that is installed on an external hd. How would I go about booting from the external hd and running windows 7? Thanks for the help

---

### Post by lisati on 2009-07-12
If your computer can handle it, there will usually be some key you press at boot time to change the order the system checks the attached devices. On my laptop it's F12, and on my desktop it's the Esc key.

---

### Post by gobberpooper on 2009-07-12
Remember that if you're booting from an external storage device, it'll be slower.
But when you start your computer, the company logo shows up and it shows you which button does what. Look for the Boot Options or Advanced Boot Menu. Before Ubuntu loads press the button to do that, and then select the option you want.

---

### Post by jskandhari on 2009-07-12
There are two ways...

One is the at boot time..
hit the boot menu option and click from usb haRDDISK ( make sure if there are more than 1 partition on the HDD the win7 partition has the boot flag if not use partition editor in ubuntu to give it)

second is in menu.lst located in boot>grub | but first hit "c" in grub and try typing these there and hit "b" after making the changes to test there and then if it works or not.

make the following changes
title Win7
root (hd1,X) |X is the partition
makeactive
savedefault
chainloader +1

---

### Post by TeamJ on 2009-07-12
it will be v. slow to load heavy windows at about 50mps (I know it is supposed to be 400 or 480, etc. but most external HDDs are 50)
in fact I only managed 50 after taking it apart and changing the jumpers.
you could take it apart, most of these you will just find a HDD and an adapter, cooling thingy, etc. and then swapping your current internal HDD with the win7 one and booting from that.

---

