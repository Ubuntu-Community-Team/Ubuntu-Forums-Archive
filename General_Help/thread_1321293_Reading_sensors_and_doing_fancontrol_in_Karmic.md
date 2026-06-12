---
title: "Reading sensors and doing fancontrol in Karmic"
date: 2009-11-09
forum: General Help
---

### Post by DeMus on 2009-11-09
Hi,
In Hardy and Jaunty I managed to read the motherboard sensors and control the fan speed accordingly.
Now, on 2 extra disks, I installed Karmic (to test it) and want to do the same. But it doesn't work.
I only see a few sensors, just the 4 in the 4 cores of my CPU. This is caused by the kernel 2.6.31. When I used that version in Jaunty it did the same.
But programs like pwmconfig and fancontrol are no longer there.

Any idea how to do this?

---

### Post by whitethorn on 2009-11-09
I had some problems with lm_sensors as well.  I'm not sure if they're fixed atm, I downloaded the binaries and compiled them myself there are a couple dependencies but you can get those installed with apt-get (oh important for it to install properly (checkinstall) you first have to purge all the lm_sensors packages in apt-get a.k.a sensors3 sensors4 and lm-sensors).  

But you might want to try running sensors-detect and see if that works b4 compiling it yourself.

Have you run 

```
sudo sensors-detect
```

and agreed to the different sensor tests? You might first need to load the proper module.  You should get a list of modules at the end.  If there's one listed which shows the proper driver then you need to get it to load at boot.  There's two ways which work. 

1) adding the name of the modules to /etc/modules
2) adding 
> 
modprobe module-name 

to your /etc/rc.local

I think that should do it.  After the proper module is loaded you should be able to *see* your fan speeds after a reboot (check to make sure)  then pwmconfig and fancontrol should work.  Although I still haven't really figured how to fancontrol to start on bootup (I got it in my sessions).

---

### Post by DeMus on 2009-11-10
> **whitethorn said:**
> I had some problems with lm_sensors as well.  I'm not sure if they're fixed atm, I downloaded the binaries and compiled them myself there are a couple dependencies but you can get those installed with apt-get (oh important for it to install properly (checkinstall) you first have to purge all the lm_sensors packages in apt-get a.k.a sensors3 sensors4 and lm-sensors).  

But you might want to try running sensors-detect and see if that works b4 compiling it yourself.

Have you run 

```
sudo sensors-detect
```

and agreed to the different sensor tests? You might first need to load the proper module.  You should get a list of modules at the end.  If there's one listed which shows the proper driver then you need to get it to load at boot.  There's two ways which work. 

1) adding the name of the modules to /etc/modules
2) adding 

to your /etc/rc.local

I think that should do it.  After the proper module is loaded you should be able to *see* your fan speeds after a reboot (check to make sure)  then pwmconfig and fancontrol should work.  Although I still haven't really figured how to fancontrol to start on bootup (I got it in my sessions).

Wow, thanks for your answer.
But what you write is not so easy. Where do I download which modules and how do I compile them? This is a bit over my head.
I did install lm-sensors and did sensors-detect. It found a few which I can add to an applet showing in the upper panel. Others, including fan-speed, are not visible.
Any reason why this is different in Karmic, compared to the former versions?

---

### Post by hal8000 on 2009-11-10
> **DeMus said:**
> Wow, thanks for your answer.
But what you write is not so easy. Where do I download which modules and how do I compile them? This is a bit over my head.
I did install lm-sensors and did sensors-detect. It found a few which I can add to an applet showing in the upper panel. Others, including fan-speed, are not visible.
Any reason why this is different in Karmic, compared to the former versions?


Hallo DeMus. At the end of running sudo sensors-detect you will see output similar to:


--snip--
Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `w83627hf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `Winbond W83627THF/THG Super IO Sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
w83627hf
#----cut here----

Do you want to add these lines automatically? (yes/NO)
--snip--

Please note you have to type "yes" without the quotes which modifies
/etc/modules

Then next time you run sensors you should see:

anc@orac:~$ sensors
w83627thf-isa-0290
Adapter: ISA adapter
VCore:       +1.42 V  (min =  +0.00 V, max =  +3.84 V)   
+12V:       +11.73 V  (min =  +6.75 V, max = +13.32 V)   
+3.3V:       +3.33 V  (min =  +3.14 V, max =  +3.47 V)   
+5V:         +5.04 V  (min =  +4.75 V, max =  +5.25 V)   
-12V:        +0.72 V  (min = -14.91 V, max = -14.91 V)   ALARM
V5SB:        +5.05 V  (min =  +4.76 V, max =  +5.24 V)   
VBat:        +3.14 V  (min =  +2.40 V, max =  +3.60 V)   
fan1:       2909 RPM  (min = 2657 RPM, div = 2)
CPU Fan:    2766 RPM  (min = 2500 RPM, div = 4)
fan3:       2616 RPM  (min = 1473 RPM, div = 4)
M/B Temp:    +20.0°C  (high = -99.0°C, hyst = +124.0°C)  sensor
--snip--

or whatever lm sensors shows for your motherboard.

You dont have to compile any modules and no need to modify rc.local
(although it may be possible to use rc.local), I just let sensors-detect
do the work.

---

### Post by forficula on 2009-11-12
I have a similar problem in that with Jaunty I could see the CPU temperature using ksensors (under Gnome).  Now ksensors appears not to work and the only temperature reading I get is for the GPU - the CPU sensor just shows 22 degrees.  When I type the sensors command, it shows a temperature close to 22 - clearly wrong!  I have set up lmsensors and done sensors-detect.

---

### Post by ernierasta on 2009-11-17
Hi everybody,
i don't know if you have the same problem as me, but on Asus M4A785TD-V EVO there is conflict between ACPI and it87 driver, so I had to add kernel option into /etc/default/grub:
so change:
GRUB_CMDLINE_LINUX=""
into:
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"

But here is a WARNING! It can make your system unstable! For me it is working ok, and in past this control was turned off, so it should be safe, but consider it.

So sensors are working ok for now, but I have some problems with fancontrol, i have strange fillings that fancontrol scripts are messed a bit, but i will investigate it.

Few times fancontrol started to work, but after restart it was gone. Maybe it is because I am starting fancontrol manually?

BELOW - NOT TESTED WELL, JUST IDEAS, DON'T TRY IT I IF YOU DON'T WANT TO EXPERIMENT!

[SIZE="1"]EDIT: I found out what is going on! I don't know why, but in my case after reboot have pwm1_enable set to 0, so i have to make (in terminal):

```

sudo -i
echo 1 >/sys/devices/platform/it87.656/pwm1_enable

```

Again BE CAREFUL! If fancontrol is not working you can burn your CPU!

But if you don't have the same motherboard it will be in different place! 
I will put it into rc.local (or into fancontrol scripts) and should be ok.[/SIZE]

Good luck!

---

