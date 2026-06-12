---
title: "Wake On Lan Magic Packet - Can Ubuntu see it?"
date: 2012-03-13
forum: General Help
---

### Post by quakes on 2012-03-13
Hi :) 

I've searched alot for this and can't seem to gather any information, I use a remote for my Ubuntu HTPC that can wake the computer but when the media centre crashes the remote functions all stop working and I need to ssh in to restart the Front End.

My question is does anyone know if Ubuntu can see the Magic Packet if it is sent whilst the computer is on? Would love to make a script that could restart the Front End on receiving that Event.

Thank you :) 

quakes

---

### Post by r+9 on 2012-03-13
First I believe you have to be on a Wired connection to use the Wake-On-Lan (you didn't specify but many networks are all wifi no-a-days)

Second you will need to study up on how to read packets promiscuously.  I'm not very savvy on it myself.  If you can master Wireshark you should be able to figure out what commands and filters you need to catch the WOL packet for other purposes.  If fact you could make your own magic packets. 

More practically, you might be able to write a script that monitors the Media-center processes and restart them when they fail.  That way you don't have to mess with packets at all. 
(bonus this will work on a wireless system)

---

### Post by quakes on 2012-03-13
Thanks for replying :) 

Gonna give Wireshack a look - its nice to have direction :)

My Media Centre is unfortunately freezing not crashing, Ubuntu thinks the process is running fine maybe i should concentrate my efforts on helping with the addons that are causing it :)

Thanks again for the advise my initial research is showing that its promising :)

quakes

---

