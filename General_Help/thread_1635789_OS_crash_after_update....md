---
title: "OS crash after update..."
date: 2010-12-02
forum: General Help
---

### Post by orky7 on 2010-12-02
so this is what happen i was updating the system and electricity went out so i cancel the download and close the update manager..when electricity is back i re-select some of the packages for update everything went fine and when installing the updates one error message is generated saying somthing like it is being used my other something and i click cancel and it says restart the system now or later i restart the system and after some time it says--- ubuntu running in low graphics, nvidia kernel fail to load and there is this OK button but nothing work neither the touchpad nor the keyboard i cannot click ok and continue using ubuntu in low graphic mode also.
i tried recovery mode lots od thing happen but it also stuck after this 
Begin: running /scripts/init-bottom
Done
and then it get stuck....
one more thing in the update package there are 2 x-server packages...

---

### Post by orky7 on 2010-12-02
any one?? at least tell me how to put the back up configuration...

---

### Post by searchfgold6789 on 2010-12-02
I had some trouble understanding most of your post, but I think I still may be able to help you.
What I can glean from your post is that:

[LIST]
[*]You tried to upgrade using the Update Manager. The package manager began the download.
[*]The electricity went out and when it came back the upgrade continued without apparent problem.
[*]You get an error message. It does not seem as if you recorded the contents of it. Do you think it might have been something like "Unable to get exclusive lock"?
[*]Then the upgrade completed and you restarted the computer as suggested by a window or other message.
[*]The nVidia driver now crashes whenever you attempt to start the computer and get to the login screen.
[/LIST]
So. If this accurately describes what happened, then maybe you can purge and reinstall your nVidia drivers, as well as xorg.
This can be done from the Live CD! (assuming you are using a complete install of Ubuntu)

[LIST=1]
[*]Boot from the LiveCD.
[*]Open up a terminal.
[*]Type in this, replacing /dev/sdXX with your main system partition:```
sudo mount /dev/sdXX /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
```
[*]Then use the terminal to purge and reinstall xorg and the nVidia drivers, in that order. (I don't know what the package name of the drivers that you are using is, so please replace "nvidia-drivers" with the package name.)```
sudo apt-get purge xorg nvidia-drivers; sudo apt-get install xorg nvidia-drivers
```
[/LIST]

---

### Post by orky7 on 2010-12-03
@ searchfgold6789 you r right. when electricity went out i close the update manager and when electricity come back i again fire up the update manager and do the rest of it. 
yes i think it says "unable to get exclusive locks" in one of the package installation.
 i have 9.04 still installed in other partion so can i do something via 9.04 and i tried recovery option also it also did not work(it also get hanged not even TTY works)..how to find the package name of "nvidia-drivers"

---

### Post by orky7 on 2010-12-05
sda3 is where corrupt os resides..

---

### Post by garvinrick4 on 2010-12-05
#I do not know what drivers you are using? After reading your original post the post3 instructions can get you into your / with the chroot command but in replacing drivers only you know what you are using. Are you using same driver in other partition of Ubuntu?
First line of code given in post3 whould be:
```
sudo mount /dev/sda3 /mnt
``````
#In list of commands you have in post 3, before the chroot command add for internet connection:
[CODE]sudo cp etc/resolve.conf /mnt/etc/resolv.conf
```#After chroot command to resolve dependencies if any from stopping upgrades
#Anything after chroot do not use sudo:
```
dpkg --configure -a
``````
apt-get update && apt-get upgrade
```#You have to install your own nvidia-drivers
```
exit
```
```
sudo umount /mnt/dev/pts
``````
sudo umount /mnt/dev
``````
sudo umount /mnt/proc
``````
sudo umount /mnt/sys
``````
sudo umount /mnt
```[/code]#This has as good a chance of any as working if your install just stopped upgrade in middle.
#This is not in theory it has worked for me when upgrade stopped in middle more than once.

---

### Post by orky7 on 2010-12-15
thank you  
@ garvinrick4
and
@ searchfgold6789

it worked but i made a mistake while running the live OS i was using 32bit on my 64bit so chroot does not work.... now every thing is normal..

---

