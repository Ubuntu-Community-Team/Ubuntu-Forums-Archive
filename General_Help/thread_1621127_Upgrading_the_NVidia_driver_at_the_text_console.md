---
title: "Upgrading the NVidia driver at the text console"
date: 2010-11-13
forum: General Help
---

### Post by CarstenF on 2010-11-13
Hi all,

using Ubuntu 10.10 amd64, my older NVidia card suffered a hardware failure last week, and so I replaced it with an NVidia GTS 450.

As the driver that was previously in use was nvidia-173, at the next boot with the new card the X server didn't start. I got to the text console, where the /var/log/Xorg.0.log had the message that the GPU/chipset is unknown to the driver. (well, ok ;) )

Some web searches revealed that the chipset GF106 of the GTS 450 is only supported by the NVidia 260.19.12 driver, which is not in the Ubuntu stock repositories, so I followed the instructions at [http://halvar.at/blog/?p=258](http://halvar.at/blog/?p=258) to install the latest driver from the PPA repository:

[FONT=Courier New] sudo aptitude install nvidia-current
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo aptitude update
sudo aptitude full-upgrade
[/FONT] 
In short, although all of the above worked fine, the problem is that even after a reboot, the system still uses the nvidia-173 driver (according to Xorg.0.log, and starting X still fails).

Before I tried the above, I also tried 

[FONT=Courier New]sudo aptitude install nvidia-current[/FONT]

alone, in order to get the latest driver that is in the stock repositories, but the result is the same in both cases.

What do I have to do in order to activate the nvidia-current driver (either stock or from the ppa above) instead of nvidia-173??

I tried to modify the proper blacklist file in /etc/modprobe.d/...  (sorry if the file names are slightly wrong - I'm typing all this from the top of my head, as the affected Ubuntu system has no graphics, and thus no graphical browser etc. ), but then there is the error:

    [FONT=Courier New]"Error: API mismatch: the NVidia kernel module has version 260.19.12, but this NVidia driver component has version 173.14.28 ..."[/FONT]

What can I do?

A thousand thanks for any help and hint.  :)

---

### Post by dcstar on 2010-11-13
> **CarstenF said:**
> 
........
What can I do?

A thousand thanks for any help and hint.  :)
Try:
```
sudo apt-get purge nvidia-current
sudo apt-get install nvidia-current
```

---

### Post by CarstenF on 2010-11-14
Hi David,
many thanks for your reply, but

> **dcstar said:**
> Try:
```
sudo apt-get purge nvidia-current
sudo apt-get install nvidia-current
```

while this worked without problems, it didn't help:
The system still tries to load the 173 driver.
On reboot or when I type startx, there is still the same API mismatch error message than above.

Anything else I can try?

Best regards,
Carsten

---

### Post by CarstenF on 2010-11-14
Hi again,

I just tried again with

[FONT=Courier New]sudo apt-get purge nvidia*
sudo aptitude install nvidia-current[/FONT]

Then it worked, purging (that I didn't dare do before) then re-installing did the trick; problem is solved (this message is written from the related system)!  :D

Best regards,
Carsten

---

