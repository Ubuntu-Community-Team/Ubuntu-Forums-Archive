---
title: "Overheating issues are KILLING me!!!"
date: 2011-04-09
forum: General Help
---

### Post by friendlybox on 2011-04-09
ok, i could really use some help with this.

i recently installed Ubuntu 10.10 (64bit) on my laptop (Toshiba satellite L300 64bit) and have since had horrible issues with the machine overheating.

when the system is idle, the temp is decent, a bit warm maybe.
if i start browsing the Internet, temp goes wayyyy up.
i cant watch more than 1 and a half minutes of a youtube video without the system's temp exceeding acceptable limits, and shutting itself down.

i have tried both the 32 bit and 64bit versions of ubuntu 10.10, as well as a 64bit version of 10.4. same overheating issues with all of these.

i am 99.999999 percent sure that it is an issue with my laptop's cooling fan, as although it appears to be spinning, it is so quiet that i would think it was off completely if i were to not tilt the laptop back and check to see if it is spinning. also, the speed of the fan does not change, regardless of the machines temp. even before it shuts off because of extremely high temps, the fan is still running at that same speed.

Can someone please help me out? i signed up for this forum just so i could ask this.
also, please try to explain your solutions well, i am still new to ubuntu and linux OS's in general.



as a side note, i am currently downloading fedora 14 , a different linux distro, to see if there is any difference.

---

### Post by pqwoerituytrueiwoq on 2011-04-09
1) remove dust
2) install flash block addon
3) get a cooling mat with fan
4) lower cpu speed using cpu scaling applet
5) 32bit uses less power (less voltage=lower temp)

---

### Post by friendlybox on 2011-04-09
> **pqwoerituytrueiwoq said:**
> 1) remove dust
2) install flash block addon
3) get a cooling mat with fan
4) lower cpu speed using cpu scaling applet
5) 32bit uses less power (less voltage=lower temp)

i am using a laptop, how do you propuse moving dust?

can you explain how to lower cpu speed with this scaling applet? i am sorry, i am an absolute newb to all of this?

and finally, as i said, i have tried both 64 bit and 32 bit, figured 32 bit would run better, no luck....

---

### Post by pqwoerituytrueiwoq on 2011-04-09
assuming it has years of dust in it look up the manual to figure out how to open the case (unless it is a strait forward design)
use a can of air (15-25 psi dry air)
if you blow it out frequently via the ventilation holes you can avoid opening it up usually

right click panel
add to panel
add "CPU scaling Frequency Monitor"
click applet 
select speed (or governor ex conservative)

---

### Post by friendlybox on 2011-04-09
> **pqwoerituytrueiwoq said:**
> assuming it has years of dust in it look up the manual to figure out how to open the case (unless it is a strait forward design)
use a can of air (15-25 psi dry air)
if you blow it out frequently via the ventilation holes you can avoid opening it up usually

right click panel
add to panel
add "CPU scaling Frequency Monitor"
click applet 
select speed (or governor ex conservative)

I can't believe it, but i actually made it through a 6 minute youtube video without the temps rising to the point where the system unexpectedly powers down.

applied the flash addon, set cpu scaling frequency monitor to the panel and set it appropriately, things seem to be going better.

i'll try to put it under a bit more load, ill report mack in a few

---

### Post by steve161 on 2011-04-09
Toshiba Satellites, and the bios they use, are notorious for causing this problem with linux.
 
In the terminal, run "gksudo nautilus" (without quotes).  Go to file system-etc-default-grub and  add either acpi_osi=Linux or acpi=copy_dsdt to GRUB_CMDLINE_LINUX_DEFAULT.  It should look like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
or
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=copy_dsdt "

Make sure to save the file after each change, and then run sudo update-grub in terminal and reboot.

Try  one at a time and see if it solves the issue.

These changes have worked for some (myself included) and not for others.  If both of them do not work for you, remove the added lines and, again, run sudo update-grub, and you will be back where you started from.

---

### Post by desnaike on 2011-04-09
My laptops intake vents are on the bottom, if I place it on my lap or sofa,cloth chair, table with table cloth it overheats. I keep it on a desk or table with vents unblocked and no problems. Just because it's a laptop does'nt mean it should sit in your lap.

---

### Post by drewsus on 2011-04-10
You seem to be taking bits and pieces of advice that people are giving, but you should do ALL that has bene suggested. You don't want to just 'get by' and have your system constantly running just under the heat threshold for which it would normally shutdown. 
I could be mistaken, but I say this because it seems you have not opened it and cleaned out built up dust. 
This is your NUMBER 1 issue. It should be done first and would probably fix your problem all together. 
My brother's laptop was like cleaning the lint trap out of a laundry drier. 
Furthermore, to expand on desnaike's suggestion of not having your laptop on your bed, sofa, pants (re: linty fabrics): This is where most of the dust and lint comes from that ends up inside of your laptop. Just try to avoid it. The dynamic nature of the fabric's form also lends it to just blocking the vents, further stressing your system. 
Think of system stress as not managing a diabetics blood sugar levels. The live shorter lives.

---

### Post by DeMus on 2011-04-10
I know it's a different story but I have a Dell Latitude 110L also with a ventilation opening at the bottom. The laptop has very tiny feet so the bottom plate of the housing is almost touching the table. That's why I always place it on three thick yellow markers to lift it up a little, making the air flow as it should.
Btw, the yellow markers could also be green, red or whatever colors. It's just I have three yellow ones here. :D

---

### Post by drewsus on 2011-04-10
> **DeMus said:**
> I know it's a different story but I have a Dell Latitude 110L also with a ventilation opening at the bottom. The laptop has very tiny feet so the bottom plate of the housing is almost touching the table. That's why I always place it on three thick yellow markers to lift it up a little, making the air flow as it should.
Btw, the yellow markers could also be green, red or whatever colors. It's just I have three yellow ones here. :D

Personally, I recommend the pink ones. They have more lift and greater air flow.

---

### Post by marvinudy on 2011-04-10
friendlybox,

I run several Ubuntu clones on a Toshiba Satellite-a136-s2246 and had a heat issue when I maxed out the memory.  First I tried a fan based cooling pad that turned out to be 'junk'.  Problem was solved by placing a 12"x12" mesh wire cookie cooling rack under the laptop sitting on the kitchen desk.

I think it came from the 'Dollar' store.


best regards,

marvinudy

---

