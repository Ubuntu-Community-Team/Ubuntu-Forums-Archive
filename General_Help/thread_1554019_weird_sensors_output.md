---
title: "weird sensors output?"
date: 2010-08-16
forum: General Help
---

### Post by princeofnam on 2010-08-16
i'm trying to install sensors, and i did everything correctly 
sudo aptitude install lm-sensors
sudo sensors-detect (answering yes to everything)

(i think), but when I type sensors in the terminal this is what I get
--
sushi@Ragnarork:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +60.0°C  (crit = +105.0°C)  
--

60 is definitely not the temp, and it never actually changes

---

### Post by princeofnam on 2010-08-16
so this is actually my sensors-detect output
--

Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): YES
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801FB ICH6
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x4c
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Analog Devices ADT7466'...                     No
Probing for `Andigilog aSC7511'...                          No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `National Semiconductor LM90'...                No
Probing for `National Semiconductor LM89/LM99'...           No
Probing for `National Semiconductor LM86'...                No
Probing for `Analog Devices ADM1032'...                     No
Probing for `Maxim MAX6654/MAX6690'...                      No
Probing for `Maxim MAX6657/MAX6658/MAX6659'...              No
Probing for `Maxim MAX6648/MAX6649/MAX6692'...              Success!
    (confidence 8, driver `lm90')
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Winbond W83L771W/G'...                         No
Probing for `Winbond W83L771AWG/ASG'...                     No
Probing for `Texas Instruments TMP401'...                   No
Probing for `Texas Instruments TMP411'...                   No
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP422'...                   No
Probing for `Texas Instruments TMP423'...                   No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `National Semiconductor LM63'...                No
Probing for `Fintek F75363SG'...                            No
Probing for `National Semiconductor LM73'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Analog Devices ADT7461'...                     No
Probing for `Analog Devices ADT7481'...                     No
Probing for `Fintek F75383S/M'...                           No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `lm90':
  * Bus `NVIDIA i2c adapter '
    Busdriver `nvidia', I2C address 0x4c
    Chip `Maxim MAX6648/MAX6649/MAX6692' (confidence: 8)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
lm90
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)YES   
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK

--

i notice it asks to run that bit of code at the end but i get this 

--
sushi@Ragnarork:~$ /etc/init.d/module-init-tools start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service module-init-tools start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start module-init-tools
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.54" (uid=1000 pid=5392 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
--

so i tried typing in

--
sushi@Ragnarork:~$ service module-init-tools start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.55" (uid=1000 pid=7379 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
sushi@Ragnarork:~$ 

--
no luck...

---

### Post by princeofnam on 2010-08-17
any luck?

---

### Post by princeofnam on 2010-08-20
nobody else has had similar sensors issues before?

---

