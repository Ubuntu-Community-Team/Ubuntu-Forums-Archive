---
title: "Can't monitor cpu temperature"
date: 2010-01-02
forum: General Help
---

### Post by head2head on 2010-01-02
I've recently installed Karmic on my new machine with the following specs;

Asus M4A785TD-V EVO Motherboard 
AMD Athlon II X4 620 2.6GHz 
Crucial 4GB (2x2GB) DDR3 
Coolermaster Elite 330 Case 
Western Digital WD5000AAKS 500GB

I'm looking to install some sort of temperature monitoring for my cpu and have had luck using either lm-sensors or acpi.

With lm sensors, I've followed the various how to's on the forum and am still coming back with nothing. Trying to add hardware monitoring to panel brings up a 'no sensors found!' error, and x-sensors just starts up with a blank screen.

'sensors' in terminal spits back this - 

```

lou@lou-quad:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
lou@lou-quad:~$ 

```

I've added the relevant lines into etc/modules as per the last question during configuration but still no joy.

I've just run 'sensors-detect and had a gander at the output, and I'm wondering if its as simple as no one has written a driver for my mobo yet....

```

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `it87' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `ITE IT8712F Super IO Sensors' (confidence: 9)

Driver **`to-be-written'** (should be inserted):
  Detects correctly:
  * Chip `AMD K10 thermal sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
it87
# **no driver for AMD K10 thermal sensors yet**
#----cut here----

Do you want to add these lines automatically? (yes/NO)y

```

The bold bits would indicate I've got an unsupported board :(.

Any thoughts? Is it just a case of waiting for drivers?

---

### Post by spiky001 on 2010-01-02
dont know if this helps if you start byobu in terminal u can make a selection for temp on the bottom of terminal screen maybe not you want

---

### Post by pulpo69 on 2010-01-02
file a bug.
how to install this driver for k10 thermal sensors?

[http://khali.linux-fr.org/devel/misc/k10temp/](http://khali.linux-fr.org/devel/misc/k10temp/)

found on this page [http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices)

---

