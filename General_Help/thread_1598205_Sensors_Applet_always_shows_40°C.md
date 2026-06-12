---
title: "Sensors Applet always shows 40°C"
date: 2010-10-16
forum: General Help
---

### Post by 2CV67 on 2010-10-16
I installed lm_sensors via Synapt & the Sensors Applet on the panel, but that applet shows me an invariable 40°C for 2 temperatures - 'CPU' & 'temp1'.

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/sensorsApplet.png[/IMG]

Now I know it can't read the CPU temperature (long story, the CPU fan is hard-wired to 6v & there is no temperature feedback...) but it should be able to find a couple of other useful temperatures.

The same PC in XP uses Speedfan which indicates plausible temperatures for (I think) Case & Hard Drive. (Temp2 & HD0 in the attached)

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/speedfan2.gif[/IMG]

I wonder what I have failed to do & why I cannot see Case or HD temps in Ubuntu?

In terminal, I ran sensors-detect which went OK until the last bit where it said:
"~$ /etc/init.d/module-init-tools start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service module-init-tools start...etc"

I don't follow that, but I have checked that I have it87 in both /etc/modules & in lib/modules/.../hwmon

Now I am stuck!

Any suggestions?

Thanks!

---

### Post by Little Blue on 2010-10-16
Have you run sensors-detect to see what sensors are installed and that it can run?

EDIT: nevermind. I'm blind and you said you did...

---

### Post by 2CV67 on 2010-10-16
> **Little Blue said:**
> Have you run sensors-detect to see what sensors are installed and that it can run?

EDIT: nevermind. I'm blind and you said you did...

Yes - here are the results, if that helps:
```
chris@DESKTOP:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +75.0°C)                  

chris@DESKTOP:~$ sudo sensors-detect
[sudo] password for chris: 
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: VIA Technologies, Inc. Aspire T120

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
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found `ITE IT8705F Super IO Sensors'                        Success!
    (address 0x290, driver `it87')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found `ITE IT8705F Super IO Sensors'                        Success!
    (address 0x290, driver `it87')

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
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): y
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

Driver `it87':
  * ISA bus, address 0x290
    Chip `ITE IT8705F Super IO Sensors' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
it87
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)y 
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/module-init-tools start'
to load them.

chris@DESKTOP:~$ /etc/init.d/module-init-tools start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service module-init-tools start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start module-init-tools
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.90" (uid=1000 pid=3127 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
chris@DESKTOP:~$ 

```

---

### Post by jenigmat429 on 2010-10-24
I'm getting the same error message when I do a sensors-detect. sensors always tells me that I have a temperature in a range between 87 and 89, and it's definitely not that hot, so I'm thinking it must be a related problem.

---

### Post by 2CV67 on 2010-11-01
Can anybody tell me what the last part of the "sensors-detect" procedure means, please?

```
Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/module-init-tools start'
to load them.

chris@DESKTOP:~$ /etc/init.d/module-init-tools start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service module-init-tools start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start module-init-tools
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.90" (uid=1000 pid=3127 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
chris@DESKTOP:~$
```

Does this explain (not to me!) why I still don't see any meaningful temperatures?

---

