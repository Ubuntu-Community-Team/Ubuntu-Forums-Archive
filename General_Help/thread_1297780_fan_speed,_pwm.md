---
title: "fan speed, pwm"
date: 2009-10-22
forum: General Help
---

### Post by penguisher on 2009-10-22
Hello everyone,

First of all I need to say, I don't know if this thread is in the right section. If it isn't, my apologies, could you pleasse move this thread.

My system specs:
Intel core2duo e7400
Arctic freezer 7 pro CPU cooler
MSI G31M3-F
4 gb Corsair ddr2-800 ram
500 gb WD black.

I run ubuntu 9.04 server edition.

The problem is that my fan speed is very high. I have installed lm-sensors and I made a screenshot from the output.
[http://img49.imageshack.us/img49/6517/temps.png](http://img49.imageshack.us/img49/6517/temps.png)

The bios is up to date and gives the same value as CPU: in lm-sensors. I think it is a little bit weird that my fan speed is that high and I think it is a little bit strange that the readings say: CPU: +44.0 C and core0 and core1 say around +35.0 C. these temps are under idle conditions.

I am trying to let ubuntu automatically adjust the fanspeeds to normal values, I don't want to manually set them, because I don't want my system to burn down if the system load is higher and the cpu temperature increases. If the temperature increases the fanspeed should automatically increase too.

Well I used a guide for setting up pwm which should do that for me. The problem is: I have a f71882fg driver and that one doesn't support pwm.

Is there another solution to reduce my cpu fanspeed and the noise? 

Are these temps even normal for my specs? I mean my desktop pc has a intel c2q q6600 with boxed cooler and even that one has a lower temp and lower fan speed when idle. I think my sensor on my motherboard is corrupt, is that possible? Because I use the amd variant of the cooler on my amd x2 4400+ and that one doesn't get a higher temp than 35 on normal load and the fan speed is around 1800 rpm. I really don't get it, I already re-installed the fan with new cooling paste, but that didn't change a thing.

---

### Post by P4man on 2009-10-22
Yeah those temps look real to me. If you cant find a software solution, consider buying a 5 euro fan controller. With that monster cooler on a fairly cool cpu, you could run it at low speed no matter what.

---

### Post by penguisher on 2009-10-22
Ok thank you for your reply, I would like to know what that fancontroler does, can they automatically control your fan speed or do you need to manually set them to a value? Do they adjust if the temperature gets higher? And won't my CPU temp get higher if I set the speed to let's say 1800 rpm?

I have never used a fancontroler before so could you please explain how I should use it?

---

### Post by P4man on 2009-10-22
First of all, doesnt your bios have a setting to ajust fan speed depending on cpu temp?

If it doesnt, I was thinking of a very simple fan controller which just regulates the current to the fan. They are not temperature dependent. Somehting like this:
[http://www.google.com/products/catalog?hl=en&source=hp&q=fan+controller&um=1&ie=UTF-8&cid=5886037019396114494&ei=CCHgStm8N9H24Aa3ws0c&sa=X&oi=product_catalog_result&ct=result&resnum=7&ved=0CB0Q8wIwBg#ps-sellers](http://www.google.com/products/catalog?hl=en&source=hp&q=fan+controller&um=1&ie=UTF-8&cid=5886037019396114494&ei=CCHgStm8N9H24Aa3ws0c&sa=X&oi=product_catalog_result&ct=result&resnum=7&ved=0CB0Q8wIwBg#ps-sellers)


If you want temp varrying fan controller you can buy something more fancy such as

[http://www.google.com/products/catalog?hl=en&source=hp&q=fan+controller&um=1&ie=UTF-8&cid=5204362226888819618&ei=CCHgStm8N9H24Aa3ws0c&sa=X&oi=product_catalog_result&ct=result&resnum=8&ved=0CCEQ8wIwBw#ps-sellers](http://www.google.com/products/catalog?hl=en&source=hp&q=fan+controller&um=1&ie=UTF-8&cid=5204362226888819618&ei=CCHgStm8N9H24Aa3ws0c&sa=X&oi=product_catalog_result&ct=result&resnum=8&ved=0CCEQ8wIwBw#ps-sellers)

They do use their own sensors though, not the bios sensor afaik.

---

### Post by penguisher on 2009-10-22
The only setting I can find is this one: 
CPU SMART TEMP, I can set a temperature target there and then I can set the minimum fan speed in %. So I did this: I set the target to 50 C and the minimum fan speed to 25%. Now my fan speed is around 1100 rpm but my CPU temp is 43 and my core0 and core1 are still 34 C. This is nais, but I hope the sensor on my motherboard is OK. Are these settings safe?? Or can I even try a lower minimimum fan speed?

---

### Post by P4man on 2009-10-22
> **penguisher said:**
> The only setting I can find is this one: 
CPU SMART TEMP, I can set a temperature target there and then I can set the minimum fan speed in %. So I did this: I set the target to 50 C and the minimum fan speed to 25%. Now my fan speed is around 1100 rpm but my CPU temp is 43 and my core0 and core1 are still 34 C. This is nais, but I hope the sensor on my motherboard is OK. Are these settings safe?? Or can I even try a lower minimimum fan speed?

the sensor is actually in the cpu itself, and Im sure it will be ok. Anything below 65-70C is fine, dont worry so much. You have an overdimensioned cooler on a cool running cpu..

---

### Post by penguisher on 2009-10-22
Ok thank you for your help

Now I can sleep without turning off my server :)

---

