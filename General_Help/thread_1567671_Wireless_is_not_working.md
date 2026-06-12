---
title: "Wireless is not working"
date: 2010-09-04
forum: General Help
---

### Post by namrata agrawal on 2010-09-04
hello freinds,
I am having problem with my wireless connectivity in ubuntu 10.04. i have installed ubuntu alongwith vista in my laptop(Dell INPIRON 1545). everytime i try to connect,it says "Wireless Connection is not available". but wireless is properly working in vista.
 
plz help me out.

---

### Post by JedMeister on 2010-09-04
The fact that it works in Vista is somewhat irrelevant (although at least you know the hardware isn't broken). So is Ubuntu recognising that you have wireless but just not connecting to any networks? Or not recognising your wireless at all?

If its not recognised at all hopefully its just because you don't have the drivers installed. I'd recommend you connect with a wire (ethernet/LAN cable) and check for Hardware drivers (In Ubuntu 10.04 it's System>>Administration>>Hardware Drivers) and see if it finds anything. Hopefully it will, just follow the instructions.

If its recognised but not finding/connecting to networks then I'm not really sure (I'm still a bit of a Linux newb). I have had some experience with wireless chips that just don't seem to work very well with Linux. To find out what yours actually is and if there's a way to get it to work: 
If its an internal card, open the terminal and use the command ```
lspci
``` if its a USB wifi dongle then use ```
lsusb
``` post the response back here and I'll try to give you a hand finding the info that you need. Or perhaps someone more knowledgeable than me will come along and help you :)

---

