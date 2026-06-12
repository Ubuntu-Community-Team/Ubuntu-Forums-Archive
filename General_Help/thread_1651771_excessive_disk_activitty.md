---
title: "excessive disk activitty"
date: 2010-12-23
forum: General Help
---

### Post by carolinason on 2010-12-23
any known issues with system waits while hdd runs for many minutes? various tasks such as inserting an audio disk will cause hdd activity and stall system until r/w is over. what the system is reading or writing i have no idea. lasts minutes 

what log would i check?

system config in sig.

---

### Post by sefs on 2010-12-23
I am going to take a wild guess here and ask if you have a functioning swap partition.

---

### Post by carolinason on 2010-12-23
yes 2GB and i have 4 gb of ram free -m shows me it is being used

---

### Post by VCoolio on 2010-12-23
install iotop and see what process is causing the write activity

---

### Post by oldos2er on 2010-12-23
That definitely should not be happening with those system specs. You could try changing swappiness:

Make a backup copy of /etc/sysctl.conf ```
sudo cp /etc/sysctl.conf /etc/sysctl.conf.backup
```

Open the file in gedit ```
gksu gedit /etc/sysctl.conf
```

Add this line at the bottom of the file: **vm.swappiness=5**
Save and close it, and either reboot, or run ```
sudo sysctl -p
```

Please post back whether this helps or not.

---

### Post by carolinason on 2010-12-23
wow - cool help - love lucille ball pic - must tend to 22 month old - will be back - again thanks

---

### Post by carolinason on 2010-12-23
it appears to be a bad audio cd...

---

### Post by carolinason on 2010-12-24
thanks VCoolio, iotop is an invaluable tool and i never knew about it. it's output shows no disk i/o when this occurs. my hdd led indicates activity and the system monitor applet runs, but i can't do much else. 

this might be exclusive and not related to the other system waits i am experiencing. but i will definitely use iotop for that!

this disk, a mix cd causes my buddies cd player to york out too. i am rebuilding it for him for that very reason. stranger things have happened. 

i assume from iotop's output of no i/o, that no swap activity is going on, but can try playing with swappiness, something to cross off anyway.

thanks!

---

### Post by oldos2er on 2010-12-24
> **carolinason said:**
> love lucille ball pic 

Um...it's Phyllis Diller.  :)

---

### Post by carolinason on 2010-12-29
oops, i'm getting senile in my old age or was concerned over my daughter crying... i remember watching phyllis diller on laugh in.

i had two issues, one with a bad cd and one with random hdd activity. 

i solved the cd problem by just extracting what i could from it and throwing it away.

i solved the random hdd activity problem by enabling AHCI in the bios and reinstalling windows and ubuntu, since i have a dual boot. i have all sata and did not need to be in IDE compatibility mode. IDE compatibility mode worked with the 32 bit versions of windows & ubuntu, but i had this problem in both 64 bit os's. which i thought was interesting. i am new to the sata scene, however i had been running sata drives with a pci card in my circa 2002 board, which i just replaced with this sabertooth x58. perhaps this will help someone.

---

### Post by carolinason on 2011-02-27
this was actually solved due to a bad controller on a hard drive. disconnected the drive and the pc works fine. odd how it was only effected when running a 64 bit os.

---

