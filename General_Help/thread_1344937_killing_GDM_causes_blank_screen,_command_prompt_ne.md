---
title: "killing GDM causes blank screen, command prompt never appears"
date: 2009-12-03
forum: General Help
---

### Post by eival on 2009-12-03
i remember having this issue before an i found a fix on the internet but i forgot to bookmark it, an now here i am on a new fresh install of Ubuntu 8.04 an im trying to update my NVIDIA drivers manually but everytime i kill the GDM with either ```
sudo /ect/init.d/gdm stop  or ctrl+alt+f1
``` i just get a blank screen, instead of the command prompt,  i can still type commands tho cause ```
sudo init 2
``` will restart the GDM.

if i remember i believe the fix was something that had to be done to one of the system files, either adding or changing some words.

hopefully someone knows cause the top returns on google are of no help, including a launchpad link that addresses a blank screen issue but its not related.

---

### Post by eival on 2009-12-05
nobody knows what im talking about?

id like to get this solved so i can install the driver an move on with my life.

feel free to move the thread to somewhere else if it'll get the attentioned needed.

for those that arent understanding my issue this is what im trying to do

[http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787)

once i get to 
```
sudo /etc/init.d/gdm stop
```
the command line never shows, the screen just flickers and i have to blindly type
```
sudo init 1
```
then my root password for my desktop to reload.

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
[http://www.linuxquestions.org/questions/linux-general-1/ctrl-alt-f1-blackblank-screen-385376/](http://www.linuxquestions.org/questions/linux-general-1/ctrl-alt-f1-blackblank-screen-385376/)

---

### Post by eival on 2009-12-08
> **Sin@Sin-Sacrifice said:**
> [http://www.linuxquestions.org/questions/linux-general-1/ctrl-alt-f1-blackblank-screen-385376/](http://www.linuxquestions.org/questions/linux-general-1/ctrl-alt-f1-blackblank-screen-385376/)

thanks, but i cant save the changes i make to the Grub menu cause it says i dont have the privleges.

other than logging in as root, is there a SUDO command i can enter in the terminal to open the boot/grub/menu.lst with root privileges?

---

### Post by eival on 2009-12-08
nevermind i found it

```
sudo gedit /boot/grub/menu.lst
```

apparently like that link says, its the actual NVIDIA driver that causes this issue.

once i disabled them an restarted, i was able to switch to the command line and install the newer driver with no issues.

---

