---
title: "/tmp missing"
date: 2011-03-12
forum: General Help
---

### Post by gudurukarthik on 2011-03-12
hi, im a new user and since a while when ever i restart or start my laptop it says that there is some error and will check for it and it states that /tmp files missing. i dont know what more info u will be needing  but im happy to provide with any more info required to solve this problem. 
thank u

---

### Post by oldos2er on 2011-03-12
You can try running fsck, which sometimes clears up these problems. Before you shutdown, run **sudo touch /forcefsck** in a terminal, and fsck will be run on next boot.

---

### Post by gmargo on 2011-03-12
So is it /tmp that is missing?  Or is it some files that were formerly saved in /tmp are missing?

At reboot time, the files in /tmp are removed.  Perhaps you a running an application (pdf viewer?  text editor? mp3 player?) that was using a file that was downloaded through the web browser and saved in /tmp?  Which application complains?  About what file?

---

### Post by gudurukarthik on 2011-03-12
k i will try with the code . and i am not talking abt the missing applications in the /tmp file , i notice that the system is stating that their is an error and it needs to be fixed . i have tryed to install windows 7 also during this time and it also stated that some file is missing ( like bous , or some thing like that . ) it whould be really helpful if i can test the entire system files and c if there are any erroes in it, so can u give me any code for that too. 
thank u for the help . 
peace

---

