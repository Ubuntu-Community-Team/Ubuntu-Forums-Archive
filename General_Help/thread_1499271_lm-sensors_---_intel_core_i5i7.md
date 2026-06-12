---
title: "lm-sensors --- intel core i5/i7"
date: 2010-06-01
forum: General Help
---

### Post by plutoniumpenguin on 2010-06-01
Has anybody been able to use 'sensors' to monitor the temperature of one of the newer Intel Core processors?  I have an Intel Core i5, and 'sensors-detect' fails to find any temperature sensor for the cpu, although I can monitor the temperature just fine with the system BIOS (except this is, of course, not very useful).  This was the case in Karmic as well, but at that time I just brushed the failure off as being due to the software not being quite up-to-date.

---

### Post by Ginsu543 on 2010-06-02
As you can see in my siggy, I have a Core i7 920-based system, and lm-sensors can see all four cores plus four hyper-threading "cores." If you look at the bottom panel on the attached pic, you can see the temps for all eight. BTW, this is under Lucid (I haven't tried under Karmic).

---

### Post by plutoniumpenguin on 2010-06-02
bump.

c'mon --- at least a few of you have to be using core i's...

---

### Post by inso_741 on 2010-06-02
'sensors' work fine for me too:)

---

### Post by jocko on 2010-06-02
I've got an i5, and according to [intel's specs]("http://ark.intel.com/Product.aspx?id=43556") it does not have any temperature sensor. The same appears to be true for all i5/i7 desktop cpus.
But lm-sensors should pick up on whatever hardware monitor you have on the motherboard.
My motherboard (Gigabyte P55-UD4) has an it8720 chip with some fan, voltage and temperature sensors (one of the temperature sensors is below the cpu).

---

### Post by Contra75 on 2010-06-03
I have i5 750 on AsRock Pro mobo and sensors show only cpu load, but not the temperature - so they are basically useless, even thou in BIOS it's all clearly displayed. I guess it's a matter of Linux/Ubuntu not catching up with the newer Intel sockets.

---

### Post by Irony on 2010-06-05
Sensors works in Lucid but not karmic because the kernel number is not new enough.

My i5 750 chip is detected though only the temperature of 3 cores is displayed rather than 4.

---

### Post by QQrice on 2010-07-13
[FONT=Arial][SIZE=2]ive got a i5 750 with p55-usb3 mobo, have been trying to get core temps for the last few hours, as ive overclocked..but seems like its not going to happen?? this is what i get when i run sensors [/SIZE][/FONT]

qqriice@qbuntu:~$ sensors
it8720-isa-0290
Adapter: ISA adapter
in0:         +1.36 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.58 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.41 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +2.98 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +0.34 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +3.15 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +0.11 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +2.16 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.23 V
fan1:       1250 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =    0 RPM)
temp1:       +32.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +25.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:       +24.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +0.313 V

[FONT=Arial][SIZE=2]im not sure what temp1,2,3 correspond to wither it be 3 of the 4 cores.. which i doubt, or 1 cpu and 2 spots on mobo...[/SIZE][/FONT]

---

### Post by jocko on 2010-07-13
> **QQrice said:**
> [FONT=Arial][SIZE=2]ive got a i5 750 with p55-usb3 mobo, have been trying to get core temps for the last few hours, as ive overclocked..but seems like its not going to happen?? [/SIZE][/FONT]
As I said in [post 5]("http://ubuntuforums.org/showpost.php?p=9397783&postcount=5"), according to intel's own specs, none of the i5 or i7 desktop cpus have any temperature sensors, so you might just as well give up.
My motherboard (gigabyte p55-UD4) have some sensors, which report these temperatures:
```

temp1:       +38.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +25.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:       +29.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor

```As far as I have managed to figure out, my "temp1" is a thermistor measuring the temperature below the cpu die, "temp2" appears not to be connected (always stays at 25 degrees) and "temp3" is the ambient temperature (today is a hot day...).
From your temperatures and the fact that you have a gigabyte p55 board with the same hardware monitor chipset as I have (it8720-isa-0290), I would guess the same is true for you... So temp1 is as close as you can get to the cpu temperature, although I guess the actual core temperature can rise quicker and become hotter than the thermistor will detect.

---

### Post by QQrice on 2010-07-14
Well there must be someway of getting the temperatures of the CPU cores? if windows can i dont see why ubuntu cant :???:

---

### Post by swalker23 on 2010-07-14
Give me a sec to look up one my old posts.  I got it working right in Karmic and Lucid.


Edit:
[http://ubuntuforums.org/showthread.php?p=8217352#post8217352](http://ubuntuforums.org/showthread.php?p=8217352#post8217352)

I had to do this when Lucid first came out.  Mainly if you put 
```
force_id=0x8860
```
in front of the alphanumeric number it should work.

---

### Post by jocko on 2010-07-15
> **QQrice said:**
> Well there must be someway of getting the temperatures of the CPU cores? if windows can i dont see why ubuntu cant :???:
Hmmm.... If windows really see the core temperatures intel must be lying about their hardware, or maybe I have misunderstood what they mean by "Thermal Monitoring Technologies  -  No" in their specs tables...

With some googling all I can find is [an old thread on the lm-sensors mailing list]("http://lists.lm-sensors.org/pipermail/lm-sensors/2009-September/026738.html") where it appears like there are sensors in core i5, but they need to know how to calibrate the numbers before they add the support (otherwise the sensors would just report some arbitrary numbers which may or may not be anywhere close to the true temperatures).

---

### Post by kubug on 2011-02-02
I know this is an old thread, but since it was the first one I found back when I had the same problem, I figured I'd post my results here.

All I had to do to get my temp readings is to get the 'coretemp' module running. For some reason, lm-sensors didn't pick it up on detection, so I just manually added it to /etc/modules 

```
sudo nano /etc/modules
```

and then add 'coretemp' at the end.

Close and save.

If you want to see if it will work, just run:

```
sudo modprobe coretemp
```

Granted I run a newer kernel than what shipped with Maverick, but it should work even with stock. If not, try out the newer kernel from:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-natty/)

