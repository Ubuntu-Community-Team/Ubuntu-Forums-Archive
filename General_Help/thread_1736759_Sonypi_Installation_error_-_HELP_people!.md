---
title: "Sonypi Installation error - HELP people!"
date: 2011-04-22
forum: General Help
---

### Post by ojuniour on 2011-04-22
I have a 32 bit ubuntu 10.10 installed on my 64bit sony vaio vpccw17fx (4 gb ddr3 , nvidia g210m)..I have installed every updates..making sure I didn't miss anything.

The FN key seems to be working (well at least when I use the FN key ..for the volume(up,down , and mute) it all works. 
The brightness on the other hand doesn't work But the graphics of the brightness slider is being displayed on the top right..but no changes to the brightness what so ever so I did a little reseach and I was told to install the sonypi (after discovering that I dont have it on my machine when I tried to run spicctrl which said something abouth /dev/sonypi directory not found.
Anyway here is the error I keep coming across when I try to make and install the sony pi.

root@valentine-VPCCW17FX:~/sony_acpi# make && sudo make install
make -C /lib/modules/2.6.35-28-generic-pae/build SUBDIRS=/root/sony_acpi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic-pae'
  CC [M]  /root/sony_acpi/sony_acpi.o
/root/sony_acpi/sony_acpi.c:55: warning: initialization from incompatible pointer type
/root/sony_acpi/sony_acpi.c: In function ‘sony_walk_callback’:
/root/sony_acpi/sony_acpi.c:258: error: dereferencing pointer to incomplete type
/root/sony_acpi/sony_acpi.c:260: error: dereferencing pointer to incomplete type
/root/sony_acpi/sony_acpi.c:261: error: dereferencing pointer to incomplete type
/root/sony_acpi/sony_acpi.c: In function ‘sony_acpi_add’:
/root/sony_acpi/sony_acpi.c:274: error: lvalue required as left operand of assignment
/root/sony_acpi/sony_acpi.c:279: error: too few arguments to function ‘acpi_walk_namespace’
/root/sony_acpi/sony_acpi.c:324: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/root/sony_acpi/sony_acpi.c: In function ‘sony_acpi_init’:
/root/sony_acpi/sony_acpi.c:379: error: ‘struct proc_dir_entry’ has no member named ‘owner’
make[2]: *** [/root/sony_acpi/sony_acpi.o] Error 1
make[1]: *** [_module_/root/sony_acpi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic-pae'
make: *** [default] Error 2



i read somewhere that i should open sonypi.c and comment out line that has 'OWNER' in them...but that doesn't work either, so anyway I am a beginner and I need help...Please..
The screen brightness is Killing my eyes. Thank you.

---

### Post by ojuniour on 2011-04-22
BuMp:(

---

### Post by ojuniour on 2011-04-24
Double Bump :(

---

### Post by ojuniour on 2011-04-25
Really? No one at all?, Please Im begging ..I am about to blind with that backlight ..

---

### Post by Quackers on 2011-04-25
I am aware of what sonypi is and what it does, but I have not heard of it being installable in Linux. I thought it was a Windows based thing. 
Is your backlight at full brightness or very dim?

---

### Post by ojuniour on 2011-04-26
> **Quackers said:**
> I am aware of what sonypi is and what it does, but I have not heard of it being installable in Linux. I thought it was a Windows based thing. 
Is your backlight at full brightness or very dim?

I can't control the brightness..its at the BRIGHTEST ...
I mean really it is BLinding...and it get worse when i am using it indoor..(OMG).. you have no idea how bright and white ..I can't just use it. I need help , really.

---

### Post by Quackers on 2011-04-26
Many Vaio users cannot change their screen brightness - including me :-)
Mine's not too bad though as full brightness isn't all that bad to look at.
Do a search on this site or do some googling. Some Vaios can be changed so that it works, but some can't.

---

### Post by ojuniour on 2011-04-26
i have looked and it does seems like you CAN..but the error i am having is the problem..I am on the right track but I just keep running into errors.... that's my main issue right now.

---

### Post by Quackers on 2011-04-26
Where have you found that tells you that you can install sonypi in a Linux system?

---

### Post by ojuniour on 2011-04-27
I search so many forum sites and here.. unless ou don't know anything about linux then that;s undesrstandable...
cut story short..just search sonypi linux on google...infact on this forum search sonypi and you will get your answer..

---

