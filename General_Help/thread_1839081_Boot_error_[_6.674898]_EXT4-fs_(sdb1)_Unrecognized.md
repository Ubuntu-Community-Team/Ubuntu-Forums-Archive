---
title: "Boot error: [ 6.674898] EXT4-fs (sdb1): Unrecognized mount option &quot;d=remount-ro&quot;"
date: 2011-09-04
forum: General Help
---

### Post by Alphax45 on 2011-09-04
Hi All  Been dual booting with Windows 7 and Kubuntu (11.04) for more than a week now and I have been spending more time in Linux land than Windows as of later. Very liberating.  

Anyways, today I go to boot up - I get the grub menu, choose my Linux option and on the Ubuntu boot screen (with the dots) I get this error:     

Boot error: [ 6.674898] EXT4-fs (sdb1): Unrecognized mount option &quot;d=remount-ro&quot; or missing value 

I did Google it and found nothing. Any thoughts/suggestions?    

I am able to boot into Windows 7 just fine.   

K

---

### Post by plucky on 2011-09-05
> Boot error: [ 6.674898] EXT4-fs (sdb1): Unrecognized mount option &quot;d=remount-ro&quot; or missing value 

Have you changed the /etc/fstab file?

The mount option for the / partition should be "errors=remount-ro".

You can boot into the "recovery mode" and edit the /etc/fstab file and fix the mount option.

Good Luck

---

### Post by Alphax45 on 2011-09-06
[COLOR=black][FONT=Verdana]Hi All[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I installed kubuntu on the second HDD in my laptop[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have NOT edited the file (at least on purpose) but will try the recovery mode and making the suggested change. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]
Thank you[/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

