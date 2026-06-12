---
title: "Loading scripts on boot"
date: 2010-11-15
forum: General Help
---

### Post by leehamer on 2010-11-15
Evening, 

I have had to replace the hard drive in the laptop I am using so a fresh installation of Ubuntu 10.04 has gone on, I am unable to get the wireless to start unless I type the following in termial

> sudo modprobe -rv ath5k
sudo modprobe acer-wmi
sudo modprobe -v ath5k                                 

I put this into a file previously and it ran on boot however I cannot remember how I did it, can anyone offer some advice on how I do this?

cheers

---

### Post by yetiman64 on 2010-11-15
Is this thread really solved ? If it is, could you please explain (for the benefit of others searching the threads for answers) how it was solved. Thanks.

If not, you can use /etc/rc.local to run commands on every startup (though the commands won't need "sudo" as this file runs with root privileges at startup)

In /etc/rc.local insert the commands so the end section of the file looks like,

> # By default this script does nothing.

modprobe -r ath5k
modprobe acer-wmi
modprobe ath5k

exit 0Is this how you previously did it ?

Edit2: [COLOR=Blue]the suggestion in post #3 sounds a better solution for modules, if you can get it to work[/COLOR]. I've also removed the verbose switch (v) from the quote box commands as they are not running in a terminal and you won't see them being processed if you decide to use rc.local.

---

### Post by lsmobrian on 2010-11-15
You should probably do that stuff in /etc/modules, add these two lines, hopefully that should work out the ordering
```
acer-wmi
ath5k
```

If that doesnt work, also try adding ath5k to /etc/modprobe.d/blacklist.conf
```
blacklist ath5k
```

---

