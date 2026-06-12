---
title: "why Brasero gives error burning disc?"
date: 2010-11-19
forum: General Help
---

### Post by rebeltaz on 2010-11-19
I have had this happen several time. When a customer comes in with a Windows system with a bad motherboard/CPU/etc and they want the data on the drive burned to a CD/DVD, I will mount the drive using a USB-IDE adapter. I then copy the data to my hard drive. From there I copy it to the CD/DVD Creator window. When I tell Brasero to burn the disc, it will tell me that the files are not compatible with Windows (interesting in itself since the files came off a Windows system) and asks if I want to disable Windows compatibility or truncate/rename the files. Regardless of which option I select, the disc gets burned and on the final comparison phase, I get an error. This last time the error said that it couldn't read the /DO& directory. 

Thing is, when I do a diff on the source directory and the discs directory, there are no differences. I can copy the entire disc back to my hard drive without any errors and running diff on that still doesn't show any differences. Then I tried running du on both directories and the final directory sizes match. I know that isn't the same as running a checksum check, but that is the closest I know how to do. And since the error log isn't very informative (I have no idea what /DO& is) I don't know what file is supposedly failing the comparison.

Can anyone shed some light on this problem? Thank you.

::edit::

I just installed a java program called CompareFolders3 and ran that on the two directories. When I compared the two xml files that the program created, there are no differences. So why did Brasero tell me there was an error?

---

