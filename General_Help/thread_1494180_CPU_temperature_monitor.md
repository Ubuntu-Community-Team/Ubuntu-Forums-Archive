---
title: "CPU temperature monitor?"
date: 2010-05-26
forum: General Help
---

### Post by ELD on 2010-05-26
Can someone point me to a good CPU temperature monitor? I'm going to overclock my quad and want to keep an easy on it.

---

### Post by philinux on 2010-05-26
lm_sensors in repo.

---

### Post by ELD on 2010-05-26
> **philinux said:**
> lm_sensors in repo.

"could not find a suitable chip" :(

---

### Post by mhgsys on 2010-05-26
Perhaps you could use screenlets,,(sensors or ringsensors)

---

### Post by uRock on 2010-05-26
I installed computertemp from Synaptic and it found the sensor automatically.

---

### Post by jerenept on 2010-05-26
computemp? I tried to apt-get that, it didn't work.

---

### Post by ELD on 2010-05-26
> **jerenept said:**
> computemp? I tried to apt-get that, it didn't work.

compu**ter**temp

will look at the other suggestion at somepoint

---

### Post by fooman on 2010-05-26
> **ELD said:**
> "could not find a suitable chip" :(

did you run sensors-detect after installing?

open a terminal and run the following:

```
sudo sensors-detect
```

follow the prompts.  when its complete,  simply run:

```
sensors
```

---

### Post by bo6o on 2010-08-19
Hi, I'm having problems with computertemp - I can't get it running. Done sensors detect and stuff, but applet refuses to show anything - it stays redcrossed. When I write sensors in terminal I get the temp reading. Other apps also show it correctly, but I want it on the pannel. Any suggestions pls... I'm with Ubuntu 10.04 lts on Lenovo 3000 N200.

---

### Post by WorMzy on 2010-08-19
Use the [GNOME Sensors Applet]("apt://sensors-applet"). Install it by clicking on the link, or by running
```
sudo apt-get install sensors-applet
```

You can then add it to your panel by right-clicking on empty space on one of your panels, and choosing "Add to panel", from there, look (or search) for "Hardware Sensors Monitor", and drag it where you want it.

---

### Post by bo6o on 2010-08-19
Thanks, it works perfect ;)

---

### Post by SirPecanGum on 2010-09-17
Thanks!

---

### Post by Kixtosh on 2010-09-19
> **WorMzy said:**
> Use the [GNOME Sensors Applet]("apt://sensors-applet"). Install it by clicking on the link, or by running
```
sudo apt-get install sensors-applet
```

You can then add it to your panel by right-clicking on empty space on one of your panels, and choosing "Add to panel", from there, look (or search) for "Hardware Sensors Monitor", and drag it where you want it.This worked great for me. I added it to the panel with a right mouse click on the panel and choosing  "_A_dd to Panel ..." from the drop down menu, then choosing from the pop-up window "Computer Temperature Monitor".

I was asked a question during the whole installation in Terminal though, and I wasn't quite sure what to answer ... something about whether I wanted whatever to activate on start-up. The default answer was "no", but I chose "yes". Not sure what all that was about. I should have saved the contents of the Terminal to give more details. If anyone else follows this procedure, perhaps they could paste the result in this thread.

---

### Post by 3Miro on 2010-09-19
It asked you if you wish to activate the service that lets you monitor hard disk temperature as well. If you want to keep an eye on that, yes is the correct answer.

---

### Post by Kixtosh on 2010-09-19
> ... If anyone else follows this procedure, perhaps they could paste the result in this thread.I tried to attempt this on another laptop, using a Live CD, so that I could help "fix" my own omission, but it didn't work: I got stuck with this message:```
ubuntu@ubuntu:~$ sudo apt-get install sensors-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sensors-applet
ubuntu@ubuntu:~$ 

```I got around this by opening the Ubuntu Software Center from the Panel "Applications" Menu, and then adding the System Profiler and Benchmark application (which I already was using on the first laptop, before I got the applet thanks to this thread). That fixed it, so I've saved a copy of the Terminal output. Since it's a bit long, here's a screenshot of the message that pops up during the installation from Terminal, and another message that pops up if you answer "Yes":

---

### Post by Kixtosh on 2010-09-19
> **3Miro said:**
> It asked you if you wish to activate the service that lets you monitor hard disk temperature as well. If you want to keep an eye on that, yes is the correct answer.Ah! Thanks for the clarification! Somehow "Yes" seemed to make more sense to me, even if it wasn't the default answer, but it didn't stop me from feeling stupid afterwards!

When you answer "Yes", there's also a pop-up window, along with the two I attached to my message above, about the delay in seconds between checks, with a default value of "0", which means that the temperature will not be logged, I think.

---

### Post by Ray_GTI-R on 2011-03-05
Ubuntu 10.10, Asus P8P67PRO & Intel i7-2600K ... no sensors detected.

FWIW I know what I'm doing, I think ;-)

Ran sudo sensors-detect that's how I know no sensors detected and yes, I did try the "sensors" command AND the restart thing.
No Joy

Listening ... :-)))

---

### Post by Ray_GTI-R on 2011-03-06
Anyone interested still in lm-sensors? 8-[

---

### Post by Yellow Pasque on 2011-03-06
IIRC, the p8p67pro uses a fairly new sensor chip. Post the output of sensors-detect.

---

### Post by Ray_GTI-R on 2011-03-07
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: System manufacturer System Product Name
# Board: ASUSTeK Computer INC. P8P67 PRO

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found unknown chip with ID 0xc333
    (logical device B has address 0x290, could be sensors)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): y
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Found unknown SMBus adapter 8086:1c22 at 0000:00:1f.3.
Sorry, no supported PCI bus adapters found.
Module i2c-dev loaded successfully.

Sorry, no sensors were detected.

Like I said ... no sensors detected ](*,)

Hope this helps .

Listening very, very hard ((:))) and with both ears now :P

(IIRC Asus P8P67PRO & Intel i7-2600K have been around for some months ?)

---

### Post by Yellow Pasque on 2011-03-08
> **Ray_GTI-R said:**
> 
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found unknown chip with ID 0xc333
    (logical device B has address 0x290, could be sensors)


There's your sensor chip. It's a Nuvoton NCT6776F. The driver is still in testing stage and not in the kernel, but you can build your own kernel module: [http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/)
> (IIRC Asus P8P67PRO & Intel i7-2600K have been around for some months ?)
The versions of lm-sensors and the kernel found in Ubuntu 10.10 have been around longer ;) I'm guessing that a Natty/11.04 LiveCD would at least see the i7's internal sensor.
Also, development of a driver for a new sensor chip can take a while. People have to start demanding it on the lm-sensors mailing list, and then sample hardware has to find its way into the hands of a capable dev.
[http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices)

---

### Post by Ray_GTI-R on 2011-03-10
Thanks for the response.
Yes, I previously saw [http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices) and discounted it since it doesn't list e.g., Asrock at all and still shows long-defunct mfg's like ABIT etc.

[url]http://www.phoronix.com/scan.php?page=article&item=intel_snb_video&num=1 says a lot - interesting too, especially "... Sandy Bridge ... code has been available since day-one."
AFAIK that's "... announced on January 3, 2011 ... available from January 9, 2011" ... or two clear months ago.:confused:

> People have to start demanding it on the lm-sensors mailing list, and then sample hardware has to find its way into the hands of a capable dev.

Seems a bit ummm ... 70's. So maybe I should switch to Windows XP & Sandra (reviews have been around since 2 Jan - Google Michael Schuette, Sisoftware 2011c etc) ):P

Ray
FWIW this is a lighthearted reply.

---

### Post by Trettel on 2011-04-12
I'm having the same problem as Ray_GTI-R (Asus P8P67-Deluxe & Intel i7-2600K)... cannot get the cpu/mobo temp sensors to work.  Does anyone know if lm-sensors is being updated or if there's another way to get these sensor inputs?

---

### Post by Yellow Pasque on 2011-04-12
The Asus P8P67-Deluxe sensor chip is a Nuvoton NCT6776F. The driver has not entered the kernel tree yet, but it is available as a standalone kernel module you can build on your own: [http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/)

---

### Post by Trettel on 2011-04-12
Excellent!  Thanks for the quick reply!

---

### Post by Frank DeMarco on 2011-08-16
Thanks for this info!  Helped me spot an overheating GPU BEFORE it burned out.
Fan was clogged with dust.  :-(

---

### Post by pqwoerituytrueiwoq on 2011-08-16
> **Ray_GTI-R said:**
> Anyone interested still in lm-sensors? 8-[
that is a dependency of sensors-applet

---

### Post by 08x on 2011-08-24
You need to check out this The OMG! Ubuntu! Guide to the best indicator applets around [http://ki.tl/Hmab](http://ki.tl/Hmab) awesome

---

### Post by Neo40 on 2011-09-21
I have computertemp installed but there is a big red cross on the icon.
Do I need to configure it? If I use xsensors it works.
Any idea?
THanks

---

