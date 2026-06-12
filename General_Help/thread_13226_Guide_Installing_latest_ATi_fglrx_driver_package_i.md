---
title: "Guide: Installing latest ATi fglrx driver package in Warty"
date: 2005-01-29
forum: General Help
---

### Post by Scottles on 2005-01-29
Ok, seeing as some of you seem to be having problems installing the drivers I am gonna post a step by step on how to get them working (or at least it works for me!). Before doing any of these steps, ensure you have the kernel headers and gcc installed. You will also need to have enabled your root account, and be reasonably confident with the command line. Oh yeah.. you will also need to have downloaded the latest fglrx drivers from ATi's site too! :)

If you don't know what your doing and you mess this up, you may be stuck with X11 not working.. so only do this if you are confident you can fix things if something goes wrong! Now on to the guide:

Note: I have made a few small ammendments to the guide which may be helpful if you are having trouble updating to the new 8.10.19 fglrx driver, from a previous ATi driver release.

1) First thing you will want to do is make sure you remove the warty fglrx drivers using synaptic or apt-get (if you never installed them skip this step).

$sudo apt-get remove fglrx-driver


2) Switch to another terminal (press CTRL+ ALT + F1) and login as root (you will need to have enabled your root account to do this). Stop X Windows using the following command:

#/etc/init.d/gdm stop


3) Find any existing "fglrx.ko" files and delete/backup. The "find" command will help you to find them. The example below stores the results in a text file called "files.txt". You can load the "files.txt" file using nano.

#find / -name fglrx.ko > files.txt


4) Convert the ATi fglrx driver .rpm file to a .deb package using alien. Switch to the directory with the driver package in first then use alien:

#alien <driver package name>

5) Install the driver package:

dpkg --force-overwrite -i <driver package name>.deb

NOTE: If you are updating from a previous ATi driver release please ensure drivers have been uninstalled using Apt-get/synaptic first and that the /lib/modules/fglrx directory has been deleted (along with any fglrx.ko files as in step 3)!


6) Build the kernel module:

#rmmod fglrx
#cd /lib/modules/fglrx/build_mod
#sh make.sh
#cd /lib/modules/fglrx
#sh make_install.sh
#mkdir /lib/modules/<kernel version>/misc
#cp fglrx.ko /lib/modules/<kernel version>/misc/
#depmod -ae
#fglrxconfig
#modprobe fglrx

NOTE: If any of you are having problems building the kernel module check aToasters comment on how to get around this issue (thanks aToaster!):
[http://ubuntuforums.org/showpost.php?p=61959&postcount=12](http://ubuntuforums.org/showpost.php?p=61959&postcount=12)

Also if you get an error with the "#rmmod fglrx" command, don't worry.. it just means you havent already got fglrx installed/running.


7) Restart X Windows and pray it works ;)

#/etc/init.d/gdm start

8) Once logged back in with X Windows running, check the ATi drivers work with fglrxinfo. Usually by this stage everything works, and normally you dont have to restart your computer either...

$fglrxinfo


10) Once you have verified its working, switch back to the text terminal (press CTRL+ ALT + F1), logout of the root account and then press press CTRL+ ALT + F7 to get back to your X Windows session :)

Hope people find that helpful!

---

### Post by Benny on 2005-01-30
HI!

First of all, thanks to write this guide. I tryied it. First everything went fine, but when i start to build kernel and write

**#rmmod fglrx**

I get this error..

**ERROR: Module fglrx does not exist in /proc/modules**

---

### Post by Scottles on 2005-01-30
Did the steps after it work ok? the "rmmod fglrx" command simply unloads fglrx if its currently loaded.. if its not loaded then you'll get an error message (either way its not a problem)... it just means it can't unload a module thats not loaded! :)

---

### Post by daniels on 2005-01-30
Bear in mind that this will not work on amd64, because the fglrx packages are set up for lib and lib64, rather than lib32 and lib.

---

### Post by Benny on 2005-01-30
I tryied again and start to build kernel

**#rmmod fglrx**
**#cd /lib/modules/fglrx/build_mod**
**#sh make.sh**

*** ATI module generator V2.0 ***
-----------------------------------------------------
initializing...
kernel includes at **/usr/src/linux/include not found or incomplete**
file: /usr/src/linux/include/linux/version.h

**#cd /lib/modules/fglrx**
**#sh make_install.sh**

*** WARNING ***

