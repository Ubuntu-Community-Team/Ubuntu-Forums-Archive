---
title: "Can no longer run Eclipse and strange chmod behavior"
date: 2011-04-18
forum: General Help
---

### Post by Rupe120 on 2011-04-18
I had Eclipse running just fine from a separate drive in 10.04 and after I upgraded to 10.10 it now tells me that "There is no application installed for executable files." 

Strange, but kind of understandable because I discovered the file had no executable permissions. So I tried to give it the proper permissions, chmod thinks it's doing something, but when I check the file afterward nothing has changed. 

I attached a screen cap of chmod saying the file is being set properly and then showing that it still has only rw permissions. (And yes I did try chmod 755 ./eclipse also, same result)

1) Why would an upgrade cause Eclipse to behave this way.

2) Why can't I change the permissions?

3) How do I get Eclipse to run again?

Thanks
Josh

---

### Post by antaios256 on 2011-04-18
> **Rupe120 said:**
> I had Eclipse running just fine from a separate drive in 10.04 and after I upgraded to 10.10 it now tells me that "There is no application installed for executable files." 

Strange, but kind of understandable because I discovered the file had no executable permissions. So I tried to give it the proper permissions, chmod thinks it's doing something, but when I check the file afterward nothing has changed. 

I attached a screen cap of chmod saying the file is being set properly and then showing that it still has only rw permissions. (And yes I did try chmod 755 ./eclipse also, same result)

1) Why would an upgrade cause Eclipse to behave this way.

2) Why can't I change the permissions?

3) How do I get Eclipse to run again?

Thanks
Josh

while i really dont have an answer for any of those questions i would recommend attempting the chmod with the sudo command, as effectively root can do anything.

---

### Post by Rupe120 on 2011-04-18
I did run it with sudo. If you look at the screen cap it shows root at the head of the prompt. I had done a sudo -s before the chmod command.

---

### Post by SavageWolf on 2011-04-18
Are you trying to run it on a FAT or NTFS drive? Because those can't handle permissions, try copying it to your main disk.

---

### Post by Rupe120 on 2011-04-18
> **SavageWolf said:**
> Are you trying to run it on a FAT or NTFS drive? Because those can't handle permissions, try copying it to your main disk.

Ding ding ding!!! We have a winner! Thank you that was it!

---

### Post by alguin2 on 2011-04-18
I started seeing the same behavior after I upgraded from 8.0 to 10.  From your screenshot, I think we have the same problem. Since your path starts with /media, I'd guess that you have a USB device (or something similar) whose format doesn't lend to unix/linux filesystem privs. 

In any case, this was answered in another thread (basically, the answer is to remount with the exec option): 
  [http://ubuntuforums.org/showthread.php?t=1686624](http://ubuntuforums.org/showthread.php?t=1686624)

---

