---
title: "Error when installing ATI driver"
date: 2009-11-02
forum: General Help
---

### Post by Kaneda187 on 2009-11-02
```
kaneda@facon-core:~$ cd /home/kaneda/Desktop
kaneda@facon-core:~/Desktop$ chmod +x ati.run
kaneda@facon-core:~/Desktop$ sudo ./ati.run
[sudo] password for kaneda: 
Created directory fglrx-install.lbVAbj
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593.....................................................................
..........................................................................
..........................................................................
..........................................................................
..........................................................................
..........................................................................
..........................................................................
..........................................................................
..........................................................................
..........................................................................
..........................................................................
..........................................................................
..........................................................................
..............................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-14-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.lbVAbj
kaneda@facon-core:~/Desktop$
```
I got that error message when trying to install the ati driver for my laptop...
anybody know what the deal is with it?

---

### Post by Kaneda187 on 2009-11-03
Can anybody shed some light on this ive been searching the net but cant find anything about that relates to the karmic release of ubuntu just older versions.

---

### Post by togo59 on 2009-11-03
The latest driver for 9.10 is 8.661

Identify your graphics card:```
lspci | grep VGA
``` and head over to [ [COLOR="Blue"]_the AMD site_[/COLOR] ]("http://www.amd.com/uk/Pages/AMDHomePage.aspx") and choose the latest driver.

Read the release notes and the installation instructions. However, I have no idea whether this will solve your problem.

On my laptop, if I install the "Tested by Ubuntu Developers" ATI/AMD proprietary FGLRX graphics driver, I get the dreaded black screen of death on reboot.

Hence I am, very cautiously, doing some background reading on installing the latest driver from the above site.

If you wait a day or two I may be able to give you some more definitive advice.

