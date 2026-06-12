---
title: "[Urgent]Keyboard lost functionality."
date: 2010-07-16
forum: General Help
---

### Post by asorron on 2010-07-16
my keyboard lost it functionality as it was used to be, something went wrong and im not sure what but it seems something wrote those settings to my pc's ROM or something.

Since i used the ubuntu and then the layout screwed up, I dont know what else to do as it seems it affected my windows too, i tried to recover to an older version of ubuntu that i had (as in i made a system backup using acronis) with all the things working right but it seems it wont help as the settings saved itself and I dont know where to change it back... im in such a panic as this thing never happen to me before, ctrl is right ctrl, right ctrl funtion as the FN key, the whole FN+Fx are wrong...

Help me out with this, im losing my patience to my computer.

---

### Post by asorron on 2010-07-16
fixed it... used the bios flashing method...
can someone tell me how the hell linux replaced my bios settings without prompting me?!

GOD im so pissed. im annoyed that the next time i'll use linux it'll screw up my pc for good.

---

### Post by simosx on 2010-07-16
Write down your hardware details in case someone else gets the same problem and searches the forum. Details such as laptop make and model, CPU, BIOS version, etc.

If the keyboard hardware is (almost) faulty, you may get some indications in /var/log/kern.log or in ~/.xsession-errors

---

### Post by NFblaze on 2010-07-16
Exactly...how did Linux mess with your bios, when 9 of 10 of bios tools are made to run in DOS. Please do specify your hardware as it maybe a hardware related.

---

### Post by asorron on 2010-07-16
Okay, so im running Gigabyte Q1580P P8700 2.53GHz chipset. so if anyone struggles it download the correct bios update from here [http://www.giga-byte.co.uk/products/product-page.aspx?pid=3223&dl=1#bios](http://www.giga-byte.co.uk/products/product-page.aspx?pid=3223&dl=1#bios) and make sure you run it at windows / dos. i've ran it through win7 and it fixed my system (though volume keys didnt work out and another flashing fixed them.) now my keyboard is fully operational and fixed, I dont have a clue what accessed those settings and changed them, I dont recall linux having any kind of ROM accessing features, but be aware that those things may occur,

I installed VMware which had tons of HD-stuckage when attempting to make WinXP virtual machine. it cause me to reboot my system couple of times and I think i ran it with root privileges, I used the G21 bios from the site, but then I saw theres new version so I upgraded it to that G51 at it.
Again, I have no clue what caused the keyboard functionality layouts to change, but I wish there was a log that tracks down any hardware changes in linux.

I hope I'll mark this one as solved. but feel free to add some stuff to help some more lost people as me.

---

### Post by asorron on 2010-07-18
God, the volume (fn+f7/f8) keys keeps on failing from time to time only in linux but it works on windows for some reason.. what can be causing it?

Status update; re-updated bios again to the previous versions, its running OKAY now but i hope i wont encounter it again...

---

