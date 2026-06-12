---
title: "How do I update an offline/sneakernet desktop"
date: 2011-04-07
forum: General Help
---

### Post by Elludium_Q-36 on 2011-04-07
How do I update and version upgrade an offline desktop box via "sneakernet"?  (Sneakernet means it's an offline box and I bring files via a thumb-drive or CD :-)

I have tried to generate a download script via Synaptic Package Manager with no success.  I would be using a windows box at the library or a net cafe'.

I tried updating packages from a 10.04 CD but it only offers a few.

I would like to upgrade to the latest LTS without losing my settings & data.

Thanks in advance for any helpful advice.

---

### Post by zvacet on 2011-04-07
Lucid is latest LTS so you can gat updates for it.Try [Keryx.]("http://keryxproject.org/")

---

### Post by Elludium_Q-36 on 2011-04-12
Thanks zvacet,

I'll give it a whirl.

---

### Post by Elludium_Q-36 on 2011-04-13
I downloaded Keryx to my thumb-drive.
I wonder if that covers version upgrades too...

Anyway, I'm in 8.04 LTS and want to go to 10.04, the next LTS.

I burned a 10.04 alternative CD and followed what I found here: [https://help.ubuntu.com/community/LucidUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD](https://help.ubuntu.com/community/LucidUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD)
I was able to call the cdromupgrade script in a Konsole terminal but I got the following error(s) ```
kubuntu@Kubuntujc1:/media/cdrom1$ sh cdromupgrade
/usr/lib/python2.5/sitepackages/apt/__init__.py:18: FutureWarning: apt API not
stable yet
warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
File "/tmp/tmp.xFtvfD6460/lucid", line 7, in <module>
sys.exit(main())
File "/tmp/tmp.xFtvfD6460/DistUpgradeMain.py", line 141, in main
logdir = setup_logging(options, config)
File "/tmp/tmp.xFtvfD6460/DistUpgradeMain.py", line 86, in setup_logging
filemode='w')
File "/usr/lib/python2.5/logging/__init__.py", line 1240, in basicConfig
hdlr = FileHandler(filename, mode)
File "/usr/lib/python2.5/logging/__init__.py", line 770, in __init__
stream = open(filename, mode)
IOError: [Errno 13] Permission denied: '/var/log/distupgrade/main.log'
kubuntu@Kubuntujc1:/media/cdrom1$  
```

I then read @ [https://help.ubuntu.com/community/LucidUpgrades#Network%20Upgrade%20for%20Kubuntu%20Desktops](https://help.ubuntu.com/community/LucidUpgrades#Network%20Upgrade%20for%20Kubuntu%20Desktops)
> Because Kubuntu 8.04 was not an LTS release and has passed its end of life, direct upgrades to Kubuntu 10.04 LTS from Kubuntu 8.04 are not supported. Please follow the directions for upgrading Kubuntu 8.04 to 9.10 first, then follow the directions above for upgrades from Kubuntu 9.10. 

I'm not sure why Ubuntu 8.04 is an LTS while Kubuntu 8.04 is not.

Anyway, I'll grab Kubuntu 9.10 from: [http://releases.ubuntu.com/kubuntu/9.10/](http://releases.ubuntu.com/kubuntu/9.10/) and give it a go :-|

---

