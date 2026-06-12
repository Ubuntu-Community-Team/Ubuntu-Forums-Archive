---
title: "Upstart will not run / kills daemon instantly"
date: 2011-12-01
forum: General Help
---

### Post by AnVoWiDo on 2011-12-01
I am trying to use upstart to start a daemon on the "input-device-added" event, however if someone knows of a different method to start something on the same event that doesn't involve Upstart I would be very pleased too. Anyway, when the input-device-added event is emitted myservice.conf gets called correctly and the first few lines of script get parsed. But when the daemon gets launched it never completely starts running and Upstart seemingly kills it prematurely.

I've tried using Upstart in two different ways, both give me the same problem:
```
author "AnVoWiDo"
start on input-device-added
script
device='printinputdevices | grep thecorrectdevice'
echo $device 
/start/my/daemon -option device
end script
```and also ```
author "AnVoWiDo"
start on input-device-added
exec myscript.sh
```where myscript.sh file contains the script above.  The echo command in there is just for diagnostics and outputs correctly in both methods.

Running myscript.sh from terminal will start the daemon perfectly fine with all the expected output. The same is true for running the "/start/my/daemon -option device" command, both will output something along the lines of
> device  0: /dev/input/event9 mydevice
Display name: :0But when launching it from Upstart (with service myservice start or by plugging in a new input device) the output halts midway 'Display name: :0' and only logs 'Display name: ' at which point Upstart kills the process. It looks to me like the double colon in the output is the culprit (or of course the :0), and perhaps Upstart mistakes it for an error code of sorts?

Anyone know of a different method of starting my service at the correct moment?
Perhaps I have missed something stupid and obvious while making the Upstart conf file which can be fixed?
Lastly maybe Upstart can in some way be convinced to ignore the ": :0" in output (if this really is the cause of course) and keep running the daemon?

---

### Post by AnVoWiDo on 2011-12-01
Shameless bump to bring renewed attention to my problem. I've reworded a lot of this in hopes of improving legibility and getting some help. Apologies if this breaks the local conventions.

---

### Post by AnVoWiDo on 2011-12-03
Stripping the echo command out, sending all output to /dev/null and nesting up to 4 scripts all do not work (the last one was more fun than it sounds).

---

