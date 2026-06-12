---
title: "Temperture Sensors and Fan Control"
date: 2011-05-03
forum: General Help
---

### Post by RFXCasey on 2011-05-03
Hello, I installed sensors with sudo apt-get iinstall lm-sensors. After installing I run 

```
sudo sensors-detect 
```

and after letting it run and telling it yes to all sensor scans the summary says 

```
Driver 'via686': * Chip 'VIA VT82c686 Integrated Sensors' (confidence: 9) To load everything that is needed, add this to /etc/modules:via686a. 
```

I added the via686a automatically when prompted. To which the program responds 

```
'Monitoring programs won't work until the need modules are loaded. You may want to run '/etc/init.d/module-init-tools start' to load them. Unloading i2c-dev.....ok. 
```

I then enter 

```
/etc/init.d/module-init-tools start

```

The bash comes back with

```
Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start module-init-tools
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.43" (uid=1000 pid=2049 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

```

I don't know what to do now?

---

### Post by RFXCasey on 2011-05-04
Ok well I did some digging and after entering the command 'sudo modprobe via686a' I see a red 'via686a 11050 0' pop up in the output. Then I do a 'sensors' command and its telling me 'No sensors found!'

All I want to do is see what my CPU temp is so I can turn the darn fan speed down. The sound is driving me crazy.

---

### Post by 4Orbs on 2011-05-04
in the terminal, type the word sensors and hit enter. If that doesn't work, reboot and try again. If that doesn't work then I don't know. When I install sensors, I just use sudo apt-get install lm-sensors and then reboot. After that the sensors command works.

---

### Post by RFXCasey on 2011-05-04
I tried that and still say 'no sensors found! Make sure you loaded all the kernal driver you need' when I run the sensors command. The motherboard is an old Asus A7v133. There is a temperature readout in the BIOS so there is obvious a sensor its reading. I just can't seem to get Xubuntu to recognize the sensor. I have the feeling that the via686a module that the 'detect-sensors' mentioned is either not installed or not working. 

Ah sorry that other post I made was inaccurate, its late and I'm punchy. I ran the lsmod | grep -i via686a and it comes back with via686a 11050 0. Does that mean that the module is installed and working? How can I tell which kernel drivers are installed?

---

### Post by RFXCasey on 2011-05-22
I Still need help on this please. Installed lm-sensors and run but still not able to get a any temp readings. BIOS shows temps and fan speed but can get Xubuntu to tap into the sensors. I believe that there is a module needed for the particular sensor chip but don't know what it is. If anyone can help that would be great but installing lm-sensors alone and running sensors isn't cutting it.

---

### Post by tgalati4 on 2011-05-22
A google search on via686a shows the following:

1	Kernel driver via686a
2	=====================
3	
4	Supported chips:
5	  * Via VT82C686A, VT82C686B  Southbridge Integrated Hardware Monitor
6	    Prefix: 'via686a'
7	    Addresses scanned: ISA in PCI-space encoded address
8	    Datasheet: On request through web form ([http://www.via.com.tw/en/resources/download-center/](http://www.via.com.tw/en/resources/download-center/))
9	
10	Authors:
11	        KyÃ¶sti MÃ¤lkki <kmalkki@cc.hut.fi>,
12	        Mark D. Studebaker <mdsxyz123@yahoo.com>
13	        Bob Dougherty <bobd@stanford.edu>
14	        (Some conversion-factor data were contributed by
15	        Jonathan Teh Soon Yew <j.teh@iname.com>
16	        and Alex van Kaam <darkside@chello.nl>.)
17	
18	Module Parameters
19	-----------------
20	
21	force_addr=0xaddr       Set the I/O base address. Useful for boards that
22	                        don't set the address in the BIOS. Look for a BIOS
23	                        upgrade before resorting to this. Does not do a
24	                        PCI force; the via686a must still be present in lspci.
25	                        Don't use this unless the driver complains that the
26	                        base address is not set.
27	                        Example: 'modprobe via686a force_addr=0x6000'
28	

Looks like you need to find the base address and add that to your /etc/modules file:

sudo modprobe via686a force_addr=0x6000

Of course your computer will use a different address.  The key is to find it!

---

### Post by ericzmeh on 2011-05-22
You should try:

```

/etc/init.d/module-init-tools restart

```

instead.

Then run sensors.  It's always best to answer yes to all when doing the sensors-detect as well.

---

### Post by RFXCasey on 2011-05-23
> **ericzmeh said:**
> You should try:

```

/etc/init.d/module-init-tools restart

```

instead.

Then run sensors.  It's always best to answer yes to all when doing the sensors-detect as well.

When I do that is says module-init-tools stop/waiting then returns me to the command prompt.

then I enter sensors and it says:

No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

---

### Post by RFXCasey on 2011-05-23
How would I go about finding the address???

---

### Post by tgalati4 on 2011-05-24
What is the output of:

cat /etc/modules

It should look like:


tgalati4@minty64 ~/Desktop $ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
sbp2

# Generated by sensors-detect on Sat May 14 17:34:06 2011
# Chip drivers
w83627ehf

Notice the last line.  I have a W83627ehf chip.  You have a via686a chip.

tgalati4@minty64 ~/Desktop $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +49.0°C  (crit = +100.0°C)                  

w83627ehf-isa-0290
Adapter: ISA adapter
VCore:       +1.30 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +12.41 V  (min =  +6.71 V, max = +13.46 V)   
AVCC:        +3.30 V  (min =  +4.08 V, max =  +3.06 V)   ALARM
3VCC:        +3.30 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
in4:         +1.60 V  (min =  +2.04 V, max =  +0.82 V)   ALARM
in5:         +1.88 V  (min =  +2.04 V, max =  +1.98 V)   ALARM
in6:         +5.15 V  (min =  +6.53 V, max =  +6.53 V)   ALARM
VSB:         +3.25 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
VBAT:        +3.22 V  (min =  +3.82 V, max =  +3.06 V)   ALARM
in9:         +1.61 V  (min =  +2.04 V, max =  +2.01 V)   ALARM
Case Fan:      0 RPM  (min =    0 RPM, div = 32)
CPU Fan:    1328 RPM  (min =  664 RPM, div = 8)
Aux Fan:       0 RPM  (min =    0 RPM, div = 32)
fan4:          0 RPM  (min =  767 RPM, div = 32)  ALARM
fan5:          0 RPM  (min =    0 RPM, div = 32)
Sys Temp:    +49.0°C  (high =  -1.0°C, hyst =  -1.0°C)  ALARM  sensor = thermistor
CPU Temp:    +55.0°C  (high = +70.0°C, hyst = +68.0°C)  sensor = diode
AUX Temp:    +50.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V

Read the documentation for your chip (a simple google search will find it, or try the link above).  From the documentation, you will find the common addresses that are used to hold the data.  Then try them.

Put the force_addr in: /etc/modprobe.d/options


tgalati4@minty64 /etc/modprobe.d $ cat options
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

# Stop auto-association.
# LP: #264104
options ipw2200 associate=0

# XXX: Ignore HPA by default. Needs to be revisted in jaunty
options libata ignore_hpa=1

---

