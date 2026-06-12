---
title: "desktop effects do not enable"
date: 2010-07-24
forum: General Help
---

### Post by narnia_fan12 on 2010-07-24
I know this is a very common question, and I've found a bunch of websites on it- but none have worked. I click 'Enable' on the dekstop effects. Usually, nothing will pop up at all. Sometimes, the 'Keep Settings' thing will turn on, upon seeing I click it to keep the new settings. I turn the appearance page back on, and it says there are no effects enabled. I want to enable normal effects. 

I had an old version of Ubuntu for almost half a year before updating to Lucid Lynx. I recently wiped the new version of ubuntu accidentally (lucid lynx) while playing around with it, but before I wiped it I had graphics driver and effects enabled no problem. Emerald and transparency worked, etc. I did the exact same steps this time that I did on my last install of Ubuntu- and now it won't work. Any help??? 

p.s. I have compiz installed but it won't enable effects either. My graphics card is a Nvidia GE Force MX, i think.

---

### Post by linux18 on 2010-07-24
just checking:
```
 sudo apt-get install nvidia-current 
```then reboot:

-choose recovery mode at grub
-drop to a root prompt
-type telinit 3 and login
-type sudo nvidia-xconfig
-then type xinit
-when xinit starts type: metacity & - for ubuntu OR flux/openbox & - if you have it OR fvwm & - for xubuntu
-then type gnome panel & -for ubuntu OR xfce4-panel & -for xubuntu
-nm-applet & -for networking
-sudo apt-get install compiz compizconfig-settings-manager
-compiz --replace
-ccsm

this will solve 99% of compiz/nvidia problems

---

### Post by narnia_fan12 on 2010-07-24
Nvidia-current package was not found... Couldn't find it in Synaptic, either.

---

### Post by dragos240 on 2010-07-24
Try sudo apt-get update

then do sudo apt-get install nvidia-current

---

### Post by narnia_fan12 on 2010-07-24
geek@geek-desktop:~$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-current


EDIT: I checked synaptic again and it has nvidia-current-modaliases installed. Is that the same thing?

---

### Post by dragos240 on 2010-07-24
> **narnia_fan12 said:**
> geek@geek-desktop:~$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-current


EDIT: I checked synaptic again and it has nvidia-current-modaliases installed. Is that the same thing?

Do what I told you. sudo apt-get update, and then apt-get install nvidia-current

---

### Post by narnia_fan12 on 2010-07-24
That's what I did, I updated then I ran sudo apt-get install nvidia-current. It updated fine, but the nvidia file isn't found.

---

### Post by dragos240 on 2010-07-24
> **narnia_fan12 said:**
> That's what I did, I updated then I ran sudo apt-get install nvidia-current. It updated fine, but the nvidia file isn't found.

Oh, okay. Could you open up software sources (system>administration>software sources) and tell me what you have enabled?

---

### Post by narnia_fan12 on 2010-07-24
currently, I have only canonical and community supported open source software checked, I forgot that I unchecked some of those when I had problems installing from the command line. Should I check the other boxes?

EDIT: I checked the boxes, ran the update, sudo apt-get install nvidia-current, and its installing now.


-drop to a root prompt

how do I drop to a root prompt?

---

### Post by narnia_fan12 on 2010-07-24
How do I access Recovery Mode?

---

### Post by howefield on 2010-07-24
> **narnia_fan12 said:**
> How do I access Recovery Mode?

Should be one of the options in the grub boot menu.

If you don't see a grub menu when you boot the computer, press the Shift key after the BIOS boots but before grub starts, this should bring up a menu of various kernels which you could boot into, select the latest one (highest number) that also has recovery in the line.

There is only a short window of time so you have to be quick to catch grub, before it goes to the splash screen.

---

### Post by FresnoFightFan on 2010-07-24
maybe your board became unstable and is giving your video drivers problens. flash bios?

---

### Post by d3v1150m471c on 2010-07-24
have you tried alt+f2 and issuing out:
```

emerald --replace
# or
compiz --replace

```

I had the same trouble until I opened my appearance preferences and turned on my visual effects to a higher mode.

---

### Post by d3v1150m471c on 2010-07-24
> **FresnoFightFan said:**
> maybe your board became unstable and is giving your video drivers problens. flash bios?

it doesn't sound like a hardware issue IMO

---

### Post by narnia_fan12 on 2010-07-25
shift doesn't work on boot. BIOS never shows up, all it is is the manufacturer logo followed by a flashing -, then the Ubuntu logo. Pressing shift doesn't give a boot menu or anything. Never any options. Compiz --replace doesn't do anything. 

...and appearance still doesn't let me check effects as normal or extra. >.< :evil:

---

### Post by narnia_fan12 on 2010-07-25
I still can't find out how to get into recovery mode, even after reading up on a bunch of posts on here... help... >.>

---

### Post by narnia_fan12 on 2010-07-25
Ok. I'm trying to reinstall my Nvidia driver. Since Envy doesn't work anymore (>.<) I downloaded it from Nvidia's website for linux. I need to ctrl+alt+f2. Then, after logging in, I need to kill the Xorg. sudo killall Xorg doesn't work- it only brings me back to the login screen. It was working the first time I did it- but since then, it hasn't worked. What am I doing wrong???

---

### Post by linux18 on 2010-07-25
thats why I drop to a root prompt, it's faster, you probably set your grub timeout to 0 so you cant see the menu ( you must have like 20 kernels in grub by now ) I believe one of these will work:
just ctrl+alt+f2 and type

```

sudo /etc/init.d/gdm stop
sudo killall xinit
sudo killall xterm
```
 
after you login then 

sudo nvidia-xconfig

---

### Post by collinp on 2010-07-25
To kill Xorg, you have to stop the GDM process. Execute the following command,
```
sudo /etc/init.d/gdm stop
```

---

### Post by narnia_fan12 on 2010-07-25
I was able to install the driver. But now its saying that Desktop Effects could not be enabled. 

More and more... I'm getting tired of this :/ maybe a fresh install of ubuntu would work...

---

### Post by dragos240 on 2010-07-28
> **narnia_fan12 said:**
> I was able to install the driver. But now its saying that Desktop Effects could not be enabled. 

More and more... I'm getting tired of this :/ maybe a fresh install of ubuntu would work...

If you want to start fresh, remember to enable all repos right off the bat. Also, you can get a list of all the programs you are using doing this:

```
dpkg --get-selections > listofprograms.bak
```

Get that file onto a flash drive or something, and when you install ubuntu again, copy it into your home folder. Then do this:

```
sudo apt-get install dselect && sudo dpkg --get-selections < listofprograms.bak && sudo dselect
```

Then press "i" to install the packages. Now you have all the packages you did before.

---

