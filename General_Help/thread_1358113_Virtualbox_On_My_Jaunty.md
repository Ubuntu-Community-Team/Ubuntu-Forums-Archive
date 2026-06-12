---
title: "Virtualbox On My Jaunty"
date: 2009-12-18
forum: General Help
---

### Post by ubunfreak on 2009-12-18
Ubuntu 9.04 jaunty

hello, can i have some help with installing virtualbox using a terminal :)  
if i could have the commands to paste in terminal that would be so great.
also do i have to enable some repo or something even if i have all the updates for ubuntu?

---

### Post by wangsuda on 2009-12-18
> **ubunfreak said:**
> Ubuntu 9.04 jaunty

hello, can i have some help with installing virtualbox using a terminal :)  
if i could have the commands to paste in terminal that would be so great.
also do i have to enable some repo or something even if i have all the updates for ubuntu?
There is no reason to do anything from the terminal. Simply go to [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and select your version of Ubuntu. the .deb package will download and install. It's that simple.

EDIT: There is also code provided at that website, if you still want to use terminal commands.

---

### Post by ubunfreak on 2009-12-18
> **wangsuda said:**
> There is no reason to do anything from the terminal. Simply go to [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and select your version of Ubuntu. the .deb package will download and install. It's that simple.

EDIT: There is also code provided at that website, if you still want to use terminal commands.
  Thank you for helping me :) i went to the site and selected jaunty and installed it by clicking open with instead of saving it. now it"s installed but where is it? how do i start it?

---

### Post by ubunfreak on 2009-12-18
I looked through everything and i can"t find any icon to start launch the program :confused:

---

### Post by wangsuda on 2009-12-18
> **ubunfreak said:**
> I looked through everything and i can"t find any icon to start launch the program :confused:

Reboot your computer, and then go to Applications>System Tools>Sun VirtualBox.

---

### Post by ubunfreak on 2009-12-18
> **wangsuda said:**
> Reboot your computer, and then go to Applications>System Tools>Sun VirtualBox.

Thank you

---

### Post by ubunfreak on 2009-12-18
I have a question regarding full screen using virtualbox, i can"t get the screen to be completely full like when im on ubuntu. i"ll show a pic of the fullest i can get it to go.

---

### Post by ajaay on 2009-12-18
> **ubunfreak said:**
> I have a question regarding full screen using virtualbox, i can"t get the screen to be completely full like when im on ubuntu. i"ll show a pic of the fullest i can get it to go.
 
have u tried the virtual box additions??:confused:
it is given by virtual box itself for the guest os..
In menu, click **install virtual box additions** when in the guest os..
a setup will start and after a restart go to full screen...:)

---

### Post by bkmfs on 2009-12-18
Go to:

[http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)

and download the 'VBoxGuestAdditions' iso in one of those folders with the Virtual Box version number that you are currently using.  You will have to mount it as a cd/dvd iso file in your virtual machine settings.  There a a couple of different versions of the same program within the iso so choose wisely.  Some are for Linux guests and there may be a couple different ones for windows guests.  (Remember that it is a .exe file since you are installing it on a windows guest).

p.s. go to bed, it's 4:35 am.

---

### Post by wangsuda on 2009-12-18
> **ubunfreak said:**
> I have a question regarding full screen using virtualbox, i can"t get the screen to be completely full like when im on ubuntu. i"ll show a pic of the fullest i can get it to go.
1. Install guest additions (Devices>Install Guest Additions [AFTER loading VirtualBox])
2. Right Ctrl and the "f" key. Do the same to shrink it.

---

### Post by ubunfreak on 2009-12-18
Thanks for helping me you guys :)  i will try that shortly after i have my first coffee :biggrin:

---

### Post by ubunfreak on 2009-12-24
> **wangsuda said:**
> 1. Install guest additions (Devices>Install Guest Additions [AFTER loading VirtualBox])
2. Right Ctrl and the "f" key. Do the same to shrink it.

I can"t seem to get it installed :confused: it just won"t install.

---

### Post by ubunfreak on 2009-12-24
After a reboot it works fine :)

---

### Post by wangsuda on 2009-12-24
> **ubunfreak said:**
> After a reboot it works fine :)Glad to read that everything is working for you.

---

