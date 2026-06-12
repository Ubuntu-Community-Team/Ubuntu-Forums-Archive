---
title: "Boot-repair question"
date: 2012-03-28
forum: General Help
---

### Post by mohanradhakrishnan on 2012-03-28
I started boot-repair and after about 20 minutes of scanning it showed a dialog and prompted me to download a newer version. I choose Yes and asked me to connect to the internet. 
 
My net connection is through a CNTLM proxy and .bashrc is updated. wget works through this proxy. Even my network settings is updated to use this proxy.
 
After some more scanning it showed the repair dialog. I clicked 'Recommended repair' and nothing happened after that. No progress bar.
 
Can I assume that it has repaired and reboot my system ? Is there another way to check that the grub files that I mistakenly removed have been reinstalled.
 
Appreciate your advice.
 
Thanks.

---

### Post by garvinrick4 on 2012-03-28
Using a Live Cd (install Cd using Try Ubuntu) with internet working open a terminal and copy and paste below. (boot_info_script from SourceForge.net and first line of code I found from oldfred I believe.)

                                  ```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
```  ```
chmod +x bootinfoscript
``````
sudo ./bootinfoscript
```Will now have a RESULTS file in Home folder. Post here and will be read for you, if you need it.

You do not say if you are booting or not but lots of simple ways to fix grub.

---

### Post by mohanradhakrishnan on 2012-03-28
Hi,
 
I haven't still rebooted after I messed up.
 
I have attached the result of the script you mentioned.
 
Meanwhile the boot-repair utility after several hours is now trying to generate a boot info. summary. A few times it popped up a message about lack of a net connection.
 
** Update : Summary from boot-repair**
 
boot-repair completed after several hours reporting no changes have been made to the system.
 
 
 
 
 
Thanks,
Mohan

---

### Post by garvinrick4 on 2012-03-28
#Your boot is in sda and pointing towards sda5 your linux install for grub files where they are so no problem there at all looks good.

#Try to boot into system.

#If for any reason does not boot. (should boot into UBuntu see no problems with Ubuntu and grub)

#Put the live cd back in and boot of off it and open a terminal:
```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --recheck --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```Also try to boot into XP if problem exist there. Need xp disk to fix or can use "lilo" app in Linux off of live cd.
Get back on if all boots ok or one does and one does not. 

Hopefully all will boot well as it exists now. Boot Script looks good for Ubuntu.
One way or the other can be fixed in a jiffy with a couple of lines of code if boot problem with Windows.
If all booting fine just marked solved.

---

