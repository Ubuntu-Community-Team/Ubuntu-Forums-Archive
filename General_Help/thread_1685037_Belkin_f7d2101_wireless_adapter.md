---
title: "Belkin f7d2101 wireless adapter"
date: 2011-02-10
forum: General Help
---

### Post by AutoSelect on 2011-02-10
friend installed on my computer so please bear with me on some very dumb questions i am sure.  

trying to get this to work so i can get internet going.  i found this thread [http://ubuntuforums.org/showthread.php?t=1515747](http://ubuntuforums.org/showthread.php?t=1515747) which seems to answer my question. i could figure everything out except how would i go about downloading that file and transferring it to the other hard drive partition which can't connect to internet yet?  also the last step is copy to directory which i also have no idea where that is?  thanks and sorry if this is painfully obvious

---

### Post by anglican on 2011-02-10
> **AutoSelect said:**
> friend installed on my computer so please bear with me on some very dumb questions i am sure.  

trying to get this to work so i can get internet going.  i found this thread [http://ubuntuforums.org/showthread.php?t=1515747](http://ubuntuforums.org/showthread.php?t=1515747) which seems to answer my question. i could figure everything out except how would i go about downloading that file and transferring it to the other hard drive partition which can't connect to internet yet?  also the last step is copy to directory which i also have no idea where that is?  thanks and sorry if this is painfully obviousYou will need to create that directory (as in post #3 in the link above) using:
```
sudo mkdir /lib/firmware/RTL8192SU
```then copy the file into that directory. You will have to download the firmware file on another computer that does have internet working and then transfer it using some sort of removable media e.g. a usb stick.

H

---

### Post by AutoSelect on 2011-02-10
Ahh k didn't realize I had to make that also.  I'll give that a try thank you.

---

### Post by AutoSelect on 2011-02-11
Ok tried using the command in reply 3 and it says /lib/firmware/rrl8192su is a directory but how do I get that directory open to copy that download into?  I tried the sudo gedit then the /lib/firmware/RTL8192SU but it won't open the directory?

---

### Post by anglican on 2011-02-11
> **AutoSelect said:**
> Ok tried using the command in reply 3 and it says /lib/firmware/rrl8192su is a directory but how do I get that directory open to copy that download into?  I tried the sudo gedit then the /lib/firmware/RTL8192SU but it won't open the directory?Note that upper/lower case **really** matters in linux (you're not using DOS now!). Make sure you are completely consistent (you have used both above - and there's a typo with rrl8192su instead of rtl8192su) and careful in what you type. > More haste, less speed! The command to copy the firmware into the directory is:
```
sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU
```

H

---

