---
title: "Ubuntu thinks laptop monitor is square.  its widescreen"
date: 2009-09-08
forum: General Help
---

### Post by Chicanob12 on 2009-09-08
Hey im a newb and I am looking for all the help I can get. I just got a Lenovo Y530 and I installed ubuntu 9.04 through wubi and everything works.  The only problem I have is that my screen is not filled.  I have to black bars on the left and right side of the screen as if the screen were square.  I tried going to the display option and trying to change the settings for the screen.  The resolution on my screen is suppose to be 1280 x 800.  Unfortunetly it won't give me that as an option.

please help....thanks

---

### Post by Seq on 2009-09-08
From a quick search, that machine seems to come with a Nvidia GPU. Have you installed the nvidia drivers?

---

### Post by cak3 on 2009-09-08
Yea, I would try installing the proprietary drivers. You can do that (if you haven't yet) by going to system>administration>Hardware Drivers.

---

### Post by Chicanob12 on 2009-09-09
> **cak3 said:**
> Yea, I would try installing the proprietary drivers. You can do that (if you haven't yet) by going to system>administration>Hardware Drivers.

sorry guys but i do not have Nvidia i actually have an Intel 4 series chip.  I think intel is part of the open source project. But I still tried to download drivers and it says everything is fine.

Thanks for the response guys keep em comming hopefully lol.


Edit: here are the specs i figured on my graphics card

Intel (R) 4 Series Express Chipset Family
Intel (R) 4500MHD
1280 x 800
32 bit
60Hz
this should be the proper settings on my screen in ubuntu on my lenovo y530

---

### Post by hellmet on 2009-09-09
What does 'Fn+F7' do? F7 on my thinkpad is LaptopScree/External Monitor key.

---

### Post by ithinkitschad on 2009-09-09
Hey, if your running Jaunty you might just need to roll back to the 2.4 drivers. Just follow [this tutorial]("https://wiki.edubuntu.org/ReinhardTartler/X/RevertingIntelDriverTo2.4"). Hope that helps. Good luck.

---

### Post by Chicanob12 on 2009-09-09
Just wondering if anyone thinks that maybe this is being caused because Ubuntu is being ran under wubi instead of being fully installed?  I've heard that installing through wubi can screw up the system sometimes, any thoughts?

---

### Post by ithinkitschad on 2009-09-09
> **Chicanob12 said:**
> Just wondering if anyone thinks that maybe this is being caused because Ubuntu is being ran under wubi instead of being fully installed?  I've heard that installing through wubi can screw up the system sometimes, any thoughts?

Did you try reverting the driver yet?

---

### Post by Chicanob12 on 2009-09-09
> **ithinkitschad said:**
> Did you try reverting the driver yet?


sry no not yet i just got home im going to try it right now if i can.  Its my bday and I have people starting to comeover so I might not even have a chance but I will let you know as soon as possible

---

### Post by Chicanob12 on 2009-09-09
okay it works but now everytime i start my laptop it says running low graphics, it runs very choppy, and it wont let me run compiz any more. suggestions?

---

### Post by Chicanob12 on 2009-09-12
SOLVED thank you BitJunkie (on a different thread) showed me the link to a different thread that actually ended up solving my issue.  I downloaded "xresprobe" from synaptic and it worked like a charm!

---

