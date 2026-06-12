---
title: "Confused about hardware temp readings w/ Phenom II 940"
date: 2009-12-05
forum: General Help
---

### Post by khamil8686 on 2009-12-05
I just got a AMD Phenom II X4 940 processor and put it in my computer, i had a AMD Athlon 64 X2 processor before which is 65W compared to 125W of heat. Im using lm-sensors to get temp readings which i use conky to display the loads of the cpus and the temps, with the X2 cpu i got a reading with 2 temps per core of the processor, with the phenom i get 3 temp readings, 2 from thermisistor and 1 from a thermal diode, sensors gives me output like this
temp1:       +30.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +33.0°C  (low  = +127.0°C, high = +60.0°C)  sensor = thermal diode
temp3:       +36.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
which reading should i trust?
the low and highs are confusing so i go by the 2nd one which tells me the true limit the cpu should be at which is about 62C, the first one stays below 60C normally but the 3rd one goes above to 60-70C whenever i run virtualbox, which i use to make blackberry themes, rignt now im just staying away from virtualbox so if im supposed to trust the 3rd temp that im not frying my processor :) anyways any help would be appreciated! thank you!

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
Did you rerun sensors-detect since you changed out the CPU?

---

### Post by khamil8686 on 2009-12-05
yes i did rerun sensors-detect and went thru the default options (i added the modules to /etc/modules like it asked, didnt do default yes on that one so i was sure stuff got in there right) it did say amd k10 sensors driver needs to be written, i did some googling on it and ive found places that say its done and places that say its in the works, i would think it wouldnt provide me with any readings if i was missing the appropriate driver? it does say low temp = 127C and high temp = 127C on the first and 3rd temp reading though oddly enaugh, still dont know what thats about, anyways! ive made sure im using the latest package of lm-sensors, 3.0.2 from the ubuntu repos. also ive installed a gnome applet for the displaying of cpu temps which correlates with the lm-sensors readings.
heres a general cooling question. ive heard that over a bit of time the thermal compound sets and lowers temps about 5C, i ordered a tube of arctic silver 5 thermal grease (compound whatever :P) i didnt use it however because the heatsink that came with the retail processor was a beast and had some thermal grease on the heatsink already, so i thought it should perform fine, sould i remove this thermal grease completely from cpu and heatsink and apply the arctic silver? ive read arctic silver is a very good thermal compound, would it be possibly better than what was on the retail heatsink? anyways, thank you for reading my long post, i tend to ramble :) i appreciate your help!

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
Sounds like you got it working well enough... cool. To me thermal paste is thermal paste but it's not a bad idea to change it periodically. Cleaning out all that stuff is always a good idea too. I have fun with the compressed air and make a day of it (5 or more computers sometimes). I wouldn't know if one thermal paste is better than another though. I've actually used thermal paste that was for something in a car... can't remember but I know it was for a car. Worked perfect.

Oh and to determine which of the sensors is CPU run something CPU intensive and see what skyrockets the temp. Forgot to mention that in the last post. Should be listed in Hardware Sensors app as CPU though.

---

### Post by khamil8686 on 2009-12-05
the temp sensors all rise after something cpu intensive, i start virtualbox and #3 is the quickest to rise, followed by #2 and then #1, either way the cpu is listed to be safe at about 62C and #3 goes above that, id rather be safe than sorry and ill try to get the temp down somehow, time to look thru some manuals and do some googling :) think i might give the different thermal paste a try, i know theyre rated at different thermal conductivities so maybe it would help to apply it differently, ive heard 4 rice grain sized drops works better than a central pea sized drop for quad core cpus, im gonna have a day of messing around in my computer hooray! :) anyways, i appreciate your help Sin@Sin-Sacrifice!

---

### Post by khamil8686 on 2009-12-05
the temp sensors all rise after something cpu intensive, i start virtualbox and #3 is the quickest to rise, followed by #2 and then #1, either way the cpu is listed to be safe at about 62C and #3 goes above that, id rather be safe than sorry and ill try to get the temp down somehow, time to look thru some manuals and do some googling :) think i might give the different thermal paste a try, i know theyre rated at different thermal conductivities so maybe it would help to apply it differently, ive heard 4 rice grain sized drops works better than a central pea sized drop for quad core cpus, im gonna have a day of messing around in my computer hooray! :) anyways, i appreciate your help Sin@Sin-Sacrifice!

---

