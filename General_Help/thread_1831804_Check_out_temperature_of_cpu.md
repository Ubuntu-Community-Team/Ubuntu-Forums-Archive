---
title: "Check out temperature of cpu"
date: 2011-08-23
forum: General Help
---

### Post by linux_dream on 2011-08-23
So I would like to check out my cpu temperature in function of time.
I've followed [http://elblogdeling.wordpress.com/2009/02/10/monitoriza-la-temperatura-de-tu-cpu-y-gpu-en-ubuntu/](http://elblogdeling.wordpress.com/2009/02/10/monitoriza-la-temperatura-de-tu-cpu-y-gpu-en-ubuntu/) but unfortunately in the description it was for the old version of Ubuntu and despite having downloaded the program, I simply can't add it in the taskbar.

I did in a terminal: sudo apt-get install sensors-applet.  Then I installed a few remaining packets from synaptic.  Now how do I run the program?

Thanking you in advance.

---

### Post by dave01945 on 2011-08-23
i could only get sensors-applet to work in gnome not in unity for unity i use indicator-sysmonitor you can get it here

[http://www.omgubuntu.co.uk/2011/03/indicator-sysmonitor-simple-system-stats-app-for-ubuntu/](http://www.omgubuntu.co.uk/2011/03/indicator-sysmonitor-simple-system-stats-app-for-ubuntu/)

then you just add indicator-sysmonitor to startup applications i also had to install lm-sensors to get the cpu temp to show after installing lm-sensors you will need to run

```
sensors-detect
```

that should load all you need

---

### Post by linux_dream on 2011-08-23
Thanks a lot.  I downloaded the indicator from the website you provided.  I also ran sensors-detect but nothing poped up.

Here's my terminal:
```
# sensors-detect revision 5861 (2010-09-21 17:21:05 +0200)
# Board: Intel Corporation DG965SS

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found `Nat. Semi. PC8374L Super IO Sensors'                 
    (but not activated)
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
Do you want to probe the I2C/SMBus adapters now? (YES/no): n
Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading cpuid... OK

isaac@isaac-desktop:~$ service module-init-tools start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.80" (uid=1000 pid=5010 comm="start module-init-tools ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
```
I don't know what to do next.

---

### Post by jfed on 2011-08-24
For me, all I have to do is type:

```
sensors
```

Into a terminal. I don't even remember if I installed the program or not to be honest, I think it may have came out of the box. Then again I am using Maverick, haven't tried that NEW WAVE HIPPY NATTY NARWHAL yet, haha.

Alternatively, if you right click a panel and select "add to panel" there may be an option to display a little applet that lets you see your cpu temp from your desktop, thats what I used to have on my laptop.

---

### Post by dave01945 on 2011-08-24
if you have added indicator-sysmonitor to your start up applications you will have to log out and in again to get it to load alternatively you can press <alt>-F2 and run it from there by typing indicator-sysmonitor then that should open it in the top bar then to add your specific sensors you need to right click on the sensors click preferences then there will be a list of available sensors highlight the ones you want and at the bottom click add selected sensors

---

### Post by linux_dream on 2011-08-24
Thank you very much guys!  Working.
Core 1:63°C. 
Core 2:65°C.
Graphic card: 59°C.

---

### Post by raja.genupula on 2011-08-24
> **dave01945 said:**
> i could only get sensors-applet to work in gnome not in unity for unity i use indicator-sysmonitor you can get it here

[http://www.omgubuntu.co.uk/2011/03/indicator-sysmonitor-simple-system-stats-app-for-ubuntu/](http://www.omgubuntu.co.uk/2011/03/indicator-sysmonitor-simple-system-stats-app-for-ubuntu/)

then you just add indicator-sysmonitor to startup applications i also had to install lm-sensors to get the cpu temp to show after installing lm-sensors you will need to run

```
sensors-detect
```

that should load all you need


thanks for this , now i am also getting temp indications ,.

---

