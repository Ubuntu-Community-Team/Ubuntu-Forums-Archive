---
title: "help needed to  understand hard disk diagnosis result"
date: 2011-04-03
forum: General Help
---

### Post by chinmay3 on 2011-04-03
I face "read error " while booting. sometimes it start normally. someone told me to check hard disk for errors. i used gsmartcontrol for this. but from its result i am unable to decide is this hard disk failure or just minor errors. can somebody tell me do i require to change my hd or it just something else to cause such error.
while reading threads regarding this problems i found some post saying it is due to bios setting . is this true?

---

### Post by coffee412 on 2011-04-03
> **chinmay3 said:**
> I face "read error " while booting. sometimes it start normally. someone told me to check hard disk for errors. i used gsmartcontrol for this. but from its result i am unable to decide is this hard disk failure or just minor errors. can somebody tell me do i require to change my hd or it just something else to cause such error.
while reading threads regarding this problems i found some post saying it is due to bios setting . is this true?

I would call it a drive problem. According to the info your drive temp is 118 F when running. However, I dont know if that is too high for your drive. Check the cooling of the drive. Otherwise I would pull the drive.

Just my 2 cents worth...

coffee

---

### Post by Jouke74 on 2011-04-04
I suggest you copy the important data to a backup drive and buy a new one. I am afraid this one is going to die soon, as all your SMART values say it is of old age (meaning close to end of life).

---

### Post by chinmay3 on 2011-04-04
Thanks for suggestions. can you recommend me which one good to buy?:confused:

---

### Post by Jouke74 on 2011-04-05
First check how the drive is connected to your computer (IDE, SATA etc). Then look for a new harddrive with the same connection (I would prefer Western Digital or Samsung). Install the new harddrive next to the old one in the computer. Boot with a live cd of Ubuntu and format & partiotion the NEW drive with gparted (make sure it is the NEW one). Then "dd" copy the whole system to the new drive. Disconnect the old drive and reboot. Run Ubuntu with recovery options. 

Another option is to get all personal data of your old harddrive and store it on USB / DVD / external harddrive. Remove the old harddrive and install the new harddrive. Install a new copy of Ubuntu (which also means you have a nice new clean system) and then copy your important data back. (Keep the old HD in case you missed something).  

Everything depends on your computer skill and the available hardware resources. If you are feeling unsure about doing this, contact someone of your friends or relatives that knows how to do this, to help you.

---

### Post by chinmay3 on 2011-04-05
Thanks a lot!!!!

---