Tailored kernel module for fglrx not present in your system. You must go to **/lib/modules/fglrx/build_mod** subdir and execute './make.sh' to build a fully customed kernel module.
Afterwards go to** /lib/modules/fglrx/** and run './make_install.sh' in order to install the module into your kernel's module repository.

As of now you can still run your XServer in 2D, but hardware accelerated OpenGL will not work and 2D graphics will lack performance.

Failed.

 ](*,) ???

---

### Post by Scottles on 2005-01-30
did you remember to install the kernel headers for your kernel version in synaptic first? without those you can not build the fglrx kernel module!

---

### Post by Benny on 2005-01-30
I install (using synaptic) kernel-headers 2.6.8-5, but it still not work. Gives same error.

---

### Post by Scottles on 2005-01-30
Im not sure if this could be it.. but im sure I remember reading somewhere that you have to have an i686 kernel installed, as opposed to the default 386 compiled kernel.. I personally am running the k7 version of the kernel, as I have an athlon XP.. grasping at straws here.. but perhaps thats the problem? Try using synaptic to switch to the i686 kernel (or k7 kernel if you have an athlon), and also download the associated headers for that kernel..

---

### Post by JoWilly on 2005-01-30
Here is how to install fglrx without compiling, as I posted in [this](http://www.ubuntuforums.org/showthread.php?t=13342) thread:

For Hoary:

```
1. install xorg-driver-fglrx
2. install linux-restricted-modules (contains the fglrx kernel module).
3. make a backup of your /etc/X11/xorg.conf file (in case of...)
4. start fglrxconfig at the shell, and go through the config. This will generate an XFREE86CONFIG file (ati are not ready here yet...never mind)

(the mouse, keyboard, etc.. are not important here as you will not use this generated XFree file (you can use it if you tweek the keyboard drivers, etc.... but it is much easier to copy the device section to your old xorg.conf file).

5. copy Section "Device" from the generated file to your xorg.conf file, and comment the old device section out.
6. restart the X server (loging out of gnome and loging back in is not enough)

-> you are set to go.

```

For Warty it would be (have not tried it as I'm on Hoary):

1. install xfree86-driver-fglrx
2. install linux-restricted-modules (contains the fglrx kernel module).
3. start fglrxconfig at the shell, and go through the config. (check the name of the resulting file, as I have not done this on Warty -> but the default file should be ok) (but the easiest would be to just copy the "Device" Section to the old config, so you are sure that mouse, etc... is setup right)
4. restart the X server

---

### Post by Scottles on 2005-01-31
uh.. no offence.. but the whole point of this thread is because you *can't* just do that with warty.. there are no up to date ATi drivers in the repositories...

---

### Post by JoWilly on 2005-01-31
[QUOTE=Scottles]uh.. no offence.. but the whole point of this thread is because you *can't* just do that with warty.. there are no up to date ATi drivers in the repositories...[/QUOTE]

Then just activate the hoarty repositories, and install the required files (you will probably have to upgrade the kernel if linux-restricted-modules is not available in warty).

Kernel 2.6.10 is more stable than 2.6.8, so no problem here if you need to do it (and synaptic handles everything if you are scared of it).

Also, there should be no dependcy problem with these packages (kernel, linux-restricted-modules, fglrx). Only fglrx needs something (Xfree4.3), but this is already installed.

Furthermore, the great thing with this system is that you can always revert back, so you don't need to worry.

Anyway, as I said I have not done it on Warty, so if someone tries it, please report back.

---

### Post by aToaster on 2005-02-02
Alright finally figured out how to get it working!

if your getting include file errors you need to install the right kernel headers.

First check your kernel version with
$uname -a

That should tell you your kernel version, now you need the kernel headers that corresepond to that version so first try to find it in the repository and see if it's available.
$apt-cache search <your kernel number>

Now once you find it you can install the headers
$sudo apt-get install <whatever the name of the kernel header file is>

Once that's done you can go to /lib/modules/fglrx/build_mod and build the make.sh.  If it's having trouble finding your kernel headers still you need to make sure its looking in the right directory.  In warty it should be in...
/lib/modules/<kernel version>/build/include/linux

Now to edit the fglrx make.sh file so that it knows where to look...
$sudo nano /lib/modules/fglrx/build_mod/make.sh

Now somewhere a couple pages down it will say...
# specify defaults for include file locations
And there will be different locations commented out with "#", just find the kernel version that's yours and uncomment it or add your own.

Oh! and for me, I used fglrxconfig and it wouldn't let me start gdm.  So I used my old Xfree config file that "apt-get reconfigure xserver-xree86" made and I also did the whole Option "UseInternalAGPGART" "no" thing...

So hope your on your way to get it working!  If you have any questions I'll try to answer as best as possible.  I got WoW and CS:S working now.  WoW is a bit choppy, evertime I try to click on a player or npc it hangs for a sec and CS:S is somewhat decent, still not up to par with Windows though, and no voice comm support.

,aToaster

---

### Post by Scottles on 2005-02-03
Thanks aToaster, im sure those with problems building the kernel module will appreciate the tip.. i've added a note about it to the guide :)

---

### Post by mirtux on 2005-02-11
Hi,
   thanks for the guide. Just for you to know: the installation went fine but for Ubuntu to recognize the new drivers i have had to **reboot** the machine, since, after /etc/init.d/gdm start, it gave me the standards "Mesa3D" information.
 
 Thanks very much,
 MC
 
 PS: i'm experiencing some heavy glittering with Celestia 1.3.2 (either with this and the old drivers). Do you know how to fix this?

---

### Post by Scottles on 2005-02-11
off hand i dont think i can help with the glittering problem if the latest drivers didn't fix it, sorry.. my only  suggestion would be to go to

[http://apps.ati.com/linuxDfeedback/index.asp](http://apps.ati.com/linuxDfeedback/index.asp)

and file a bug report, as its likely a driver issue.. if you notify ATi about it they can look in to it and hopefully fix it :)

---

### Post by mirtux on 2005-02-11
Thanks i'll do it!
 
 Regards,
 MC

---

### Post by tkw on 2005-02-13
Howdy.

I'm running  2.6.8.1-4-amd64-generic kernel and Warty on Asus A8V mobo with AMD Athlon 64 and Asus Radeon 9200 SE. First after installation of Warty, sunning X jammed the whole PC (X's "generic" ATI driver selected from XFree86 config). I managed to get the system stable by running VESA driver.  I'd like to get my S-video out and more boost from the 9200SE, so I'm trying to get the real ATi drivers to work. However,...

I'm quite unexperienced with Linux in general and especially with all package related issues and find it hard to find out how instructions for "Debian world" should be interpreted when running Ubuntu. I'm not feeling at all safe to try out something based on i386 + Warty or amd64 + Debian instructions. I'd need instructions for amd64 + Warty...

So, could some one please send me detailed instructions on how to get my ATI card supported in Warty running the 2.6.8.1-4-amd64-generic kernel? It's not a problem for me to upgrade the kernel, too, with Synaptic, but I do not know which direction to go in the beginning!

Any help will be much appreciated.

brgrds, TKW

---

### Post by haiku on 2005-02-13
Ok I just got mine working, but it didn't work for me just following your steps.  

I'll post the method I followed and perhaps it will help someone else.

First, I just installed Warty for an amd64 for the first time today.  I've got a radeon 9600xt.

Since my install was fresh I didn't have to worry about getting rid of old fglrx.ko modules so I proceeded on to installing the fglrx module source.

I tried to run 

#alien  fglrx64_4_3_0-8.8.25-1.x86_64.rpm

but I got some lib dependency errors and I couldn't make a the deb package.  But I remembered, that when I was playing around with the hoary live CD earlier I did manage to use alien to turn an rpm into a deb package, so i used a thumb drive to create the deb package on hoary and transfer it to my warty distro. So perhaps you can do this or try to find the package online some where.

I was able to run 

#dpkg --force-overwrite -i <driver package name>.deb

without a hitch.

When trying to run the fglrx compile scripts, I soon found that Gcc wasn't installed by default with warty so I ran synaptic and installed gcc.

From there, i was able to succesfully build the fglrx module, and went on to run fglrxconfig.

I went to start gnome back up, but Xfree wasn't happy and blue screened on me.  So I skeptically tried the easiest thing I could think of to fix it.

I opened up my original XFree86-4 file that I had backed up before running fglrxconfig, and in the device section I simply changed the Driver from

Driver "ati" to Driver "fglrx", I saved and booted up gnome and everything worked, 3d acceleration enabled.

Hopefully this rambling post helps someone... good luck.

-haiku

P.S. Oh, and if anyone knows anything about how I could enable dual monitor support I would appreciate a tip.

---

### Post by Strider on 2005-02-14
Try the following link to get the latest fglrx/ATI drivers on Warty (2.6.8.x):

[http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html)

I tried it and it worked great.  The just the instructions and it should work.

Good luck.

---

### Post by Scottles on 2005-02-16
Seeing as ATi have now released the 8.10.19 drivers, I have made a few small ammendments to the guide which will aid you if you are having trouble updating from the previous ATi 8.8.25 drivers! :)

List of fixes.. in new driver:

Issues Resolved:


    * Starting X on a DVI display no longer results in noisy or flickering output with some displays
    * The Monitor autodetect no longer finds a phantom CRT display if none is connected either RADEON™ X800, X700, X300, or FireGL™ V5100, and V5000
    * The ATI Proprietary Linux driver now works with Apple Cinema display flat panels in single link mode
    * fglrxconfig now produces a proper xorg.conf X Server configuration file
    * Running certain 3D applications no longer result in system hangs on x86_64 systems with RADEON™ 9100/8500 series or FireGL™ 8800 installed
    * Kernel Module Driver compile support for Kernel 2.6.10 lbb
    * XVideo support now available in dualhead configuration lbb
    * 3D geometry corruption no longer occurs with Celestia and other 3d apps
    * A blank screen or X failing to load and returning to the console no longer occurs under X.Org 6.8 when using the config file generated by fglrxconfig
    * 64 Bit systems with 4 or more GB of RAM no longer hang the system while loading the X Server

---

### Post by mirtux on 2005-02-17
[QUOTE=Scottles]
     * 3D geometry corruption no longer occurs with Celestia and other 3d apps
[/QUOTE]
 Thanks Scottles for pointing this out..... now i'm sure that the problem i have with Celestia in not related to some mine misconfiguration.
 
 Regards,
 MC

---

### Post by Dihi Doctor on 2005-02-24
I think I got it all working, but now that I'm back in X, I tried to run fglrxinfo and I get this?
```
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
``` 
So, I'm not sure if it's worked or not :-k. Sadly, it's 2 in the morning and I need some sleep. Any ideas for my tinkering tomorrow?

---

### Post by Dihi Doctor on 2005-02-25
woohoo! Got it working by bodging it:  \\:D/ 
Found a file  /usr/share/fglrx/diversions/libGL.so.1.2 and made a sym link in the directory /usr/X11R6/lib called libGL.so.1

fglrxinfo and fgl_glxgears seem to work fine now. However, I am a bit concerned by my bodge effort. A proper way of doing it would be nice, in case what I have done breaks something else  :roll:

---

### Post by starfarer on 2005-02-28
(Found a file /usr/share/fglrx/diversions/libGL.so.1.2 and made a sym link in the directory /usr/X11R6/lib called libGL.so.1)

Can you give detail commands? Thanks.

---

### Post by Dihi Doctor on 2005-03-01
[QUOTE=starfarer](Found a file /usr/share/fglrx/diversions/libGL.so.1.2 and made a sym link in the directory /usr/X11R6/lib called libGL.so.1)

Can you give detail commands? Thanks.[/QUOTE]

Navigate to the directory and use ln -s to create the symbolic link. As I said, I don't exactly know if this is ok to do, but it worked for me.
```
cd /usr/X11R6/lib
sudo ln -s /usr/share/fglrx/diversions/libGL.so.1.2 libGL.so.1

```

---

### Post by kidrock on 2005-03-04
I get the following error;

root@ubuntu:/lib/modules/fglrx # sh make_install.sh
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
FATAL: Error inserting fglrx (/lib/modules/2.6.8.1-3-386/kernel/drivers/video/fglrx.ko): Operation not permitted
failed.

---

### Post by Scottles on 2005-03-04
Kidrock, I have posted a reply in the other thread you have started about this.. it appears to be because you didnt install GCC or the kernel headers first! You need those installed as prerequisites for installing the fglrx drivers...

---

### Post by kidrock on 2005-03-04
Thanks... I solved  that but still running under mesa...sorry for so many posts...not getting many replies...  :lol:

---

### Post by kidrock on 2005-03-04
some help please....driver installs....but once the new fglrx config file is generated i cant boot into XServer...help please :confused:

---

### Post by kidrock on 2005-03-04
Probelm resolved....but now can;t change the resolution in Gnome :(

---

### Post by Scottles on 2005-03-06
Due to the ATi drivers not supporting the XRandR extension with DGA enabled, you have to alter resolution by modifying your XF86Config file... you can disable DGA to get it working.. but that causes problems with certain games with mouse input in my experience...

---

### Post by Trevor Bramble on 2005-03-06
[QUOTE=kidrock]Probelm resolved....but now can;t change the resolution in Gnome :([/QUOTE]

Well then, how did you resolve it?

---

### Post by ketiko on 2005-09-09
[QUOTE=Trevor Bramble]Well then, how did you resolve it?[/QUOTE]
 Trevor -

To change the resolution do this

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

Go down to the section that looks like this:

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes   "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Where is says "Modes" add the resolutions you want to switch between in order high to low.  The above examples covers some frequently used resolutions.

Save your xorg.conf file.

Now press ctrl+alt+minus(- on number pad) or ctrl+alt+plus (+ on number pad)
This will let toggle between the resolutions listed in your xorg.conf.

Hope that helps.

---

