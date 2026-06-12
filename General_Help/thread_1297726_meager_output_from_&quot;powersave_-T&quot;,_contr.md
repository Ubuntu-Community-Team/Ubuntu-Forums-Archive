---
title: "meager output from &quot;powersave -T&quot;, control fan speed?"
date: 2009-10-22
forum: General Help
---

### Post by aaronre on 2009-10-22
Hi all,

I'm trying to control the fan on my old dell inspiron 8200 laptop.

I found a few tutorials on installing lm-sensors and then using some programs to control fan speed, but when i execute
```
powersave -T
```i get

```

Thermal Device no. 0:
Temperature: 51
Critical: 94
```the powersave manual says:
> Use the powersave -T command to find supported thermal zones and their default trip point settings.So does this mean that I don't have any trip points?

This script was supposed to tell me what modules to add:
```

#!/bin/bash
     
     # Here you can set several defaults.
     
     # The number of devices to create (max: 256)
     NUMBER=32
     
     # The owner and group of the devices
     OUSER=root
     OGROUP=root
     # The mode of the devices
     MODE=600
     
     # This script doesn't need to be run if devfs is used
     if [ -r /proc/mounts ] ; then
         if grep -q "/dev devfs" /proc/mounts ; then
             echo "You do not need to run this script as your system uses devfs."
             exit;
         fi
     fi
     
     i=0;
     
     while [ $i -lt $NUMBER ] ; do
         echo /dev/i2c-$i
         mknod -m $MODE /dev/i2c-$i c 89 $i || exit
         chown "$OUSER:$OGROUP" /dev/i2c-$i || exit
         i=$[$i + 1]
     done
     #end of file
```
but when i run sensor-detect, the relevant part of the output that i get is:
```

#----cut here----
# Chip drivers   
# no driver for SMSC LPC47N252 Super IO Fan Sensors yet
#----cut here----
```
Which is supposed to get added to /etc/modules, but as you can see, this won't have any effect.

All of the tutorials and documentation assume hearty output when running their scripts, so i'm not sure what it means when i get really weak output like i have.  Also, the "no driver" thing (in the previous code box) gave me some doubts, too.

All of the tutorials seemed to be derivatives of one another, the one i was following is this one:
[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

Am I out of luck, or can this be worked around?

Thank you

---

### Post by P4man on 2009-10-22
that tutorial is from 2004.. 
May or may not still work,
but if you installed lm-sensors, run

```
sudo sensors-detect
```

reply YES to each question. Paste the output here.
I seem to recall you got cpu temps in ubuntu earlier on, so there must be a sensor that works.

---

### Post by aaronre on 2009-10-24
Running sensors-detect plays out as follows:
```
aaron@adelle:~$ sudo sensors-detect
[sudo] password for aaron:         
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe  
and recommended to accept the default answers to all questions,   
unless you know what you're doing.                                

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y                     
Probing for PCI bus adapters...                           
Sorry, no supported PCI bus adapters found.               

If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): y     
Module loaded successfully.                        

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence    
value in that case.                                                  
If you found that the adapter hung after probing a certain address,  
you can specify that address to remain unprobed.                     

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!   
Do you want to scan the ISA I/O ports? (YES/no): y                      
Probing for `National Semiconductor LM78' at 0x290...       No          
Probing for `National Semiconductor LM78-J' at 0x290...     No          
Probing for `National Semiconductor LM79' at 0x290...       No          
Probing for `Winbond W83781D' at 0x290...                   No          
Probing for `Winbond W83782D' at 0x290...                   No          
Probing for `IPMI BMC KCS' at 0xca0...                      No          
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found `SMSC LPC47N252 Super IO Fan Sensors'                 Success!
    (address 0x910, driver `to-be-written')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue:

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x910
    Chip `SMSC LPC47N252 Super IO Fan Sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue:

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
# no driver for SMSC LPC47N252 Super IO Fan Sensors yet
#----cut here----

Do you want to add these lines automatically? (yes/NO)y

```as you can see, the lines that it wants to add to /etc/modules are useless.  It seems like i do have a temperature sensor somewhere in there, and it appears to give accurate readings, which i can see with 
```
acpi -t
```, but sensors-detect doesn't work out so well.  Not really sure what's up

thank you

---

