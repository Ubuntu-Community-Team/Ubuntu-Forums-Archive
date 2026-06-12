---
title: "Prevent External Drive from sleeping"
date: 2010-08-26
forum: General Help
---

### Post by Xeijin on 2010-08-26
Hi There,

I have a Hitachi SimpleDrive [([SIZE=1]LS-1000-EMEA)[/SIZE]]("http://www.amazon.co.uk/Hitachi-LS-1000-EMEA-3-5-inch-Simpledrive-External/dp/B002TV5JWW/ref=cm_cr_pr_product_top") it has an "Auto-sleep" function which I believe is controlled by the enclosure itself.

The problem I'm having is that when the drive goes to sleep Ubuntu does not seem to be able to wake it up again. I am running Karmic 9.10 as a stripped down install with XBMC as a front-end. I cannot access the drive at all when it does this.

I'm not sure if the problem is that the drive is formatted as NTFS. I notice that when the drive is connected to my Mac or PC it resumes no problem (with a slight delay as the drive gets out of standby) but with Ubuntu it just seems to stop responding. When I reboot the drive is not mounted by Ubuntu. Physically, the blue LED indicator on the drive is frozen (i.e. lit-up) rather than flashing as it normally would. I have to actually unplug (from the mains) and plug it back in for it to work.

I have tried using sdparm, but as I say I think the sleep function is controlled by the enclosure and thus sdparm gives me no standby options.

Any help would be greatly appreciated.
[[SIZE=1][/SIZE]]("http://www.amazon.co.uk/Hitachi-LS-1000-EMEA-3-5-inch-Simpledrive-External/dp/B002TV5JWW/ref=cm_cr_pr_product_top")

---

### Post by viralmeme on 2010-08-26
> **Xeijin said:**
> Hi There, I have a Hitachi SimpleDrive .. The problem I'm having is that when the drive goes to sleep Ubuntu does not seem to be able to wake it up again

Try [Hdparm]("http://en.wikipedia.org/wiki/Hdparm") ...

---

### Post by Xeijin on 2010-08-26
> **viralmeme said:**
> Try [Hdparm]("http://en.wikipedia.org/wiki/Hdparm") ...

Hi There,

Just tried hdparm, as well as sdparm, tried various options none of which seem to have worked. As I said I think the enclosure itself has its own power management (for example the drive does not have a physical power switch -- it turns on as soon as both a power and usb cable are connected).

**Edit:** OK, after some experimenting with hdparm I've realised that the state when the LED activity is "frozen" is when my drive is in idle mode. By running the command "hdparm -y /dev/sdd" (and putting it into "standby" mode) it magically starts working again. 

Does anyone know if it is possible to disable this altogether? I have tried messing about with hdparm but with no avail, if I can put the drive in and out of this state manually then surely I can disable it altogether?

If not does anyone know how to make Ubuntu send the standby command when accessing the drive?

**Edit 2:** Right, seems I misread the instructions for the -S parameter. I've since run "hdparm -S 0 /dev/sdd", which apparently disables any standby functions and seems to have gone through alright. I will observe the drive for a couple of hours to see if this has fixed my problem.

---

### Post by elnetotaca on 2011-03-22
awesome!
after 5 hours looking around your command line was my answer!
thanks lol.
what I did was;
sudo fdisk -l
find out my external hdd was /dev/sdc1
so the command line Fixed my problem was;

sudo hdparm -S 0 /dev/sdc1
in case anybody else can use the info.
Thanks again.

---

