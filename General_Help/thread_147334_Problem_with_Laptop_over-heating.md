---
title: "Problem with Laptop over-heating"
date: 2006-03-20
forum: General Help
---

### Post by rko618 on 2006-03-20
I have a Dell Inspiron 8500 labtop running Breezy and I am having a problem with my laptop overheading while running Linux.  When the computer gets to hot it will just power off instantly without any warning.  I don't recall this ever happening under Windows (or near as much) so I think the problem is specific to my linux installation.  I am using my laptop on a flat surface (a desk) so I don't think its a problem with airflow and the fan seems to be working.  Also I don't have to be doing anything particular processor intensive when it happens.  Most recently the screen saver was running and it overheated.

Any suggestions?

---

### Post by andlinux21 on 2006-03-20
How old is the laptop and have you tried cleaning it out with air to make sure that its getting good airflow I have never heard about linux causing something to overheat like that

---

### Post by dmizer on 2006-03-20
screensavers are graphics and therefore cpu intensive.  if you have a laptop, i highly suggest you simply change the screensaver to blank screen.

i haven't looked closely, but i suspect the answer to your problem will be here: [http://www.ee.surrey.ac.uk/Personal/G.Wilford/Inspiron8500/#Power_Management_-_ACPI](http://www.ee.surrey.ac.uk/Personal/G.Wilford/Inspiron8500/#Power_Management_-_ACPI)

i highly suggest you do good solid research on this.  if your computer is getting hot enough to default shutoff, you may be endagering other hardware.  i fried a couple of memory slots because of this problem on my toshiba.

also, are you sure the shutdown is temp related?
you can check the temp by typing: cat /proc/acpi/thermal_zone/THM1/temperature

---

### Post by davidfield on 2006-03-20
If your laptop is anything like my Toshiba satellite, i would suggest you go to your nearest camera suppliers, and buy a can of compressed air for cleaning, and clean all the air ducts fans, keyboard etc..

---

### Post by MichaelZ on 2006-03-20
[quote=rko618]I have a Dell Inspiron 8500 labtop running Breezy and I am having a problem with my laptop overheading while running Linux.  When the computer gets to hot it will just power off instantly without any warning.  I don't recall this ever happening under Windows (or near as much) so I think the problem is specific to my linux installation.  I am using my laptop on a flat surface (a desk) so I don't think its a problem with airflow and the fan seems to be working.  Also I don't have to be doing anything particular processor intensive when it happens.  Most recently the screen saver was running and it overheated.

Any suggestions?[/quote] 
I have a Dell too, but a different model (Latitude D600). IIRC, Dell has some tests that you can perform to check if your hardware (CPU, FAN, Hard-disk, etc.) are ok. I think that these tests are called Dell Utilities. When you re-boot your laptop, you should press F8 or F10(sorry, but I do not remember exactly) and then choose to perform the Dell Utilities.

Check if you fan is working fine (with the utilities) and if the ventilation is correct and the holes are not stopped.

Best wishes,
Michael

---

### Post by Frizguru on 2006-04-06
Oddly enough, I had problems with my Dell Inspiron overheating constantly when I was running Windows. I switched to Linux and have had no problems now. Whenever I boot Windows, my computer instantly heats up about 20-40 degrees within about 2 minutes. I didn't even think it was possible.

---

### Post by jimmt on 2006-04-10
I am  having this problem on my Duel Xeon system. Interesting is that it does not happen in Suse or XP; only in Ubuntu. Ubuntu making my system hot? 

It is really bad. I can't do any coding. As soon as I start to compile it overheats and powers off...

EDIT: One more observation. Under Windows and other platforms when I am doing heavy CPU intensive processes the FANS on the CPU's will speed up. However, under (K)UBuntu the fans do not rev up. Instead, they stay the same consistant speed. 

Jim

---

### Post by rko618 on 2006-04-11
update: I think I have fixed the problem.  Unscrewed the fan from the laptop and blew it out with an air can.  

I haven't had it over-heat since but I would still like to install something like lm-sensors to monitor the temperature except as far as I can tell lm-sensors doesn't work on Inspiron 8500s so I'll have to find something else.

I do believe Ubuntu still has trouble controlling the fan speed however, it doesn't seem to be speeding up and slowing down like it should.

---

