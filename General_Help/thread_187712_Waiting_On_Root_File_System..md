---
title: "Waiting On Root File System."
date: 2006-06-03
forum: General Help
---

### Post by darkcow on 2006-06-03
***sparknotes edition*** install dapper beta "waiting on root file system bug"
try evms_activate. doesn't work because linux doesn't say my partition exists.

i next try it on my other HD and it works

i then do a secure format of my previous partition and install the official dapper. (not beta) and same problem

***end sparknotes edition***

this problem occured when i first install ubuntu with the Dapper Beta. everytime i install it the first time i boot it just times out on "waiting on root file system" so i tried evms_activate command. but that didn't work considering the linux didn't even acnowledge that my HDA7 partition doesn't even exist. when obviously it does cuz then how did it start linux up this far?


so i decided to install ubuntu on my other hard-drive *note this hard-drive was dying on me... clicking like crazy. but maxtor wouldn't acknowledge it was dead untill yesterday* and the problem was gone. i could boot every time with out problems. 


now that the official dapper was released i decided to give it one last try on my main hard-drive. the reason for this is because my other hard-drive died in 3 months flat out.. which is very odd. and this time i figured that the only diffrence between my first attempt on hda7 partition and my other hard-drive. is that hda7 had windows XP x64 edition on it before hand. so in partition magic i did a secure erase so all the data was 100% gone. i then re-installed ubuntu. same problem. so i gave up. i next just watched a movie in windows. i thought i shut down the computer, but actualy i hit restart. i went a brushed my teath. i came back to my pleasure to see ubuntu booted up nicely. i next ran automatix, and yea... rebooted again. same problem.


(btw this problem or problems similar happen on diffrent distros)




my question to you... is my hard-drive a windows lover?

---

### Post by rcarring on 2006-06-03
Only if you have usb external drives attached. =D

Seriously, it sounds like there is a fundamental difference between the dead Maxtor and your main drive. I would hazard that the main drive is sata. The hard drive that failed sounds like a warranty problem as most hard drives (even abused ones) will last a long time before bad clusters start appearing.

---

### Post by darkcow on 2006-06-03
well, i did send in the hard-drive on warrenty. and it should be back in my hands in a few days probably more.... so im guessing its just that my current hard-drive likes to corrupt EXT3 partitions.. which is odd.... i was just searching for a reason. and if so... if theres a solution.

---

