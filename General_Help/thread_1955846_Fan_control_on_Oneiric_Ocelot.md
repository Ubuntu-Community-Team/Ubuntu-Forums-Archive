---
title: "Fan control on Oneiric Ocelot"
date: 2012-04-10
forum: General Help
---

### Post by Basher101 on 2012-04-10
Hello fellow members ):P

I tried to cut the CPU fan speed to 50% (what it was running on Windows with a program from the motherboard driver disc) but it runs with 100% speed all the time otherwise, which is rather annoying, since Ubuntu will never use that much CPU that it needs such cooling.

I tried lm-sensors and pwmconfig, but it does not slow down.

what i got so far:

```
# pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following devices:
   hwmon0/device is coretemp
   hwmon1/device is f71889a

Found the following PWM controls:
   hwmon1/device/pwm1
   hwmon1/device/pwm2
   hwmon1/device/pwm3

Giving the fans some time to reach full speed...
Found the following fan sensors:
   hwmon1/device/fan1_input     current speed: 1111 RPM
   hwmon1/device/fan2_input     current speed: 0 ... skipping!
   hwmon1/device/fan3_input     current speed: 0 ... skipping!

Warning!!! This program will stop your fans, one at a time,
for approximately 5 seconds each!!!
This may cause your processor temperature to rise!!!
If you do not want to do this hit control-C now!!!
Hit return to continue: 

Testing pwm control hwmon1/device/pwm1 ...
  hwmon1/device/fan1_input ... speed was 1111 now 1111
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon1/device/pwm1,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? n

Testing pwm control hwmon1/device/pwm2 ...
  hwmon1/device/fan1_input ... speed was 1111 now 1113
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon1/device/pwm2,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? n

Testing pwm control hwmon1/device/pwm3 ...
  hwmon1/device/fan1_input ... speed was 1111 now 1111
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon1/device/pwm3,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? n

Testing is complete.
Please verify that all fans have returned to their normal speed.

The fancontrol script can automatically respond to temperature changes
of your system by changing fanspeeds.
Do you want to set up its configuration file now (y)? y
What should be the path to your fancontrol config file (/etc/fancontrol)?  

Select fan output to configure, or other action:
1) hwmon1/device/pwm1    3) Just quit       5) configuration
2) Change INTERVAL  	 4) Save and quit    
select (1-n): 1

Devices:
hwmon0/device is coretemp
hwmon1/device is f71889a

Current temperature readings are as follows:
hwmon0/device/temp1_input	33
hwmon0/device/temp2_input	23
hwmon0/device/temp3_input	26
hwmon0/device/temp4_input	30
hwmon0/device/temp5_input	28
hwmon1/device/temp1_input	33
hwmon1/device/temp2_input	37
hwmon1/device/temp3_input	31

Select a temperature sensor as source for hwmon1/device/pwm1:
1) hwmon0/device/temp1_input
2) hwmon0/device/temp2_input
3) hwmon0/device/temp3_input
4) hwmon0/device/temp4_input
5) hwmon0/device/temp5_input
6) hwmon1/device/temp1_input
7) hwmon1/device/temp2_input
8) hwmon1/device/temp3_input
9) None (Do not affect this PWM output)
select (1-n): 8

Enter the low temperature (degree C)
below which the fan should spin at minimum speed (20): 38

Enter the high temperature (degree C)
over which the fan should spin at maximum speed (60): 58
/usr/sbin/pwmconfig: Zeile 926: [: -eq: Einstelliger (unärer) Operator erwartet.
/usr/sbin/pwmconfig: Zeile 952: [: -eq: Einstelliger (unärer) Operator erwartet.

Enter the PWM value (0-255) to use when the temperature
is over the high temperature limit (255): 255

Common Settings:
INTERVAL=10

Settings of hwmon1/device/pwm1:
  Depends on hwmon1/device/temp3_input
  Controls 
  MINTEMP=38
  MAXTEMP=58
  MINSTART=150
  MINSTOP=0
  MAXPWM=255

Select fan output to configure, or other action:
1) hwmon1/device/pwm1    3) Just quit       5) configuration
2) Change INTERVAL  	 4) Save and quit    
select (1-n): 4

Saving configuration to /etc/fancontrol...
Configuration saved

```

If anyone wonders why 1111 RPM are the maximum, it is because my CPU cooler is the Alpenföhn Himalaya, which uses the Wingboost fan (140 mm), which have the best cooling in low to mid speeds compared to others.

I also let the Fan run on 50% speed when under load, i made benchmarks with Prime95 to see how much of a difference 100% and 50% speed would make. With 50% speed it got mere 3 °C hotter, which was fine for me to let it run 50% all the time.

---

### Post by zeljkojagust on 2012-04-10
Check out this thread: [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)
By following it I was able to fully customize all my fans on one old Intel server.

---

### Post by Basher101 on 2012-04-10
> **zeljkojagust said:**
> Check out this thread: [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)
By following it I was able to fully customize all my fans on one old Intel server.

thanks, i found a similar how-to i followed here [http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu](http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu)

also when i actually use pwmconfig my CPU fan does NOT slow down or stop whatsoever..it stays solid on those 1111 RPM

---

### Post by zeljkojagust on 2012-04-10
I know lm-sensors won't work on all chips. And if your chipset does not support fan control management than it's worthless to even try. So... first you should confirm your chipset, check it's features on the web, and than maybe try and ask vendor directly for support. Nothing else comes to mi mind now, hope other members will come with something smarter.

---

### Post by Basher101 on 2012-04-10
> **zeljkojagust said:**
> I know lm-sensors won't work on all chips. And if your chipset does not support fan control management than it's worthless to even try. So... first you should confirm your chipset, check it's features on the web, and than maybe try and ask vendor directly for support. Nothing else comes to mi mind now, hope other members will come with something smarter.

thanks for your help so far

edit: googeling my chipset does not get me anything, only posts from others that tried pwmconfig but somewhat failed and ask for help.

---

### Post by Basher101 on 2012-04-10
i forgot to mention that i cannot set the CPU fan speed in the BIOS. I can controll all the other fans on the case with manual control over the Voltage, whith knobs at the front panel of the case.

---

### Post by zeljkojagust on 2012-04-10
Did you consider buying CPU fan with external speed control? :)

---

### Post by Basher101 on 2012-04-10
> **zeljkojagust said:**
> Did you consider buying CPU fan with external speed control? :)

it would be a problem to implement. Also i have no $ for anything^^ If you take a look at my sig and what hardware i am using you would know why...

---

### Post by Basher101 on 2012-04-10
After a reboot the changes took effect. Thanks for all the help anyways! :popcorn:

only weird thing now is, when i type ```
sensors
``` i get 0 RPM shown...but whatever, i can see the fan spins, it spins slow, and that is exactly what i wanted :guitar:

---

### Post by zeljkojagust on 2012-04-11
I got 0 RPM also when was configuring lm-sensors, up until I properly configured lower/upper RPM limit form my fans. Than I got correct RPM count also.

---

