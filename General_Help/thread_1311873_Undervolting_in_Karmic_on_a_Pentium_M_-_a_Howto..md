---
title: "Undervolting in Karmic on a Pentium M - a Howto."
date: 2009-11-02
forum: General Help
---

### Post by ebsbel on 2009-11-02
It was so difficult for me to get this working, so I thought I might as well write a Howto. It should work in 9.04 as well, but you would have to do the modifications yourself.

Before you start, remember that undervolting is risky and it is likely that it will crash your computer. However, when you get it working it is a very comfortable feeling to have a quite computer.

To undervolt you need to either compile a new kernel or get one that is compiled for undervolting your pc. I got mine from here:
[https://launchpad.net/~linux-phc/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~linux-phc/+archive/ppa?field.series_filter=karmic)
After adding these lines to the repository:
```
deb http://ppa.launchpad.net/linux-phc/ppa/ubuntu karmic main 
deb-src http://ppa.launchpad.net/linux-phc/ppa/ubuntu karmic main 

```
I could install the kernel by:
```
sudo apt-get install linux-image-2.6.31-14-generic-phc
```
After booting into the new kernel it should be possible to get the undervolting working by just doing:
```
sudo modprobe acpi-cpufreq
```
If you get a lot of files starting with phc in /sys/devices/system/cpu/cpu0/cpufreq/ then you should be on your way.
I did not get these files, so I had to use a different method.
I tried:
```
sudo modprobe speedstep-centrino
```
but that did not work.
I had to download phc-intel from
[http://www.linux-phc.org/forum/viewtopic.php?f=13&t=2](http://www.linux-phc.org/forum/viewtopic.php?f=13&t=2)
This had to be compiled, so I needed the kernel-headers:
```
sudo apt-get install linux-headers-generic-phc
```
Then I followed the instructions in the phc-linux README and compiled it successfully. I unloaded the acpi-cpufreq module and loaded the new module:
```
sudo modprobe -r acpi-cpufreq
sudo modprobe phc-intel
```
This worked and it populated my /sys/devices/system/cpu/cpu0/cpufreq/ with a lot of files starting with phc. Especially important are the files phc_vids and phc_controls. They contain the information about the voltages that the cpu will use for each scaling frequency.
I already knew which voltages work on my system since I have used RM-Clock in windows and tested it thoroughly.
To get everything loaded with the correct frequencies on boot up I edited /etc/rc.local by adding the lines:
```
echo "17:17 14:12 12:9 10:6 8:0 6:0" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
I also wanted the computer to work 'Ondemand'. It may be better to use the built in function for this. You can add a cpu-applet to your desktop panel and you can control the scaling with that.
To explain what these numbers mean:
17:17 means that at frequency 1700MHz it uses the voltage 17*16+700=972mV.
14:12 means that at frequency 1400MHz it uses the voltage 12*16+700=892mV.
The numbers mean something else for other cpu:s, so check what is valid for yours. 
Also remember that if you set your voltages too low and maybe if you copy my numbers your computer will probably CRASH! Be cautious!
To get phc-intel to load on startup  I added a line:
```
phc-intel
``` to /etc/modules.
That was it. I restarted and my laptop runs cool and quite. Very satisfying. I have also tried the 'Conservative' cpu-scaling which is a bit smoother than 'Ondemand'.
Good luck!
E

---

### Post by raido357 on 2009-11-24
When 2.6.31-15-phc version will be released ?

---

### Post by zcats on 2009-11-26
Hey.  I DID not need to do all this! 
Undervolting was as simple as adding the ppa for PHC :p:D and installing the kernel 2.6.31-14-generic-phc using synaptic.
BTW I have a Pentium M processor 1.70GHz
Of course I still needed to determine and set my optimal values and edit your /etc/rc.local file to make permanent 
>sudo gedit /etc/rc.local 
so it looks like:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo "17:19 14:12 12:18 10:4 8:1 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
exit 0

---

### Post by zcats on 2009-12-01
Mmmmm.  Sorry.  I DO need to do this now! My previous report was with a fresh install of Xubuntu karmic while keeping old jaunty home partition that had an old .ko file.  However on  a fresh install of Ubuntu karmic without keeping old home partition this does not work (even though I copied the old .ko module to my new home directory). ?! (BTW I did a fresh install because googleearth crashed my machine and trashed the mbr or boot files and e2fsck repair did not fix this. I reinstalled grub on this partition without formating  using live cd but it wiped the whole partition, WTF!:o)

So........I followed the above tutorial exactly and it worked out perfectly!
Thanks ;):p

---

### Post by seish on 2009-12-03
:KS     :KS     :KS     :KS     :KS     :KS     :KS      
OMG thank you so much.

I had given up on the whole thing because looking for documentation on anything in linux in general has been almost impossible :)
the regular thread was too outdated.

Followed ur exact steps and it works like a charm. I'm down 10 degrees

I downloaded the phc-intel-0.3.2-8 since I guess that's the newest dowloadable version.

Btw I removed the acpi_cpufreq module from /etc/modules before adding phc-intel, that's correct, right?

Here's the values for my processor if it helps anyone
Intel® Core&#8482;2 Duo Mobile Processor T5750
VID VOltage range:  1.075V-1.175V
12:10 10:0 8:0 6:0

---

### Post by mister_playboy on 2009-12-12
> **seish said:**
> Here's the values for my processor if it helps anyone
Intel® Core™2 Duo Mobile Processor T5750
VID VOltage range:  1.075V-1.175V
12:10 10:0 8:0 6:0

The crash script doesn't work right on Core 2 Duo processors.  This is because the lowest allowable value for these processors is 19... when the script is testing any number lower than 19, in fact, absolutely nothing is happening... the test runs to negative (impossible) values without crashing.

19 across the board should be just fine.  I'm not sure if a lower number either does nothing or is treated as though it were 19.

---

### Post by zcats on 2009-12-23
Lower numbers can cause machine to hang/crash (no danger of cpu damage, only curruption/data loss)

Method described confirmed Works with 2.6.31-14-generic-phc and 2.6.31-16-generic-phc on laptop with 1.7GHz intel cpu (thinkpad T42)

Silence and cool is cool......

---

### Post by Ixtao on 2010-01-01
First try with the 2.6.31-14 kernel didn't work on the Pentium M 1.2 I'm working with. After the update to 31-16 and compiling the newer phc-intel-0.3.2-9 offtree I'm in!! :KS

Got one weird crash where my screen would blurr all grey. not sure if this was a problem because of undervolting. my values are: 12:8 11:7 10:6 9:5 8:4 6:2

---

### Post by ebsbel on 2010-01-11
> **mister_playboy said:**
> The crash script doesn't work right on Core 2 Duo processors.  This is because the lowest allowable value for these processors is 19... when the script is testing any number lower than 19, in fact, absolutely nothing is happening... the test runs to negative (impossible) values without crashing.

19 across the board should be just fine.  I'm not sure if a lower number either does nothing or is treated as though it were 19.


I just updated my kernel, so I had to visit my own thread again to know what to do;).I had to re-compile the phc-intel. They had a new version. 

This howto is only for Pentium M. I got my values for undervolting by testing to lower the voltage until the system got unstable. You have to find these numbers out by yourself. It may be very different for your cpu. If you just copy my values your computer may crash.

I am glad that many of you have had success with my method.

E

---

### Post by beezwings on 2010-03-11
Hi~

Can someone help? I used to have my laptop undervolted. Since my upgrade to a few days ago to Karmic koala, I get through to all the undervolting steps, but for some reason, when I reboot, the system doesn't seem to be reading the rc.local file, since my values are still the same. When I try either sudo echo "11:22 8:1 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls, I get a "permission denied" message. I'm a newbie, so please walk me through, thanks!

---

### Post by zcats on 2010-05-04
Try these two commands one after the other:
sudo -s
echo "11:22 8:1 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls

---

### Post by simoniemesko on 2010-09-22
i have the same problem, i cant change phc_xxxyyy files or any files in /sys/devices/system/cpu/cpu0/cpufreq folder. I also cant load my voltages on starttup. There are defaults, ihave to run hctool as sudo and than it is all OK...

---

