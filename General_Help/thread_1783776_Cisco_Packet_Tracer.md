---
title: "Cisco Packet Tracer"
date: 2011-06-16
forum: General Help
---

### Post by shamz_71 on 2011-06-16
I need detailed steps of installing Cisco paket tracer on Ubuntu 11.04

---

### Post by elliotbeken on 2011-06-16
Do you want to use wine or not i use wine to run the windows one?

---

### Post by kukker32 on 2011-06-16
step 1:
Download the .bin file somewhere, i downloaded it from cisco.netacad.net

step 2:
for easiest use, place it in your home folder. for more easy use, rename the file to packet.bin

step 3:
start up terminal and navigate to your home folder
cd /home/*your username*

step 4:
innitiate the installation in terminal by typing.
sh packet.bin

step 5:
read and accept the EULA

step 6:
type in your admin pass in terminal

step 7:
wait for installation to finish

step 8:
you can now start packet tracer from applications > internet > cisco packet tracer..

---

### Post by shamz_71 on 2011-06-16
how to download the .bin file. ? :S

"To  install the Linux BIN packages, set the permission to be executable   (chmod +x PacketTracer52_*.bin) then execute the binary in the  terminal."
i dont get this . Above statement is from the following link,
[http://www.packettracer.info/packet-tracer-5-3-2-download.html](http://www.packettracer.info/packet-tracer-5-3-2-download.html)

---

### Post by kukker32 on 2011-06-16
> **shamz_71 said:**
> how to download the .bin file. ? :S

"To  install the Linux BIN packages, set the permission to be executable   (chmod +x PacketTracer52_*.bin) then execute the binary in the  terminal."
i dont get this . Above statement is from the following link,
[http://www.packettracer.info/packet-tracer-5-3-2-download.html](http://www.packettracer.info/packet-tracer-5-3-2-download.html)

chmodding shouldn't be necessary, I didn't need to do it..
but if you want to and or are needed to then the command is.

```
sudo chmod 777 /home/packet.bin
``` (asuming that you rename the file to packet.bin to make the typing process easier)

but yet again shouldn't be necessary

I've uploaded a non pirated, and 100% legal copy of mine on the following link.
.[http://dl.dropbox.com/u/10503980/PacketTracer532_i386_installer-deb.bin](http://dl.dropbox.com/u/10503980/PacketTracer532_i386_installer-deb.bin)

---

### Post by shamz_71 on 2011-06-18
> **kukker32 said:**
> step 1:
Download the .bin file somewhere, i downloaded it from cisco.netacad.net

step 2:
for easiest use, place it in your home folder. for more easy use, rename the file to packet.bin

step 3:
start up terminal and navigate to your home folder
cd /home/*your username*

step 4:
innitiate the installation in terminal by typing.
sh packet.bin

step 5:
read and accept the EULA

step 6:
type in your admin pass in terminal

step 7:
wait for installation to finish

step 8:
you can now start packet tracer from applications > internet > cisco packet tracer..

THanks man ... worked for me ... Cant get more simpler than that

---

### Post by kasl33 on 2011-06-19
> **shamz_71 said:**
> I need detailed steps of installing Cisco paket tracer on Ubuntu 11.04

Try this: [Installing Cisco PacketTracer 5.3.2 on 64-bit Ubuntu or Debian]("http://kaslit.com/blog.php?id=70")

---

### Post by shamz_71 on 2011-06-20
Its working for me now , thanks

---

### Post by shamz_71 on 2011-06-21
Is there any difference b/w the files of Cisco Pacter Tracer in UBuntu and Cisco packet tracer in windows ?
I was working on my laptop (ubuntu) , saved one file in Cisco packet tracer.
I had some doubts about my work , so i decided to take my file to the institute which runs windows pc . When i copied my packet tracer file , it couldn't open :S

---

### Post by shamz_71 on 2011-06-24
Anyone?

---

### Post by Xillix on 2011-10-11
> **kasl33 said:**
> Try this: [Installing Cisco PacketTracer 5.3.2 on 64-bit Ubuntu or Debian]("http://kaslit.com/blog.php?id=70")

Got it to work on Ubuntu 11.04 64bit, thanks a lot!

---

