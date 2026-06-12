---
title: "Struggling with lm-sensors"
date: 2009-12-11
forum: General Help
---

### Post by gabe17 on 2009-12-11
Hi! I have beed struggling with lm-sensors for a long time, and I’ve had many problems and questions during the installation (or configuration). Thats the reason of starting this thread. I will try to install it again following [COLOR=#0000ff]_[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)_[/COLOR] tutorial, and I will ask here my n00b questions. I hope somebody will help me. Thanks.
 Well, I’ve done steps 1 and 2 without any problems. I’ve almost done step 3, but I want to ask about the last part of step 3: 



 > To make the sensors modules behave correctly, add these lines to
/etc/modprobe.d/local and run update-modules:
#----cut here----
# I2C module options
alias char-major-89 i2c-dev
#----cut here---- 
 Should I add exactly these lines, or does it depend on the previous output?


```
$ sudo apt-get install lm-sensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 conky-all liblua5.1-0 libimlib2 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  sensord read-edid i2c-tools
The following NEW packages will be installed:
  lm-sensors
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/125kB of archives.
After this operation, 569kB of additional disk space will be used.
Selecting previously deselected package lm-sensors.
(Reading database ... 176956 files and directories currently installed.)
Unpacking lm-sensors (from .../lm-sensors_1%3a3.0.2-2ubuntu4_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up lm-sensors (1:3.0.2-2ubuntu4) ...

~$ cd lm-sensors
~/lm-sensors$ chmod 755 mkdev.sh
~/lm-sensors$ sudo ./mkdev.sh
/dev/i2c-0
/dev/i2c-1
/dev/i2c-2
/dev/i2c-3
/dev/i2c-4
/dev/i2c-5
/dev/i2c-6
/dev/i2c-7
/dev/i2c-8
/dev/i2c-9
/dev/i2c-10
/dev/i2c-11
/dev/i2c-12
/dev/i2c-13
/dev/i2c-14
/dev/i2c-15
/dev/i2c-16
/dev/i2c-17
/dev/i2c-18
/dev/i2c-19
/dev/i2c-20
/dev/i2c-21
/dev/i2c-22
/dev/i2c-23
/dev/i2c-24
/dev/i2c-25
/dev/i2c-26
/dev/i2c-27
/dev/i2c-28
/dev/i2c-29
/dev/i2c-30
/dev/i2c-31
~/lm-sensors$ sensors-detect
You need to be root to run this script.
~/lm-sensors$ sudo sensors-detect
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801H ICH8

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): y
Module loaded successfully.
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
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Winbond W83627DHG Super IO Sensors'                  Success!
    (address 0x290, driver `w83627ehf')
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

Driver `w83627ehf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `Winbond W83627DHG Super IO Sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
w83627ehf
#----cut here----

Do you want to add these lines automatically? (yes/NO)y
~/lm-sensors$ cd
~$ /etc/init.d/module-init-tools
Usage: /etc/init.d/module-init-tools COMMAND

```

---

### Post by mal on 2009-12-11
gabe17,

From the information you provided, it appears that you chose to add the required lines to /etc/modules automatically, so you should not need to make any more changes.  To check you could run:

```
$ cat /etc/modules
```

and make sure that the line has been added.

The instructions about adding lines to /etc/modprobe.d/local were only for the example in the howto, so I don't think they apply to you.

I suggest you proceed with the rest of the instructions and it should work.

Mal

---

### Post by gabe17 on 2009-12-11
mal, thanks for your reply, so as I comprehended, I can skip steps 4 and 5 (if not please let me know). 

Step 6 - another problem...see the code below
```

~$ sudo modprobe w83627ehf 
FATAL: Error inserting w83627ehf (/lib/modules/2.6.31-16-generic/kernel/drivers/hwmon/w83627ehf.ko): Device or resource busy 

```

---

### Post by mal on 2009-12-11
gabe17,

Yes, I think you probably can skip 4 and 5.  You might be getting the error message because the module (w83627ehf) is already loaded.  In which case you should be able to run the command:```
$ sensors
``` and get a read out of your processor sensors.

If this doesn't work you can check that the module has loaded by running this command:
 
```
lsmod | grep w83627ehf
```

You should see at least one line with this module name listed.

Mal

---

### Post by gabe17 on 2009-12-11
```

~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
~$ 

```

```

~$ lsmod | grep w83627ehf
~$  

```

without any success :(

---

### Post by mal on 2009-12-12
gabe17,

Try: ```
$ cat /etc/modules
``` to make sure that the module is included.  I assume that it is not or it would have been loaded during the last boot of your computer (have you rebooted?).

If the required module is not listed, you can add it using: ```
$ sudo echo "w83627ehf" >> /etc/modules
```

Then reboot and try sensors again.

Mal

---

### Post by gabe17 on 2009-12-12
```

$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

# Generated by sensors-detect on Fri Dec 11 10:02:46 2009
# Chip drivers
w83627ehf
w83627ehf
$ 

```

So the module is included, but still, no sensors found. (yes, I have rebooted)
```

$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
$ 

```

---

### Post by mal on 2009-12-12
OK - I'm a bit stumped now.

You could remove one of the w83627ehf lines from /etc/modules, but this is unlikely to be causing any problems.

I would also try adding a line with i2c-i801 before the w83627ehf line to see if that makes any difference, although this is probably just clutching at straws.  It should not cause any problems if it is not needed.  (Make sure you reboot after changing /etc/modules.)

Otherwise, I'm running out of ideas...

Mal

---

### Post by mal on 2009-12-12
It might be a good idea to have a look at [this post]("http://ubuntuforums.org/showthread.php?p=7210837&highlight=w83627ehf#post7210837").

Mal

---

### Post by gabe17 on 2009-12-12
Great! It works! I've read all links you've posted and I've added ```
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"
```into ```
/etc/default/grub
```, run ```
sudo update-grub
```, rebooted and I've got the conclusion I wished. (you know how happy I am now after few weeks of struggling with it). Thanks a lot!!!:D

---

### Post by mal on 2009-12-12
gabe17,

I'm glad to hear that you got it working.  Sometimes it can be a bit frustrating when things don't work as expected, but it is a great learning experience and very satisfying when a solution is found.

Regards,

Mal

---

### Post by Ramsos on 2011-08-08
Thank you so much for this thread ! It was exactly what I need to make lm-sensors work on my P4SC8 supermicro server !

---

### Post by MeduZa on 2012-12-24
> **gabe17 said:**
> Great! It works! I've read all links you've posted and I've added ```
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"
```into ```
/etc/default/grub
```, run ```
sudo update-grub
```, rebooted and I've got the conclusion I wished. (you know how happy I am now after few weeks of struggling with it). Thanks a lot!!!:D

motherboard: supermicro p4cs8 thermal chip: w83627hf
adding the line also work for me :guitar:
thanks!

---

