---
title: "lucid ram usage"
date: 2011-08-29
forum: General Help
---

### Post by astroclast on 2011-08-29
Hi,

I just installed Ubuntu 10.04 on my Thinkpad T61 laptop (I use the GNOME desktop environment.)  Of the 2GB of available RAM, when no other application is running, only 500 MB are free.  After I load, say, Chrome and Thunderbird, which I use at all times, I am left with under 200 MB of RAM.

I wonder if there is a way to tweak GNOME's memory usage, and if so, if anybody has any recommendations to that effect.  (None of the default gnome-* commands seems relevant.)

If not, does anyone know how I could find the maximum memory supported by my motherboard?

Thanks.

---

### Post by sisco311 on 2011-08-29
[http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage)

---

### Post by astroclast on 2011-08-29
Great, thanks!

I don't fully understand how RAM works, so please bear with me.

I posted this thread because since I switched from 08.04 to 10.04 simple tasks such as closing application windows appear to take longer than they used to.  If RAM isn't the culprit, I wonder what could cause the slower response times.

I have been thinking of upgrading to 4GB or more of RAM, but it sounds like that wouldn't probably affect things much, except maybe through the RAM speed?  (My current memory cards are at 667 MHz.)

Thanks again.

---

### Post by garvinrick4 on 2011-08-29
Look at your cpu usage also, do not know what type of processor you have but look in System Monitor
under resources. Also make sure if it is running on the high side anything that is running flash video make
sure you set it at sd and hd or 240 and not 720 on Youtube. Flash is a hog on cpu usage.

---

### Post by astroclast on 2011-08-29
Thanks for the reply, garvinrick4.

On the system monitor, the memory usage is ~30%, the same as what 'free -m' reports under buffers/cache.  My CPU usage is ~13%, unless I start moving the cursor about violently, in which case it reaches almost 50%, remarkably.

On youtube I use the standard 360p definition, and I need to launch 3 youtube tabs on chrome in order to start reaching near 700MB (>30%) of memory usage, and more than 60% of CPU usage.

It looks like I was wrong to think that I need more RAM, but I still don't understand why certain actions seem to take longer under Lucid.

Any ideas are welcome.

My system is:
```

$ sudo dmidecode --type 4
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0006, DMI type 4, 35 bytes
Processor Information
	Socket Designation: None
	Type: Central Processor
	Family: Other
	Manufacturer: GenuineIntel
	ID: FB 06 00 00 FF FB EB BF
	Version: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
	Voltage: 1.4 V
	External Clock: 200 MHz
	Max Speed: 2200 MHz
	Current Speed: 2200 MHz
	Status: Populated, Enabled
	Upgrade: None
	L1 Cache Handle: 0x000A
	L2 Cache Handle: 0x000C
	L3 Cache Handle: Not Provided
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

$ sudo dmidecode --type 17
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x002C, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002B
	Error Information Handle: 0xFF01
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: SODIMM
	Set: None
	Locator: DIMM 1
	Bank Locator: Bank 0/1
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

Handle 0x002D, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002B
	Error Information Handle: 0xFF01
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: SODIMM
	Set: None
	Locator: DIMM 2
	Bank Locator: Bank 2/3
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

```


Thanks your responses!

---

### Post by garvinrick4 on 2011-08-29
I see no reason why you would be sluggish, looks fine to me. This will bump it up
to front to see if another user has a better answer for you.

---

### Post by bodhi.zazen on 2011-08-29
> **garvinrick4 said:**
> I see no reason why you would be sluggish, looks fine to me. This will bump it up
to front to see if another user has a better answer for you.

"sluggish" is subjective and can be from a variety of causes, more often from hardware drivers, including video and wireless.

Unlike windows, it is not often from ram use and I have never seen significant fragmentation on the hard drive.

---

### Post by astroclast on 2011-08-29
> **bodhi.zazen said:**
> "sluggish" is subjective and can be from a variety of causes, more often from hardware drivers, including video and wireless.

Unlike windows, it is not often from ram use and I have never seen significant fragmentation on the hard drive.


As I said, the new system seems to be sluggish when I terminate windows of 'heavy' applications, say Chrome, Thunderbird, Gimp, etc, but not when I close lighter GUIS, such as gnome-terminal.  That's what made me think of RAM in the first place.

The hard drive is brand new, and / is 53% empty.
```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.3G  4.1G  4.7G  47% /
none                  980M  324K  980M   1% /dev
none                  987M  1.1M  986M   1% /dev/shm
none                  987M   92K  987M   1% /var/run
none                  987M     0  987M   0% /var/lock
none                  987M     0  987M   0% /lib/init/rw
/dev/sda5             284G  4.6G  265G   2% /home

```

I should point out that the file systems for /dev/sda1 (and /dev/sda5) are encrypted ext4.  I didn't think that was relevant, but if these programs attempt to write data out before they terminate, maybe that'd slow things up a bit?

---

