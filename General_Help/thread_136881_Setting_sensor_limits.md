---
title: "Setting sensor limits"
date: 2006-02-26
forum: General Help
---

### Post by tadashi on 2006-02-26
I notice during boot up that I get an error message saying "setting sensor limits.... [failed]".  Any ideas on where to start to fix this?

I am running Kubuntu 5.1 on a Sony Vaio VGN-TX670PB.

---

### Post by aggiechemist on 2006-02-26
Sensors is a program that communicates with your motherboard to give feedback on stuff like temps, voltages, fan speeds.

You can monitor it by going to the terminal and just typing sensors (usually).

I think the limits part is about alarms. For instance, I could set an upper limit for my CPU temp of 60 degrees C. If the sensor exceeds that limit, I could have a program notify me.

Why did it fail? Well the most obvious possibility is that your motherboard doesn't work with the sensors system. Some old MBs haven't been made part of the system yet, I've seen this on one of my old laptops. I have no idea if your system can work with sensors or not.

If you really want to learn more, go to the terminal and type man sensors.

But this is NOT a big deal. Nothing is broken, it shouldn't be slowing your system down or anything like that.

Hope that helps.

---

### Post by tadashi on 2006-02-27
thanks I will do some reading.  My motherboard is not too new.  The laptop just came out but I think it uses the same components as the model just before this one, 650, so I think it does have sensors in it.

---