### Post by albinoloverats on 2006-04-13
I wouldn't mind jumping on this topic whilst it's recent: my HP Pavilion laptop seems to display a rather high reading when I look in /proc/acpi/thermal_zone/THRM/temperature, such as 60'C, sometimes even when only browsing the web it will reach almost 80'C!!!

I'm sure this display is wrong as my laptop will claim to be 40'C when I first turn it on, so I'm really hoping someone could confirm that the sensors are ofset by about 20'C.  Either that or explain how my hardware could survive that heat ;)

---

### Post by xyz on 2006-04-13
What temp is too hot? I realize it depends on what I'm doing.How much should it not exceed say ...while surfing?
> cat /proc/acpi/thermal_zone/THRM/temperature
temperature:             71 C

...while surfing,about 10 tabs open.

Toshiba Satellite A40
IntelR CeleronR
512MB/2.70GHz

Thanks in adv.

---

### Post by xyz on 2006-04-13
Sorry about doubling! I got logged out and didn't realize post was up.

---

### Post by dgrafix on 2006-04-13
:confused: 
Dont know if its related, but my pc (now running linux) never seems to poswesave like it did with windows. The fans and disks are always at full pelt and never seems to go quiet like it used to. Sometimes the disks seem to click off for a second and then kick back in straight away (same noise they make on startup)

---

### Post by jimmt on 2006-04-17
well, I fixed my problem by switching cases. Go figure :p

Jim

---

### Post by testube_babies on 2006-04-17
I had an overheating problem, too.  I solved it by cleaning out my case and buying [one of these]("http://www.newegg.com/Product/Product.asp?Item=N82E16834999413").  Even though my laptop (like yours) is quite a bit larger than the cooling pad, it still takes ~7-15C off of the CPU/hard drive temps.

---

### Post by xyz on 2006-04-18
[QUOTE=xyz]What temp is too hot? I realize it depends on what I'm doing.How much should it not exceed say ...while surfing?

...while surfing,about 10 tabs open.

Toshiba Satellite A40
IntelR CeleronR
512MB/2.70GHz

Thanks in adv.[/QUOTE]
Well no matter what I was doing on my computer, is always showed 71 degrees! So I figured it wasn't possible and found this:
[http://doc.gwos.org/index.php/Lm-sensors_hddtemp](http://doc.gwos.org/index.php/Lm-sensors_hddtemp)
and ran:
sudo apt-get  install hddtemp

then:sudo hddtemp /dev/hda

> th@meander:~$ sudo hddtemp /dev/hda
/dev/hda: TOSHIBA MK4025GAS: 35°C


...much better and the temp varies!!

---

### Post by dmizer on 2006-04-18
[QUOTE=xyz]...much better and the temp varies!![/QUOTE]
except that with hddtemp, you are only monitoring your hard disk temperature, not your cpu temperature.  if you want to monitor your cpu temperature, you'll need to also install and configure lm-sensors from the same link.

---

### Post by xyz on 2006-04-18
[QUOTE=dmizer]except that with hddtemp, you are only monitoring your hard disk temperature, not your cpu temperature.  if you want to monitor your cpu temperature, you'll need to also install and configure lm-sensors from the same link.[/QUOTE]
Thanks for letting me know.
Following the 'howto-link' I indicated, I installed sensors but when I run it:
> th@meander:~$ sensors
bash: sensors: command not found
th@meander:~$ sudo -s
root@meander:~# sensors
bash: sensors: command not found

Do you have any ideas as to why this is happening?

---

### Post by xyz on 2006-04-19
The install of 'sensors' got somehow messed up but went through the procedure again. I can run
```
sensors
```
> th@meander:~$ sensors
eeprom-i2c-0-51
Adapter: SMBus I801 adapter at d880
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

eeprom-i2c-0-50
Adapter: SMBus I801 adapter at d880
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

adm1032-i2c-0-4c
Adapter: SMBus I801 adapter at d880
M/B Temp:    +43°C  (low  =   -65°C, high =  +127°C)
CPU Temp:  +44.1°C  (low  = +28.0°C, high = +72.0°C)
M/B Crit:   +127°C  (hyst =  +122°C)
CPU Crit:    +82°C  (hyst =   +77°C)

Now is that good/bad? What does it mean???

---