It should work even in Lucid.

---

### Post by Seinfeld on 2011-02-05
Hi..

I really do appreciate your help in this..
I just bought an Intel DPX558SO. Installed Core i7 960.
Using Ubuntu 10.10. With lm-sensors. The Core(2) i.e. third core is reporting 10 degrees higher than all other three cores, even at idle.
I reinstalled the heat sink, applied a proper amount of thermal compound etc.. Still same problem. all other cores, 0,1,and 3 seem to be fine with only 1-2 degrees difference among them
lm-sensors being the only hardware monitoring software available in Linux, I don't have any other way to know.
I don't want to install Windows for trying out Coretemp, Realtemp etc. kind of a hassle here.

Thanks a lot in advance for your help

---

### Post by kubug on 2011-02-06
> **Seinfeld said:**
> Hi..

I really do appreciate your help in this..
I just bought an Intel DPX558SO. Installed Core i7 960.
Using Ubuntu 10.10. With lm-sensors. The Core(2) i.e. third core is reporting 10 degrees higher than all other three cores, even at idle.
I reinstalled the heat sink, applied a proper amount of thermal compound etc.. Still same problem. all other cores, 0,1,and 3 seem to be fine with only 1-2 degrees difference among them
lm-sensors being the only hardware monitoring software available in Linux, I don't have any other way to know.
I don't want to install Windows for trying out Coretemp, Realtemp etc. kind of a hassle here.

Thanks a lot in advance for your help

Temperature difference, even if 10C, between cores is not unheard of. You didn't mention your idle and load temperatures, so I will assume they are within their limits when I say not to worry about the temperature. 
If you googled 'temperature difference between cores' you will find plenty of people asking about this. Just like no two CPU's are made the same, so no two Cores are the same. It's just physics. Enjoy your 960.

---

### Post by Seinfeld on 2011-02-06
kubug

Thanks a lot for you reply..
My idles are 32,31,40,30.. (see that annoying core #2, it reads 40) uhh.:confused:
I don't deny that I am a perfectionist:p, but i can't help it when it comes to my machine :)
Now when loading, temps fluctuate considerably and as some between 60-70 so this different core adds up to some 7-8 above.
By the way, I just upgraded the BIOS to rule it out and no difference... My question now is, does this come from the processor hardware itself and no way of fixing it or an updated kernel or the upcoming distro might cure it by a newer version of lm-sensors??  

Thanks again

---

### Post by kubug on 2011-02-06
Yeah, no BIOS update or Kernel is going to fix that for you. In fact, even a new heatsink isn't (it could bring those load temps down a bit).
It's the CPU hardware. You'll just have to live with it. Or if you have a friend that doesn't care and has the same CPU, swap it out with him.

---

### Post by Seinfeld on 2011-02-06
Thanks very much. I have heard that this is quite common with 45nm quads. It seems that this is the best solution :)
Thanks again :)

---

### Post by inso_741 on 2011-02-08
Run system monitor and check the usage of the core in question...

---

### Post by Seinfeld on 2011-02-08
Hi..

Thanks for the reply... I did.. In fact the difference tend to occur at lower loads. When the processors cools down after some loaded session, the 1,2 and 4 sag nicely to maintain the 30-35 Celsius mar. But this third guy sticks high and drops down to 46. I feel a bit annoyed as I spent some money so I should be satisfied.
I cannot RMA it with Intel as tis might not be considered something major, but..
Now, the problem is there is no other linux application that can efficiently confirm this other than the poor lm-sensors :(. Please read this article and looking forward for your comments. Thanks again...  
[http://www.techpowerup.com/realtemp/docs.php](http://www.techpowerup.com/realtemp/docs.php)

---

### Post by Novak on 2012-01-05
I use Intel® Core™ i5-2410M CPU @ 2.30GHz under Pear OS v3.0 (based on Ubuntu 11.10) and temperatures at idle are:
acpitz-virtual-0
Adapter: Virtual device
temp1:        +48.0&#65533;&#65533;C  (crit = +128.0&#65533;&#65533;C)
temp2:        +67.0&#65533;&#65533;C  (crit = +128.0&#65533;&#65533;C)
temp3:        +29.0&#65533;&#65533;C  (crit = +128.0&#65533;&#65533;C)
temp4:        +45.0&#65533;&#65533;C  (crit = +128.0&#65533;&#65533;C)
temp5:        +21.0&#65533;&#65533;C  (crit = +128.0&#65533;&#65533;C)
temp6:         +0.0&#65533;&#65533;C  (crit = +128.0&#65533;&#65533;C)
temp7:         +0.0&#65533;&#65533;C  (crit = +128.0&#65533;&#65533;C)
temp8:         +0.0&#65533;&#65533;C  (crit = +128.0&#65533;&#65533;C)
To me, it does't look good at idle.Is it possible to fix using GRUB config or any settings?Thank you.

---

