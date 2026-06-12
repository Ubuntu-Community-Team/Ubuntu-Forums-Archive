---
title: "Start up Manager (Grub) 1.9.12 + Win 7"
date: 2010-01-25
forum: General Help
---

### Post by FabianX2 on 2010-01-25
Hi,

you will find the question in the best my English can offer under the German part

ich habe Win 7 auf einer SSD und Ubuntu 9.10 auf einer SATA Hard Disk installiert. Nun Bootet das jeweilige System das am Sata 0 Port angeschlossen ist. Meine Frage ist wie ich entweder Grub unter Linux oder den Windows Bootmangaer konfiguriere um beim Start ein sys wählen zu können. Ich bin Linux anfänger und habe mich durch endlos viele Tutorials gequält um Ubunt in mühsamer arbeit zu konfigurieren. Die Anpassung von Win 7 hat auch einige Zeit in Anspruch genommen. Ich möchte jetzt nichts falsch machen.

Ich glaube der einfachste Weg sollte sein den Grub Manager anzupassen. In der menu.lst datei dachte ich mir eine weiter Zeile mit den Parametern für den Boot von Windows einzutragen. Ich hatte mir das so vorgestellt:

_titel Microsoft Windows 7_

_ rootnoverify (hd1,**0**)             _

Erklärung: hd1 da die windows platte am 2. Port des Sata Controllers steckt und die Platte am ersten hd0 ist. **",0"** weil die Windows platte nur über eine Partition verfügt. Im Partionsmanager ist meine Linux platte mit dem Pfad /dev/sda angegben genauer gesagt ist /dev/sda1 die partition die ext 3 formatiert ist und mit boot bezeichnet wird. Die Windows Platte mit dev/sdb ganauer ist dev/sdb1 eine 100mb große ntfs partition die mit boot gekennzeichnet ist und dev/sdb2 eine nicht weiter gekennzeichnete Partition im NTFS Format die den rest der Platte in anspruch nimmt.

 
[U]savedefault
makeactive
chainloader +1
[/U] 
Der Kontext in dem die Einträge in meiner menul.lst geschrieben ist sieht allerdings wie folgt aus:

title Ubuntu 9.10, kernel 2.6.31-17-generic
uuid 1716973a-1137-4c3f-a5c8-c9e5c297319a
kernel /boot/vmlinuz-2.6.31-17-generic root=UUID=1716973a-1137-4c3f-a5c8-c9e5c297319a ro splash
initrd /boot/initrd.img-2.6.31-17-generic
quiet


Sollte mich das beunrigen? Ich habe gesehen das eine menu.last.backup datei vorhanden ist. Wie greife ich den auf diese zurück fals etwas schief gehen sollte? (Ich habe kein Diskettenlaufwerk kann also keine normale grup back up floppy erstellen.)

Danke schon mal

Ps: Ich bitte um Nachsicht dür einen Anfänger !!!


The hole question again in the best my english can offer:

I have installed Win 7 and Ubuntu 9.10 on two diffrent Hrad Drives. Now I like to know how to configure Grub. I am a Linux beginner. The divice plugged on first lane of the Sata Controller is the one wich is booting. For the Moment the Linux Disk is the one. So I thought konfiguring the menu.lst of grub should be the simple way to solf my problem. I tought of s.th like that:

_titel Microsoft Windows 7_
 
 _ rootnoverify (hd1,**0**)             _
 
Explanation: hd1 becorse of the Win Device pluged on the second port of the controller. I think the Linux device should be hd 0. And the second 0 becourse of only one partition. 

In the partition manager under Linux the divices are named as following:

/dev/sda1 is the ext 3 partition of Linux with the mark boot. The Windows Device is splitt in /dev/sdb1 a 100mb partition in NTFS also markt boot and /dev/sdb2 not markt with the rest of the disk space also in NTFS.

 [U]savedefault
makeactive
chainloader +1
[/U] 
The entries in the menu.lst look like this:

title Ubuntu 9.10, kernel 2.6.31-17-generic
 uuid 1716973a-1137-4c3f-a5c8-c9e5c297319a
 kernel /boot/vmlinuz-2.6.31-17-generic root=UUID=1716973a-1137-4c3f-a5c8-c9e5c297319a ro splash
 initrd /boot/initrd.img-2.6.31-17-generic
 quiet
 
I have no Floppy to creat a back up disk. The Folder contains a menu.lst.back up data. How could I use it if s.th goes terribly wrong? 

Please help me. I am affraid of runing my sys konfigurations wich cost houres of time !

---

### Post by FabianX2 on 2010-01-25
So habs geschafft!!!  folgendes habe ich im grub menu ergänzt:  
title Windows 7 
rootnoverify (hd1,0) 
makeactive 
chainloader +1  

So nun kann ich win 7 imbootmanager auswählen und es bootet auch. Nur leider gibt es jetzt ein neues problem. Ich kann nur mit meiner p2 tastatur auswählen auf meine usb tastatur reagiert der manager nicht. sie funktioniert vor dem boot loader also im bios usw und nach dem bootloader in win oder linux aber nicht im bootloader... warum zum teufel????

I finally made it. Folling was written to menu.lst:
title Windows 7 
rootnoverify (hd1,0) 
makeactive 
chainloader +1

Now i am able to boot Win 7 out of Grub. But here is the new Problem ...
My usb keyboard is not working in Grub. The P2 is... All the time befor grub (as is Bios and such things) and all the time after (as is Win 7 and Ubuntu) it is working. Why the ******?????

---

### Post by Jackzor on 2010-01-25
Versuchen Sie etwas in Ihrem BIOS über "USB-Legacy-Tastatur zu finden"

Try to find anything in your bios about "USB Legacy Keyboard"

---

