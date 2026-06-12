---
title: "Slow boot time to ubuntu after creating virtual disk for virtualbox guest"
date: 2010-06-04
forum: General Help
---

### Post by vrhahaha on 2010-06-04
My laptop boot up time increased considerably (10 seconds) after allocating a virtual drive for virtualbox guest. The guest installation did not work so i removed it along with the virtual disk. Now everytime when i boot to ubuntu, after inputting my password in the login screen, it takes much longer to load the system. And during the loading time the disk activity indicator light blinks indicating the harddisk is actually busy loading the system. 
Can anybody point out how can i correct this problem?

Edit:
I decided to search around for a possible answer and force reprofiling ureadahead does the trick
Now boot time is back to what it used to be

---

### Post by lewys93 on 2011-03-04
I have had exactly the same problem, but reprofiling ureadahead makes no difference for me
Am I right in saying that to force ureadahead to reprofile you must remove the file 'pack', located in /var/lib/ureadahead?

---

### Post by vrhahaha on 2011-03-05
I did not use the same method to reprofile. Instead i followed the guide given in the link.
[http://www.techtipsgeek.com/speed-up-boot-up-process-ubuntu-10-04-lucid-lynx/9496/]("http://www.techtipsgeek.com/speed-up-boot-up-process-ubuntu-10-04-lucid-lynx/9496/")
Another user suggested both methods produce the same effect
[http://ca.ubuntuforums.org/showpost.php?p=9723665&postcount=180]("http://ca.ubuntuforums.org/showpost.php?p=9723665&postcount=180")

Be aware though that I did this when i was still using ubuntu 10.04. I am not sure if it would work for you.

---

### Post by lewys93 on 2011-03-05
> **vrhahaha said:**
> I did not use the same method to reprofile. Instead i followed the guide given in the link.
[http://www.techtipsgeek.com/speed-up-boot-up-process-ubuntu-10-04-lucid-lynx/9496/]("http://www.techtipsgeek.com/speed-up-boot-up-process-ubuntu-10-04-lucid-lynx/9496/")
Another user suggested both methods produce the same effect
[http://ca.ubuntuforums.org/showpost.php?p=9723665&postcount=180]("http://ca.ubuntuforums.org/showpost.php?p=9723665&postcount=180")

Be aware though that I did this when i was still using ubuntu 10.04. I am not sure if it would work for you.

Thanks for your reply - I've managed to get it working now, I just had to restart my computer a few times after reprofiling.

Thanks again, Lewys

---

