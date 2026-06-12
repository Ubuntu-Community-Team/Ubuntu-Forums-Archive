---
title: "Ubuntu 10.10 Maverick heavy hdd load_cycle"
date: 2010-10-25
forum: General Help
---

### Post by makmiler on 2010-10-25
Hi,

I just want to tell laptop users how they can protect their hdd from heavy load cycle count (spin up/down of the hdd) when using battery.

If you are not sure then just type this command several times in interval of 1-2 minutes, and you will see how much the hdd head spins down, and up:

```
sudo smartctl --all /dev/sda | grep -i load_cycle
```

Change /dev/sda with appropriate hdd path for your pc.

If you notice spin difference in this time interval, then you have a problem.

Just do the following:

Create a file named 95hdparm-apm under /etc/pm/power.d/

```
#!/bin/sh
hdparm -B 254 /dev/sda
```

Change /dev/sda appropriately to your hdd.

Save it and do a ```
sudo chmod u+rwx,g+rx,o+rx /etc/pm/power.d/95hdparm-apm
```

Now you can put your laptop to sleep, and wake it up to see if this is working.

Just type ```
sudo hdparm -I /dev/sda | grep -i "Advanced power management level"
```

Change /dev/sda appropriately.

It should say 254, and **not** 128.

---

### Post by siepo on 2010-10-31
Thanks for this.

---

### Post by beruic on 2010-11-15
This fixed everything for me too. Installing laptop-mode-tools made my computer unable to suspend and hibernate.

---

