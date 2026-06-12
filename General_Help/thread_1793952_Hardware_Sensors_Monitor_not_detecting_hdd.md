---
title: "Hardware Sensors Monitor not detecting hdd"
date: 2011-06-30
forum: General Help
---

### Post by Killah on 2011-06-30
After several attempts, the Hardware Sensors Monitor cannot detect hdd. The following is what was done.

I originally installed gnome sensor applet through ubuntu software center and without paying much attention I also proceeded not to have the hddtemp boot up. After adding to the panel the hardware sensors monitor, the hddtemp was not there so..ive proceeded to do the following in the terminal:

sudo dpkg-reconfigure hddtemp
sudo chmod u+s /usr/sbin/hddtemp
sudo sensors-detect and yes to all
sudo modprobe..there were two chip drivers

when i did sudo hddtemp /dev/sda the temp is detected.

I added back the applet to the panel but the sensor is still not there.

sudo dpkg -s hddtemp also returned the status that everything was installed.

so i rebooted

i double checked in the synpatics manager if all the programs are installed. I have lm-sensors, hddtemp and sensors-applet.

in the command line..i did dmesg

removing and re-adding the applet to the panel proved futile and still cannot see hdd temps. 

Where did I go wrong?

---

### Post by foutes on 2011-06-30
sudo dpkg-reconfigure hddtemp


Did you allow hddtemp to start at boot when you ran the above command?

---

### Post by Killah on 2011-06-30
> **foutes said:**
> sudo dpkg-reconfigure hddtemp


Did you allow hddtemp to start at boot when you ran the above command?

I did say OK to boot at start up, to listen for incoming connections on all interfaces. I just tried again to reconfigure and still i cant see that option when i add the applet to the panel. At this point, I'm wondering if I shouldn't just altogether purge and re-install. I'm lost atm.

---

### Post by Killah on 2011-06-30
UPDATE:

I purged all the programs and re-installed them following a guide I found...however, on loading the chip drivers I get this returned to me

[I]sudo modprobe w83627ehf
FATAL: Error inserting w83627ehf (/lib/modules/2.6.35-30-generic-pae/kernel/drivers/hwmon/w83627ehf.ko): Device or resource busy[/I]

I cannot see any other reason except for this one why I would be having issues. Has anyone else encountered such issues? Looks like a kernel problem? Am currrently looking at how to fix this?!? any ideas on what my next step should be?****

---

