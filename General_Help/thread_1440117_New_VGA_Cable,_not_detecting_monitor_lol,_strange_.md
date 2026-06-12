---
title: "New VGA Cable, not detecting monitor lol, strange issue"
date: 2010-03-27
forum: General Help
---

### Post by ade234uk on 2010-03-27
I bought a new VGA cable M to M from ebay. This was to replace my old cable that was so twisted. Anyway this morning I wake up and Ubuntu is not detecting my BENQ monitor and I am reverted to 800x600 YUk!!, What the hell. 

I checked connections, and restarted again. Again Ubuntu detected 800x600, so I thought I would try my old cable. I booted Ubuntu and it got me to a resolution of 1600x900 and also detected my BENQ monitor.

Now please explain something, I have been using PC's for years, and a monitor cable is just a monitor cable right? Or is the there different types of VGA/Quality type cables lol?

If there is a difference can someone point me in the right direction of where I can buy a half decent VGA monitor cable in the UK?

---

### Post by teejmya on 2010-03-27
No, I'm pretty sure they're one size fits all, if you will.
It might have reset your card settings because it's new, so double check on your Display settings in the Preferences menu.

Oh, and by the way, I would refrain from putting "lol" in the title of your post.

---

### Post by ade234uk on 2010-03-27
Basically my motherboard has onboard graphics so no graphics card. This could be one of the reasons, and a poor quality VGA cable might stop detecting of monitor.

---

### Post by Mark Phelps on 2010-03-27
You're repeatedly posting on the same problem.  

You've already received answers to your newer post on exactly this same problem.

Please do NOT post repeatedly for the same problem.

---

### Post by realzippy on 2010-03-27
[http://en.wikipedia.org/wiki/Display_data_channel](http://en.wikipedia.org/wiki/Display_data_channel)



*"The most common version, called DDC2B, is based on I²C, a serial bus. Pin 12, ID1 is now used as the data pin from the I²C bus, and the formerly-unused pin 15 became the I²C clock; pin 9, previously used as a mechanical key, supplied +5V DC power up to 50mA to drive the EEPROM, this allows the host to read the EDID even if the monitor is powered off..."*

.. there are physically changes concerning the "edid" channel pin in VGA cables.
Many "resolution problem threads" here may be affected...

---

