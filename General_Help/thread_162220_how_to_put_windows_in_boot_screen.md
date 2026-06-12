---
title: "how to put windows in boot screen???"
date: 2006-04-18
forum: General Help
---

### Post by salman16 on 2006-04-18
I installed  Abuntu in 1 of my partions on hard drive and i had 3 partions in my hard drive my windows home was in 1 of them but when i installed the abuntu in abuntu boot screen i cant see the windows .. I dont no what to do any one help me please!!!!!:( :( :( :( :( :-?

---

### Post by DOtSlaSHuCantCME on 2006-04-18
[QUOTE=salman16]I installed  Abuntu in 1 of my partions on hard drive and i had 3 partions in my hard drive my windows home was in 1 of them but when i installed the abuntu in abuntu boot screen i cant see the windows .. I dont no what to do any one help me please!!!!!:( :( :( :( :( :-?[/QUOTE] 

Hello............

Read this page [http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622), especially "Menu Configuration". 

This is the code from that link to boot into windows. 

grub> rootnoverify (hd0,0)
grub> makeactive
grub> chainloader +1
grub> boot

===============================================

**[COLOR="black"][COLOR="Blue"]I think if u install grub in your windows mbr,then grub will chainload with the windows bootloader,then giving you a entry in your menu list.[/COLOR][/COLOR]**
===============================================



===============================================
*This is the entry in my  /boot/grub/menu.lst,which shows the input needed in the menu list to boot windows.(**use it as a guide**,subbing (hd0,0)with your partiotion numbers).*

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

===============================================

Hope this sheds some light on the situation.
=====================================================

EDit: **More specific info**" Load another boot loader to boot unsupported operating systems"

If you want to boot an unsupported operating system (e.g. Windows 95), chain-load a boot loader for the operating system. Normally, the boot loader is embedded in the boot sector of the partition on which the operating system is installed.

   1. Set GRUB's root device to the partition by the command rootnoverify (see rootnoverify):

          grub> rootnoverify (hd0,0)
     

   2. Set the active flag in the partition using the command makeactive6 (see makeactive):

          grub> makeactive
     

   3. Load the boot loader with the command chainloader (see chainloader):

          grub> chainloader +1
     

      `+1' indicates that GRUB should read one sector from the start of the partition. The complete description about this syntax can be found in Block list syntax.
   4. Run the command boot (see boot). 



"i should say there might be another way to do this also".

---

### Post by salman16 on 2006-04-18
its saying the same thing  again "Selected disk does not exist" you want me to send you the print screen?

---

### Post by salman16 on 2006-04-18
this is the p/s [http://rapidshare.de/files/18352566/Screenshot.jpeg.html](http://rapidshare.de/files/18352566/Screenshot.jpeg.html)

---

### Post by DOtSlaSHuCantCME on 2006-04-18
[QUOTE=salman16]its saying "Selected disk does not exist"[/QUOTE]

remenber the Grub naming system?) make sure you pick the right partition.

Where are u planning to install Grub? 

Also do this "find /boot/grub/stage1"  without the quotes  that will tell you your linux root.

---

### Post by salman16 on 2006-04-18
[QUOTE=DOtSlaSHuCantCME]remenber the Grub naming system?) make sure you pick the right partition.

Where are u planning to install Grub? 

Also do this "find /boot/grub/stage1"  without the quotes  that will tell you your linux root.[/QUOTE]


i did pick the right partion but i dnt know where to instail Grub?

---

### Post by DOtSlaSHuCantCME on 2006-04-18
If you used the example from the link you would use your specs,if u have one hard drive with 3 partitions and i believe you said windows was on the first partition,then
the grub naming would be (hd0,0)if linux is on third partition then it would be (hd0,2).

---

### Post by salman16 on 2006-04-18
i understand now  the first partion was empty and there is 2 files on my dekstop "hda5" and "hda6" i think hda6 is windows

---

### Post by DOtSlaSHuCantCME on 2006-04-18
[QUOTE=salman16]i did pick the right partion but i dnt know where to instail Grub?[/QUOTE]

Its up to you where to install it (choices rule) install it on ( hd0,0)this will put Grub on windows mbr ,giving you a menu list with ubuntu and windows options to boot.

---

### Post by salman16 on 2006-04-18
yeah im trying to instail but its saying the disk is not exist?

---

### Post by DOtSlaSHuCantCME on 2006-04-18
[QUOTE=salman16]yeah im trying to instail but its saying the disk is not exist?[/QUOTE

that happens when u type root?

==============================================
if you have a live CD try this method:This is from a GruB restore guide.

1. pop in the live cd, boot from it until you reach the desktop
2.open a terminal window or switch to a tty.
3.type"grub"
4.type "root (hd0,6)" ,or whatever your harddisk +boot partition numbers are.
5.type"setup" (hd0)" ,or whatever your harddisk nr is
6.Quit grub by typing "quit".
7.reboot.

---

### Post by salman16 on 2006-04-18
but the thing is i dnt understand its saying "Selected disk does not exist" 


Thanks for your held by da way;)

---

### Post by salman16 on 2006-04-18
no i dnt have the live cd but i have the cd u installing abuntu ;)

---

### Post by salman16 on 2006-04-18
yh thats whats happends when i type "make active part"

---

### Post by DOtSlaSHuCantCME on 2006-04-18
if u have xp cd put in drive, boot from it,after boot at prompt ,type rescue.At next prompt type fixmbr (maybe in caps).

then boot from a live cd (knoppix ,ubuntu,ect)and install grub **to your Windows partition**.


Do the above last, if all else fails.

---

### Post by salman16 on 2006-04-18
yeah true i have to reboot my pc and instail windows again.. thanks for your help;)

---

### Post by DOtSlaSHuCantCME on 2006-04-18
[QUOTE=salman16]yh thats whats happends when i type "make active part"[/QUOTE]

for grub>rootnoverify ,try(hd0,1) if not, then try (hd0,2).

WIndows was not installed? maybe thats it ;-)

---

### Post by salman16 on 2006-04-18
GNU GRUB  version 0.95  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub> rootnoverify (hd0,1)

grub> makeactive

Error 21: Selected disk does not exist

grub> rootnoverify (hd0,2)

grub> makeactive

Error 21: Selected disk does not exist

grub>



its same... but i found the stage1 in file system/boot/grub

---

### Post by salman16 on 2006-04-18
windows was installed before i installed abuntu

---

