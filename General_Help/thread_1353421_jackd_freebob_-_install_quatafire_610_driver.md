---
title: "jackd freebob - install quatafire 610 driver"
date: 2009-12-12
forum: General Help
---

### Post by ThirdKind on 2009-12-12
Hello,

I have been trying to install a quatafire 610 on ubuntu OS with using jackd and freebob....The 610 is Bebob firmware. I get this error when Iplace in this code;
desktop:/$ jackd -d freebob -d hw:2

no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 2, node -1
Ieee1394Service::initialize: Could not get 1394 handle: Invalid argument
Is ieee1394 and raw1394 driver loaded?
Fatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
Fatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
FreeBoB ERR: FREEBOB: Error creating virtual device
cannot load driver module freebob

I know I need to create a permission file and rules file but I am having difficulties

Any help would be greatly appreciated. Thanks in advance

---

### Post by ThirdKind on 2009-12-17
[SIZE=4]UPDATE:[/SIZE][SIZE=1] 

[SIZE=2]I found code that gets me past the previous point. The code is;

~$ modprobe raw1394
~$ sudo chmod a+rw /dev/raw1394

Then, ~$ jackd -d freebob      runs and has this as output;

~$ jackd -d freebob
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
LibFreeBoB ERR: Dropped packets on connection 1

The line '[/SIZE][/SIZE][SIZE=1][SIZE=2]LibFreeBoB ERR: Dropped packets on connection 1' is repeated until I use a keyboard interrupt which then out puts;

^Cjack main caught signal 2
no message buffer overruns


If anybody has any ideas about this or can solve the problem please post.

Thanks and Kind Regards[/SIZE][/SIZE]

---

