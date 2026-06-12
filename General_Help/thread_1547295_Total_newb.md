---
title: "Total newb"
date: 2010-08-06
forum: General Help
---

### Post by dieseltwitch on 2010-08-06
Hello All,

To say I am new to ubuntu and linux as a whole is a huge understatement. I've wanted to learn for some time just never made the choice to do it. To that end I believe that the best way to learn is through persistent head bashing on desk while trying to solve problems I run across. 

Today I downloaded and installed Ubuntu 10.4, Im running Ubuntu in a parallels VM under macosx. i have managed to do a few thing by watching tutorials and examples found on youtube. however. there is a lot left to learn (never ending in fact).

My current problem is this. Im trying to install the parallel tools into Ubuntu so that I dont have to keep hitting Ctl+Option to move from my VM to the OSX. I have mounted the cd. gone into the install process and stated the install..... however during the install It stops at an error

The logs final lines are:

/etc/modprobe.conf is missing
Start installtion of user space modules
X server: xorg, V1.7.6
Install X modules from directory: .1.7
System X modules are places in /use/lib/xorg/modules
Error: there is not X modules for this version of X server
Error: faild to install user space application and drivers
2010-08-06T11:46:47-0600: execCmd: ./install --install [165]
2010-08-06T11:46:47-0600: Error: an error occurred when installing Parallels Tools. Please go to log for more info

What is the problem and how do i fix it?

---

### Post by Ocxic on 2010-08-06
"/etc/modprobe.conf" does not exist in Ubuntu 10.04.

parallels tools seems to make that an issue. 
You might want to try the parallels forum, OR you could try using VirtualBox, it's free, and works with 10.04, I use it myself.

---

### Post by dieseltwitch on 2010-08-06
Thanks, Its a good alt to parallels. however, how do i get it to let me get a res better then 800x600?

And my network connection seams to be very slow through VBox. only getting about 50kB/s

---

### Post by Ocxic on 2010-08-06
After installing the guest additions, just drag the window bigger like you would any application, or use the normal resolution switcher in Ubuntu(if available).

---