P.S. Read [[COLOR="RoyalBlue"]_this thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1238129")

---

### Post by Kaneda187 on 2009-11-03
I got the driver from the ati site but it turns out its only supported by the older versions of the kernel like the one in 9.04 so sadly looks like I'm going back.
unless thers away to downgrade the kernel to the one that supports that driver I dont know anything about that and it could be a lot of work.
Im not impressed at all by this release its been a nightmare.
I just hope that lucid lynx is an improvement it has to be more stable since its and LTS release.

---

### Post by togo59 on 2009-11-03
> **Kaneda187 said:**
> 
Im not impressed at all by this release its been a nightmare.
I just hope that lucid lynx is an improvement it has to be more stable since its and LTS release.

I agree with you, I haven't had this amount of grief since the wireless woes of 7.10. And come to think of it 8.10 seemed to screw up the sound with major pulse audio issues. Maybe there's a pattern...       

However, some people claim to have installed Catalyst 9.10 and got their ATI Radeon hardware to work under Karmic.

I'll post back again if I can get my 3400 card to work properly under Karmic.

---

### Post by Kaneda187 on 2009-11-05
just thought id ask if anybody had any luck with this or knows a workaround i dont wanna uninstall karmic but i would really like my graphics card to work.......

---

### Post by Kaneda187 on 2009-11-07
bump

---

### Post by espmartin on 2009-11-10
bump bump

---

### Post by espmartin on 2009-11-14
No latest news?

---

### Post by Zoot7 on 2009-11-14
What ATi card have you?

The best way to install the ATi drivers is via a package based install using the Catalyst Installer.

To do that:
```
cd ~
mkdir ati_driver && cd !$
wget http://www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run
sh ati-driver-installer-9-10-x86.x86_64.run --buildpkg Ubuntu/karmic
sudo dpkg -i *.deb
```

Then set up xorg.conf
```
gksu gedit xorg.conf
```
Go down to the following section:
```
Section "Device"
	Identifier	"SOME IDENTIFIER"
	**Driver		"fglrx"**
EndSection
```
And add the line in bold above to the file between the Section and EndSection, save and close.

Then run this to generate a proper ATi xorg.conf file
```
sudo aticonfig --initial -f
```

Run this to force the ATi driver to use xorg.conf (some people believe it's better to do this aswell)
```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
``` 

Lastly reboot and run:
```
fglrxinfo
```

If it shows your card then you're away, here's what I get:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.8673
```

This way I find is a much more efficient way than running the script directly, plus you get a much more stable install.

---

### Post by espmartin on 2009-11-14
Trying now. Thanks !

---

### Post by Zoot7 on 2009-11-14
I do remember getting the error message to the effect "errors processing some package or what not". But I haven't had any issues with the fglrx driver in Karmic with my HD4870 for either games or compiz effects yet.

---

### Post by espmartin on 2009-11-14
It was working great, until I get to this point:

> Then run this to generate a proper ATi xorg.conf file
     Code:
     sudo ati-config --initial -f 
I get: > sudo: ati-config: command not found

Any thoughts?

---

### Post by Zoot7 on 2009-11-14
> **espmartin said:**
> Any thoughts?
My apologies, it should be:
```
sudo aticonfig --initial -f 
```

Sorry about that! :)

---

### Post by espmartin on 2009-11-14
Ah. Thanks ;) But now I get this:
> martin@martin-desktop:~/ati_driver$ sudo aticonfig --initial -f
Unable to open /etc/ati/control, please reinstall the driver.
aticonfig: No supported adapters detected


---

### Post by espmartin on 2009-11-14
The system shows my card correctly as:
> Graphics chip:         ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]


---

### Post by Zoot7 on 2009-11-14
What ATi card have you?

```
lspci | grep VGA
```

There was a lot of them that support was dropped for recently.

---

### Post by espmartin on 2009-11-14
> martin@martin-desktop:~/ati_driver$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]

Thanks Zoot for taking time with this!!!!

---

### Post by Zoot7 on 2009-11-14
Ah! there's your problem. Catalyst 9.10 doesn't support the Radeon X1300/X1550 Series.

Try out the 9.3 driver:
[https://www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run](https://www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run)

The only thing is now you won't be able to build packages for Karmic on account of that driver not being around near Karmic's release.
Instead of building packages try running the script directly, and then set up xorg in the same way.
```
chmod +x ati-driver-installer-9-3-x86.x86_64.run
sudo ./ati-driver-installer-9-3-x86.x86_64.run
```

I'm not sure how you'll get on with this - in my experience running the script directly normally doesn't work. :(
Give it a shot none the less.

---

### Post by espmartin on 2009-11-14
Ah - no dice. I get the dreaded error:
> Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-15-generic-pae; make sure that the version is being
correctly set by --iscurrentdistro


---

### Post by Zoot7 on 2009-11-14
Actually wait. 9.3 is incompatible with the version of X that's in Jaunty, so I'm guessing it's the same in Karmic.

For that you're going to have to downgrade X to an earlier version. Check out the guide here:
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

It's for Jaunty but I'm guessing it'll work in Karmic too. 
I know it's a lot of hoops to jump through :( but this is a classic example of the ATi troubles under Linux - nVidia is always the better option.

I've no idea whether that'll work or not TBH. My 4870 thankfully is well supported at this time.

---

### Post by espmartin on 2009-11-14
Thanks so much so far!

---

### Post by Zoot7 on 2009-11-14
No worries. :) Hopefully we can get you set up someway. :)

---

### Post by mrhippieguy on 2009-11-26
i just sort o' stumbled across this thread, because it's the closest thing to the trouble i'm having.

so i know that 9.3 driver installer doesn't work with 9, so i'm still using 8.04.. now my trouble (and this is really f**ked up)is that, well, i'm a 3d graphic designer. i need my video card to be working, and i work on a budget of $0.00(got my computer, ram, graphics card, monitor, and 3d development software for free).

what happens is i start it up, then it works fer a few times. then, suddenly, i start it up, and right after the loading screen, i see some console lines that say something about an 'anac(h)ronistic anacron' or somthing. then, funky random green 'n' black colorbars, then dialog box.('Ubuntu is running in low-graphics mode') and i can't use glsl, can't even set my screen res higher than 800x600. the only fix that works is reinstalling ubuntu, but that ony works for a short time, and after twenty times this week, it's getting stupid.

help is appreciated, and very much needed.

---

### Post by mrhippieguy on 2009-11-26
bump?

---

### Post by Zoot7 on 2009-11-26
Have you tried the package based install i posted earlier in this thread?

I find this the best way to install the driver, running the script directly seems almost to never work.

---

### Post by mrhippieguy on 2009-11-26
yes! it worked!
```
mrhippieguy@mrhippieguy:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.1.8543 Release

mrhippieguy@mrhippieguy:~$ echo yay!!!
yay!!!

```
THANK YOU!!!1!!111
seriously, this is the seventh time this week my computer has done that.

---

### Post by Zoot7 on 2009-11-27
Glad to hear you're sorted! :)

---

### Post by Caathrok on 2009-12-02
There is not a xorg.conf file in 9.10

---

### Post by Zoot7 on 2009-12-03
> **Caathrok said:**
> There is not a xorg.conf file in 9.10
By default no, but one will be generated if you setup either the Nvidia driver or the fglrx driver.

---

