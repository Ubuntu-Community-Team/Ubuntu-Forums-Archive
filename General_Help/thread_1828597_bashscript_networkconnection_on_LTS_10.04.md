---
title: "bashscript networkconnection on LTS 10.04"
date: 2011-08-19
forum: General Help
---

### Post by Hetepeperfan on 2011-08-19
Dear Community,

I've a question wich is related to the difference between a normal commandline interface and one small script that should run the three commands in one.

So what i'm trying to do is ```
$sudo modprobe rt3572sta
``` which should load the ralink driver for my network card.
Then I run: ```
$sudo wpa_supplicant -B -c /etc/wpa_cupplicant.conf
```to start a wpa_connection with my router.
and finally I do: ```
$sudo dhclient ra0
```to obtain a network adres

The above will start my network connection and it runs nicely.
However, me trying to be smart thought heey I can make a bash/sh script to run these commands in one go and I called it: connectme.sh

so this is the script:
```
#!/bin/bash

modprobe rt3572sta
wpa_supplicant -c/etc/wpa_supplicant.conf -ira0 -Dwext -B
dhclient ra0

```and then I run it like:```
sudo ./connectme.sh
```however then no luck. 

Would someone please enlighten me why the three separate command line commando's work but the script failes.

yours faithfully and cheers,

Maarten

---

### Post by Azdour on 2011-08-19
Hi,

This is only a guess. I wonder if you adding the sleep command after each command will make it work? That should give each command a chance to run and finish before calling the next command, e.g.:

```
#!/bin/bash

modprobe rt3572sta
sleep 10
wpa_supplicant -c/etc/wpa_supplicant.conf -ira0 -Dwext -B
sleep 10
dhclient ra0
```

That will wait 10 seconds before calling the next command.

---

### Post by Hetepeperfan on 2011-08-19
Hi Azdour this does seem to work! However with values of like 5 sec to sleep it's instable, thus it takes still a significant amount of time. Perhaps I should just start it as a background process.

thanks,

Maarten

---

