---
title: "Pulling out my hair now"
date: 2006-03-29
forum: General Help
---

### Post by HeYeahThat0neGuy on 2006-03-29
Ok. So Creative ZEn STILL not being recognized. I got Limewire to install, but I don't have the latest version of JRE, and as such I can only run it if I open the source code through the terminal. 

PLEASE HELP ME SOMEONE.

When I try to update JRE I get something about permission denied from some file called 13 or something.....](*,)

---

### Post by Ramses de Norre on 2006-03-29
[http://ubuntuforums.org/showthread.php?t=76754]("http://ubuntuforums.org/showthread.php?t=76754") mind the change of version numbers!

And what do you mean by not recognized? Did you mount it? What filesystem is on it?

---

### Post by HeYeahThat0neGuy on 2006-03-29
I plug it in and it doesn't even show that it's connected.

---

### Post by Ramses de Norre on 2006-03-29
```
lsusb
```
Is it mentioned in the output? (compare it to the output without the drive plugged in, the name of the chipset might be different than the name of the mp3 player)

---

### Post by trent dillman on 2006-03-29
Have you tried plugging it in, and leaving it plugged while rebooting?

---

### Post by s_h_a_d_o_w_s on 2006-03-29
This thread might help you with you MP3 player problem. I made it a couple days ago. But i was talking about my pc not recognizing my sony PSP. It might help you out. If it dosen't, i suggest asking aysiu ( the guy who helped me out with my problem. Anyway, it works now so there's a chance it will work for you. 

link: [http://www.ubuntuforums.org/showthread.php?t=150618](http://www.ubuntuforums.org/showthread.php?t=150618)

as for limewire, I strongly suggest Frostwire. It works and looks exactly the same way. I got my version with automatix:


sudo apt-get install automatix

---

### Post by HeYeahThat0neGuy on 2006-03-30
everette@everette:~$ lsusb
Bus 004 Device 006: ID 062a:0000 Creative Labs
Bus 004 Device 005: ID 043d:008a Lexmark International, Inc.
Bus 004 Device 004: ID 099a:5321 Zippy Technology Corp.
Bus 004 Device 003: ID 04cc:1521 Philips Semiconductors USB 2.0 Hub
Bus 004 Device 002: ID 041e:413c Creative Technology, Ltd
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

OK so it shows up there, so why won't it show up on my comp?

ALSO: I tried to download the version of Gnomad2 that has what I need on it (2.8.3), that works with my Mp3 player, but it won't let me. If someone will PLEASE in lehman's terms explain how to install software, I'd appreciate it:)

Thanks a bunch for the help. And as for frostwire, I downloaded it, but when I click the icon, it doesn't do anything.

---

