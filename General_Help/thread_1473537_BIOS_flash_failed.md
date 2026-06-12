---
title: "BIOS flash failed"
date: 2010-05-05
forum: General Help
---

### Post by Desolathor on 2010-05-05
So I'm running a dual bot xp and ubuntu 10.04 and I decide to update my BIOS using flashROM so it would support usb booting.

All seemed fine, but I guess my computer disagreed cause now it barely even loads into BIOS (at least it does that...) but I have no idea how to fix it. 
I already destroyed 1 cd making an iso image of an older bios driver but the default app EZflash doesnt recognize it....

I'm running ASUS M2N-sli deluxe motherboard if that info's worth anything.

I guess it serves me right for dealing with things I dont know well.
I hope you can help me...thanks,
tomas

oh and lemme know which other info I should provide

---

### Post by dino99 on 2010-05-05
if you are not used to flash bios, i hope you have read what ASUS says about flashing. How have you flashed it ?

try to reset the bios: unplug power cord first, wait a few seconds then remove the battery, wait again few minutes, maybe there is a jumper too, you may read the manual, then put the battery back in and power on. See now if it can boot.

If not, then re-flash with floppy

---

### Post by Desolathor on 2010-05-05
I wish I did read what they say about it... I will definitely do that now.

I'll try your suggestion and also another note, the computer doesnt have a flash drive, thats why I tried with the CD. I'll get back to you once I unplug etc.

---

### Post by Desolathor on 2010-05-05
The simplest solutions are always the best... It worked, only barely loaded the system but I'm in. The question is, what now, tho? :D I hope I'm not a bother...
Oh and the load showed an error:

could not update ICEauthority file /home/tomas/.ICEauthority

Thanks for the help so far, I hope you can help me setting things back to normal too.

tomas

edit: I remember making a backup of bios in the flashROM terminal but I wouldnt be me if I made a note where it is...lol

---

### Post by dino99 on 2010-05-05
i've a fealing about you : you are a lucky guy  :p

so now you are booting with the new bios ?

dont worry about: /home/tomas/.ICEauthority, its nothing

sudo chown tomas\: ~/.ICEauthority
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by Desolathor on 2010-05-05
I ran the commands before the edit (without sudo chown tomas\: ~/.ICEauthority) and it checked disks so it boots without problems now.

If anything, it flashes an error screen for a brief moment before the ubuntu screen but it works normally otherwise.

You absolutely saved and made my day! :)

---

### Post by dino99 on 2010-05-05
> **Desolathor said:**
> I ran the commands before the edit (without sudo chown tomas\: ~/.ICEauthority) and it checked disks so it boots without problems now.

If anything, it flashes an error screen for a brief moment before the ubuntu screen but it works normally otherwise.

You absolutely saved and made my day! :)

ok, now you know that flashing can be risky ;)
oh sorry i forgot that you need to tweak again the settings of bios of course (date, ...)

---

### Post by Desolathor on 2010-05-05
I'll sure think twice before pulling of a stunt like this again... thanks for your help :)

---

