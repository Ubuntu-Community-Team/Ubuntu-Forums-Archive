---
title: "Can't check my ink levels sx100"
date: 2010-06-06
forum: General Help
---

### Post by Mortesins93 on 2010-06-06
Hello,
I have a epson sx100 and i can't check my ink levels with esputil. This is what i get when i type the command.

pianoterra@pianoterra-desktop:~$ sudo escputil -r /dev/usblp0 -s
Escputil version 5.2.0-rc1, Copyright (C) 2000-2006 Robert Krawitz
Escputil comes with ABSOLUTELY NO WARRANTY; for details type 'escputil -l'
This is free software, and you are welcome to redistribute it
under certain conditions; type 'escputil -l' for details.

Impossibile aprire /dev/usblp0 in lettura/scrittura: Dispositivo o risorsa occupata

The last line can be translated in: "Can't open /dev/usblp0 in read/write: Device or resource busy"
I tried Qink and it says it can't detect any printers. I even ran it through root.
I tried ink and this is what i get:
pianoterra@pianoterra-desktop:~$ ink -d /dev/usblp0
ink v0.4.1 &#65533; 2007 Markus Heinz

Could not access custom usb device '/dev/usblp0'.
Could not get ink level.

By the way i also tried these commands with /dev/usb/lp0 and it gives me the same message but if i try with /dev/lp0 i get this:
pianoterra@pianoterra-desktop:~$ ink -d /dev/lp0
ink v0.4.1 &#65533; 2007 Markus Heinz

Could not get device id.
Could not get ink level.

So i am guessing there is no /dev/lp0.
I also tried mtink and it says:
"No access to printer device file
Make sure that mtink has the permissions to access the device files"

I also have another problem which is i can't change the permissions of /dev/usblp0 because i stupidly changed them in to read write execute to all using chmod 777 without thinking that the device file isn't executable. Why can't i change the permissions back as they were?

---

### Post by ellgor on 2010-06-07
Hi,

With regard to mtink, start it from a terminal with:

sudo mtink

that should cure the permission problem, there is a simpler ink app called stylus-toolbox, available in synaptic ( I believe ) again if there's an issue with permissions run it from a terminal, first time anyway.

Regards, Ellgor.

---

### Post by Mark Phelps on 2010-06-07
To get mtink to work, the simplest solution is to add yourself to the lp "group", as follows:

Do the following in a terminal: sudo adduser <username> lp

Replace "<username>" with your user name

Then, do "cat /etc/group | grep lp:"

Assuming your username is "bob", you should get something like "lp:x:7:bob"

---

### Post by coldraven on 2010-06-08
I installed the package from Avasys and it shows the levels on a SX115 (all-in-one)

See:
[http://www.epson.co.uk/Store/Printers-and-All-in-Ones/Epson-Stylus-SX115/Drivers-Support?target=article&extn=.html&articleId=3458](http://www.epson.co.uk/Store/Printers-and-All-in-Ones/Epson-Stylus-SX115/Drivers-Support?target=article&extn=.html&articleId=3458)

Download from here:
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

---

### Post by Mortesins93 on 2010-06-08
pianoterra@pianoterra-desktop:~$ sudo mtink
Unknown IEEE 1284.4 error number 69
Unknown IEEE 1284.4 error number 66

this is what i get from sudo mtink. mtink opens and it says there are problems with the communication with the printer and that i should check if the printer is on, if there is paper in the tray, and if there is ink, but i am sure that there is paper, ink and that my printer is on. Sometimes after running mtink, the printer starts working as if it was to print something but then it gets stuck and stops.

I did what Mark Phelps said and this is what i get:
pianoterra@pianoterra-desktop:~$ cat /etc/group | grep lp
lp:x:1001:root,pianoterra
lpadmin:x:108:pianoterra
By the way i am pianoterra and i had already heard about the group thing but i couldn't find the lp group just the lpadmin so i thought i had to create the lp group, which is probably a mistake.

Well i found out that /dev/usblp0 is just a link and i can't manage to change its permissions but i managed to change the permissions of /dev/usb/lp0 to crw-rw-rw-.
But now when i run the command: 
                sudo escputil -r /dev/usb/lp0 -i
I get the following message:
pianoterra@pianoterra-desktop:~$ sudo escputil -r /dev/usb/lp0 -i
Escputil version 5.2.0-rc1, Copyright (C) 2000-2006 Robert Krawitz
Escputil comes with ABSOLUTELY NO WARRANTY; for details type 'escputil -l'
This is free software, and you are welcome to redistribute it
under certain conditions; type 'escputil -l' for details.

Data received for a non opened channel.
Channel is not open.
Impossibile aprire /dev/usb/lp0 in lettura/scrittura: Dispositivo o risorsa occupata

Which as i said before means: "Can't open /dev/usblp0 in read/write: Device or resource busy"
What is a non-opened channel? How come using after opening the directory /dev/usb in terminal and running the following command:     sudo chmod 666 lp0     the permissions change but as soon as i turn off the printer and turn it back on the permissions change back to what they used to be? Do i have to save or something?!?!?
Anyways, thank you for replying and trying to help me out. I hope to solve this problem with your help.

---

