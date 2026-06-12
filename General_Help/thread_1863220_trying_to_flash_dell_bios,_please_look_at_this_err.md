---
title: "trying to flash dell bios, please look at this error. thanks"
date: 2011-10-17
forum: General Help
---

### Post by slixz85 on 2011-10-17
i am trying to flash the bios on my dell optiplex gx260 which has had some video issues alot. after i run the sudo dellBiosUpdate -u -f data1.hdr i get this error message below. i used the command wine R89214.exe -writehdrfile -nopause before hand to extract the .hdr file there was only this one in the exe along with a bunch of other files but the hdr is what a website said you only needed. 

thanks to any help



^[[Aace@optiplexsudo dellBiosUpdate -u -f data1.hdr
[sudo] password for ace: 
Performing BIOS update...
Traceback (most recent call last):
  File "/usr/sbin/dellBiosUpdate", line 115, in <module>
    def ensureRbuDriver():
  File "/usr/sbin/dellBiosUpdate", line 153, in main
    exit_code = updateBios(HdrFile(options.hdr), options)
  File "<peak.util.decorators.rewrap wrapping libsmbios_c.rbu_hdr.__init__ at 0x0875F17C>", line 3, in __init__
  File "/usr/lib/python2.7/dist-packages/libsmbios_c/trace_decorator.py", line 108, in trace
    result = func(*args, **kw)
  File "/usr/lib/python2.7/dist-packages/libsmbios_c/rbu_hdr.py", line 65, in __init__
    raise InvalidRbuHdr("Not a valid RBU HDR File. Header doesnt have '$RBU' header.")
libsmbios_c.rbu_hdr.InvalidRbuHdr: Not a valid RBU HDR File. Header doesnt have '$RBU' header.
ace@optiplex:~$

---

### Post by Gyokuro on 2011-10-17
You have to boot your system via a boot floppy. At first you have to make a boot floppy and afterwards extract the content of this archive to your boot floppy. Dell mentioned the steps under Installation Instructions - you can't flash your bios via wine!! Read throw the steps as in case something goes wrong during flashing your BIOS you can teach your laptop to fly through your window. **You do this one your own risk!!!**

---

### Post by slixz85 on 2011-10-17
alright i dont remember seeing anything on the site i was on about a floppy drive, i will look some more. i have tooken my floppy drive out since they are so outdated. couldn't i still just do it by flash drive. and could u please let me know how to do this. i understand some problems could arise but this video card is the worst i have ever used so glitchy. i have another pc about the same specs as this one with an internal card that acts the same way. alot of people have had these problems with their video cards on these dells. my other thread [http://ubuntuforums.org/showthread.php?t=1861741](http://ubuntuforums.org/showthread.php?t=1861741) is what lead to trying to do this, as other websites say to flash the bios SOMETIMES for video trouble

---

