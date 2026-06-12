---
title: "Configuring ADSL pppoE connection with SmartAX MT841 modem"
date: 2006-04-09
forum: General Help
---

### Post by Maccabee on 2006-04-09
Hi
   Can any one tell me how to configure internet connection in Kubuntu 5.10
My net connection 256kbps works fine in Windows XP.I need to shift it to Kubuntu.

I ve a ADSL pppoE connection with huawei modem  SmartAX MT841 ,connected to my PC via a USB cable.The accompanying CD contains a USB linux driver and instructions for redhat 8.But it too confusing for a newbie like me who knows nothing abt networking.They says the IP address and subnet mask should be configured to some 192.bla.bla and 255.bla,...
Plz tell me where to begin...

---

### Post by xael on 2006-04-10
I don't have exactly the same modem than you, but Ubuntu/ Kubuntu install by default the pppoeconf package, so if you open a terminal, type "sudo pppoeconf" & hit Enter, it'll open the proper tool where you can type your info & if everything goes well, seconds later, you'll be online.

---

### Post by Maccabee on 2006-04-11
But plz tell me whether i need to install any driver since my modem is connected via a USB cable??
Or will Kubuntu doesnt need a driver as XP needed?

---

### Post by Maccabee on 2006-04-11
Help!!!!!!!!!
when i type sudo ppoeconf
a new window pops up and after some scannng complains that it cant find any ethernet concentrator or its not responding
I dunno what this ethernet card is??
But is it needed when my modem is connected via a USB cable??
PLZ ANYONE PROVIDE ME SOME HELP!!!!!!!!!!!!!!!!!!!!!

---

### Post by xael on 2006-04-11
[QUOTE=Maccabee]Help!!!!!!!!!
when i type sudo ppoeconf
a new window pops up and after some scannng complains that it cant find any ethernet concentrator or its not responding
I dunno what this ethernet card is??
But is it needed when my modem is connected via a USB cable??
PLZ ANYONE PROVIDE ME SOME HELP!!!!!!!!!!!!!!!!!!!!![/QUOTE]

You say the system found no Ethernet card, but you know that's wrong 'cause WinXP opens it & establishes a connection, right?. 

So, we've to make Ubuntu see it, how?, easy, try this, unplug the cable & plug it again. In that way, you'll be forcing the system to recognise the device. Next, open the terminal...

---

### Post by jwalantsoneji on 2007-09-07
will it work for broadband connections with username and password and don't have modem installed.
It works fine with windows xp!

---

