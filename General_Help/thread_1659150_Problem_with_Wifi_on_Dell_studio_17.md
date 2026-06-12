---
title: "Problem with Wifi on Dell studio 17"
date: 2011-01-03
forum: General Help
---

### Post by TheRageXIII on 2011-01-03
Dear readers,

I hope you guys can help me with the following problem.
After a problem with a wireless Windows driver, Ubuntu is having a problem with my wireless network card.

***Time for some explaining***
After installing Ubuntu 10.10 as dual-boot next to Win7 64-bit, the first thing that happened was a problem with Wifi. There was no driver installed and with little knowledge of Ubuntu I used the additional drivers window to install the Broadcom STA driver.

Being used to high speed internet connections, I was rather disappointed that the speed of the STA driver was really slow(a least, that's my experience).
To try something else I used NDISwrapper to install a Windows Wireless driver. This solution worked perfect for exactly one night. After a reboot of the laptop, the wireless connection didn't start anymore. Even reinstalling didn't work. While I tried to reinstall the STA driver, I noticed from the console that ifconfig and iwconfig didn't show any wireless device. Even using an ethernet-cable to install the STA driver, the wifi card doesn't seem to be on my side.

So tell me, what am I forgetting here?

---

### Post by mikewhatever on 2011-01-03
Make sure you completely remove ndiswrapper because the two drivers may be conflicting.

---

### Post by TheRageXIII on 2011-01-04
> **mikewhatever said:**
> Make sure you completely remove ndiswrapper because the two drivers may be conflicting.
 
Never thought of that. I'll give it a shot.
I'll post the results here when I uninstalled NDISwrapper and  retried to install the STA driver

---

### Post by TheRageXIII on 2011-01-04
I'm glad to announce that the problem seem to be solved. Wireless connection is working again. Only thing that stays unanwsered is why NDISwrapper stopped working in the first place.
 
Thank you for the quick response

---

### Post by TheRageXIII on 2011-01-06
Hey i'm back again. Problem was solved but after a reboot of the laptop, the wireless connection again isn't working and disappeared from the ifconfig screen. This time instead of the Windows driver, the Broadcom STA driver is installed.

Any suggestions?

---

### Post by bkratz on 2011-01-06
In the terminal try

gksudo gedit /etc/modules

and see if all that is there is just lp.  If so, add a line with just wl below the other one. Gksudo would require your password which would not be seen on the screen at all, not even ****. Just put the password in and press return(enter). It would look like this

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
wl


Just save and reboot when done

---

### Post by TheRageXIII on 2011-01-06
> **bkratz said:**
> In the terminal try

gksudo gedit /etc/modules

and see if all that is there is just lp.  If so, add a line with just wl below the other one. Gksudo would require your password which would not be seen on the screen at all, not even ****. Just put the password in and press return(enter). It would look like this

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
wl


Just save and reboot when done

Well it seems to work for now. I hope it keeps working this time.
Thank you for your help

---

