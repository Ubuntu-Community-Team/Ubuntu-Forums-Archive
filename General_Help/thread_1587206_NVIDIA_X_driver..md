---
title: "NVIDIA X driver."
date: 2010-10-03
forum: General Help
---

### Post by otnarg on 2010-10-03
hi all. this is my 2nd post. i'm fairly new to ubuntu. i have a problem. i've tried my hardest to get the nvidia driver to work. as far as i know i've got it on my system but all i get when i go to the nvidia is

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.


i've checked for updates and if i go to the hardware drivers its blank. i've looked all over google but not had much luck.
my main goal is to get my ubuntu on my tv with hdmi and to get my compiz to work again. when i start up my laptop now it comes up with i'm in low grapic mode. so at the min if i want to watch a mover from my 1tb hard drive i'm having too boot up from windows 7. but i foooooking hate windows!!
any help would be fantastic... 
i'm running on ubuntu 10'4 and my laptop is a samsung r730

thanks guys. 
otanrg :)

---

### Post by otnarg on 2010-10-03
is anyone else having the same problem?

---

### Post by GhostCoder on 2010-10-03
> **otnarg said:**
> hi all. this is my 2nd post. i'm fairly new to ubuntu. i have a problem. i've tried my hardest to get the nvidia driver to work. as far as i know i've got it on my system but all i get when i go to the nvidia is

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.


Open a terminal and run "dpkg -l | grep nvidia". Copy & paste the results here.

I, for example, get:

$ dpkg -l | grep nvidia
ii  nvidia-173                            173.14.22-0ubuntu11                             NVIDIA binary Xorg driver, kernel module and
ii  nvidia-173-modaliases                 173.14.22-0ubuntu11                             Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-185-modaliases                 195.36.24-0ubuntu1~10.04                        Transitional package for nvidia-185-modalias
ii  nvidia-96-modaliases                  96.43.17-0ubuntu1                               Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                         0.2.23                                          Find obsolete NVIDIA drivers
ii  nvidia-current                        195.36.24-0ubuntu1~10.04                        NVIDIA binary Xorg driver, kernel module and
ii  nvidia-current-modaliases             195.36.24-0ubuntu1~10.04                        Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-glx-173                        173.14.22-0ubuntu11                             Transitional package for nvidia-glx-173
rc  nvidia-glx-185                        185.18.36-0ubuntu9                              NVIDIA binary Xorg driver
ii  nvidia-settings                       195.36.08-0ubuntu2                              Tool of configuring the NVIDIA graphics driv

---

### Post by otnarg on 2010-10-03
ii  nvidia-173                                 173.14.22-0ubuntu11                             NVIDIA binary Xorg driver, kernel module and
ii  nvidia-current                             195.36.24-0ubuntu1~10.04                        NVIDIA binary Xorg driver, kernel module and
ii  nvidia-glx-173                             173.14.22-0ubuntu11                             Transitional package for nvidia-glx-173
ii  nvidia-glx-185                             195.36.24-0ubuntu1~10.04                        Transitional package for nvidia-glx-185
ii  nvidia-settings                            195.36.08-0ubuntu2                              Tool of configuring the NVIDIA graphics driv
otnarg@ubuntu:~$

---

### Post by The Cog on 2010-10-03
I'm not sure what GhostCoder was looking for. But you do at least seem to have some nvidia driver packages installed. 

Can you also try the command **lspci -v** and post the part about the vga controller. That will tell us what drivers are currently being used. As an example, mine looks like:
> 05:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 82c7
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=512M]
	Memory at f0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at a000 [size=128]
	[virtual] Expansion ROM at f3000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau


---

### Post by otnarg on 2010-10-03
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
	Subsystem: Samsung Electronics Co Ltd Device c06d
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at f8000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915
thanks for your help cog

---

### Post by sdowney717 on 2010-10-03
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
Kernel driver in use: i915


are you sure you have NVIDIA, looks like intel 
have you plugged the monitor into an Nvidia card ?

I always use the Linux Nvidia driver straight from Nvidia website.
Boot to a command prompt
run file as ./nameoffile.run
follow the prompts, might see some minor errors, let it finish updating everything then restart.

---

### Post by otnarg on 2010-10-03
> **sdowney717 said:**
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
Kernel driver in use: i915


are you sure you have NVIDIA, looks like intel 
have you plugged the monitor into an Nvidia card ?

not sure. i have tried to plug a hdmi cable in and nothing happens. 
as far as i knew i'd got nvidia.if i go system, administration,nvida x server settings  i get this.

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server

---

### Post by sdowney717 on 2010-10-03
[http://www.nvidia.com/object/linux-display-ia32-260.19.04-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.04-driver.html)
download site

if you run lspci -v command 
you should see nvidia somewhere like this
IF you dont see Nvidia, then you dont have Nvidia hardware in the system anywhere.


01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Device 196e:05cc
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at bc00 [size=128]
	[virtual] Expansion ROM at fe8e0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nouveau, nvidiafb

---

### Post by SeijiSensei on 2010-10-03
I don't think you have an NVIDIA card either, but just to be sure....

> **otnarg said:**
> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Did you do what the error message said -- open a terminal and run "sudo nvidia-xconfig"? If not, start with that, then see what happens.

---

### Post by otnarg on 2010-10-03
> **SeijiSensei said:**
> I don't think you have an NVIDIA card either, but just to be sure....



Did you do what the error message said -- open a terminal and run "sudo nvidia-xconfig"? If not, start with that, then see what happens.

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf' 


that happened then, been on the link for the down load.gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.....
i could not open that?? do i need to be doing something else with the file?

---

### Post by sdowney717 on 2010-10-03
Did you download the file?
you might have to make it executable, if it is not, the gedit might want to open the file.
So using filemanager, go to the file right click goto properties and select  allow executing file as program

ALSO, when running nvidia installer, you need to reboot to recovery console
this might dump you at a root prompt
so you need to navigate to where the file is located to run it
like 
cd ..  to back out of root home
cd home
cd username
cd directorywherefielis
then run as 

./nameoffiel.run

I found renaming the file to something simpler is easier when doing all that typing.
AND, the Nvidia installer cant install if your running the GUI desktop.

---

### Post by otnarg on 2010-10-03
i'm a little lost now. how do i boot to root?? sorry i'm a total newbi on this.

---

### Post by sdowney717 on 2010-10-03
when you reboot you should get a grub menu with lists. You select the recovery console at the top of the list under the latest kernel in the list
.
I have seen where some people dont get the grub boot list.
anyway, as it boots, AFTER you select recovery mode, ubuntu will offer a menu, I just select root prompt with networking

This will dump you at a command login or root prompt
The it like MS DOS, you navigate to the nvidia.run file and run it kinda like you would a DOS program.
cd (change directories) till you find the file
ls n* command lists file names starting with 'n' in the current directory.
when you find it run it as

./namefile.run


BUT, if you do not have an nvidia hardware, then this is a waste of time and bother, did you run lspci? that will tell you what hardware you have.

---

### Post by sdowney717 on 2010-10-03
for example here is ls n* output in a terminal

> scott@scott-desktop:~$ cd Download
scott@scott-desktop:~/Download$ ls n*
nevernote-0.90_i386.deb             nvidia19530.run
novell-moonlight-2.99.0.2-i586.xpi  nzd_AdrianneSetup.exe
scott@scott-desktop:~/Download$ 


ALSO, when you get to the root prompt in recovery console, you will be at a terminal like screen with text.

you will find your in root's home directory and the file you downloaded is in your home's user directory, a totally different place.

You need to back out of root's home by typing 'cd ..' cd space period period
'cd ..' always backs you up one level in the directory file structure.

this will put you in the file system, you can test that by typing 'ls' and you should see file system names like 'home' in the list.
then you can cd to home, then cd to username, then cd to where you put the download.run file

run it as ./nameoffile.run
after it installs type in 'reboot'

---

### Post by GhostCoder on 2010-10-03
> **otnarg said:**
> not sure. i have tried to plug a hdmi cable in and nothing happens. 
as far as i knew i'd got nvidia.if i go system, administration,nvida x server settings  i get this.

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server


It is possible to install nvidia-settings even if you have some other graphics chipset. To me it also looked like you have an Intel.

---

### Post by otnarg on 2010-10-03
sdowney717 i'm going to have a look later when i'm home. i'll go on my other laptop and then follow your steps. one other thing i'll ask will this **** up any windows 7 stuff? i don't like windows but need it for auto cad 2010. 


thanks for you time :-)

---

### Post by cocopuffz on 2010-10-03
Here is what I do. 

Download the drivers from nvidia.com.. save it to your Download folder (or wherever you want. As long as you remember where)

Press cntrl + alt + f1 to drop to the terminal/shell

enter your username & password

Kill X by going "sudo service gdm stop"

CD to the file's directory "cd /home/yourusernamehere/Downloads"

type:
chmod +x filenameofdriver.run

That will allow you proper permissions to execute the file

type:
sudo sh filenameofdriver.run

IF all is well, you should be prompted to install the drivers.. go yes yes yes yes... blahablah.. yes. hehe

once you're done type:
sudo reboot

-------------------------------------------
*IF GDM/X doesn't shut down*

exit the installer and...

type:
init 1

This should kill everything and drop you to the root shell...

select what makes sense at this point.. something about terminal blahalh.. 

then type:
telinit 3

The Nvidia drivers require this run level to write to the kernel..

then CD to the file again and try to run it. Should work. Does for me.

---

### Post by sdowney717 on 2010-10-03
> will this **** up any windows 7 stuff?

no it wont, nothing anyone has told you in this thread will do anything to grub or windows.

---

### Post by efflandt on 2010-10-03
Since what you showed us so far makes it a appear that you have Intel video, going around in circles trying to install nvidia video drivers will not do any good.  In fact it may make your Intel video slower because the nvidia GLX does not work with Intel video.

---

### Post by otnarg on 2010-10-03
> **efflandt said:**
> Since what you showed us so far makes it a appear that you have Intel video, going around in circles trying to install nvidia video drivers will not do any good.  In fact it may make your Intel video slower because the nvidia GLX does not work with Intel video.



now i'm unsure what to do if your saying nvidia wont work on my system. is there any other way of geting my ubuntu to work on my tv?

---

### Post by otnarg on 2010-10-03
> **cocopuffz said:**
> Here is what I do. 

Download the drivers from nvidia.com.. save it to your Download folder (or wherever you want. As long as you remember where)

Press cntrl + alt + f1 to drop to the terminal/shell

enter your username & password

Kill X by going "sudo service gdm stop"

CD to the file's directory "cd /home/yourusernamehere/Downloads"

type:
chmod +x filenameofdriver.run

That will allow you proper permissions to execute the file

type:
sudo sh filenameofdriver.run

IF all is well, you should be prompted to install the drivers.. go yes yes yes yes... blahablah.. yes. hehe

once you're done type:
sudo reboot

-------------------------------------------
*IF GDM/X doesn't shut down*

exit the installer and...

type:
init 1

This should kill everything and drop you to the root shell...

select what makes sense at this point.. something about terminal blahalh.. 

then type:
telinit 3

The Nvidia drivers require this run level to write to the kernel..

then CD to the file again and try to run it. Should work. Does for me.



i've tried the cd/home/otnarg/downloads

but comes up with 

-bash:cd/home/otnarg/downloads no such file or directory

---

### Post by yabbadabbadont on 2010-10-03
According to everything I can find (through google), that laptop has integrated Intel graphics, specifically the Intel GMA X4500MHD.  It doesn't have an nvidia chipset, so there isn't any point in trying to get nvidia drivers working with it.  Instead, you should be trying to find out what the correct drivers are for the listed Intel chipset.  (and I think someone pointed them out on the first page ;))

---

### Post by otnarg on 2010-10-03
so anyone know where i can get the correct drivers for my system

---

### Post by sdowney717 on 2010-10-03
[http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html)
> Question: I heard Intel graphics driver supports dual head, but I don't know how to do it.
Answer
We wrote a user guide at [http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html) 

[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

using this may get you your dual output to work onto the TV.
> This guide is targeted for people who want to use extended desktop mode on two outputs. Clone mode should work out-of-box with a normal configuration.

They say, clone mode should work out of the box
Do you have a dual head configuration?
What is on the back of the machine?

---

### Post by otnarg on 2010-10-03
> **sdowney717 said:**
> [http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html)


[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

using this may get you your dual output to work onto the TV.


They say, clone mode should work out of the box
Do you have a dual head configuration?
What is on the back of the machine?


sorry i must be doing all you guys heads in. back end of my machine? i don't know.dual head config i'm lost again.i've been on monitor preferences.
think i'm a little out my depth here

---

### Post by GhostCoder on 2010-10-03
> **otnarg said:**
> sorry i must be doing all you guys heads in. back end of my machine? i don't know.dual head config i'm lost again.i've been on monitor preferences.
think i'm a little out my depth here


What if you just:

sudo apt-get install xserver-xorg-video-intel

There must be still something wrong, because it should have worked out-of-the-box.

---

### Post by otnarg on 2010-10-03
> **GhostCoder said:**
> What if you just:

sudo apt-get install xserver-xorg-video-intel

There must be still something wrong, because it should have worked out-of-the-box.

its saying xserver-xorg so on is already the newest version

---

### Post by The Cog on 2010-10-04
I've go the same chipset on my lappy as you have, except mine is rev 07 on a dell and yours is rev 09. 
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 0263
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at f6c00000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at efe8 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

All I do is plug the telly into the VGA connector (my lappy hasn't got an HDMI and I didn't think the intel set supports HDMI) and then go to the menus System->Preferences->Monitors and set up how I want the displays shared across the desktop. With your telly plugged in, does this dialog show you both screens? I don't have a tv to hand, but here's the dialog with an external monitor plugged in.

---

### Post by otnarg on 2010-10-04
> **The Cog said:**
> I've go the same chipset on my lappy as you have, except mine is rev 07 on a dell and yours is rev 09. 

All I do is plug the telly into the VGA connector (my lappy hasn't got an HDMI and I didn't think the intel set supports HDMI) and then go to the menus System->Preferences->Monitors and set up how I want the displays shared across the desktop. With your telly plugged in, does this dialog show you both screens? I don't have a tv to hand, but here's the dialog with an external monitor plugged in.

no mate. i've tried that route from day one and had no luck. i don't know much about chip sets but thought with the windows working on the tv that ubuntu would have something very easy to match it. so far i'm only using windows for auto cad and to watch flims from a hard drive.its such a shame really as i prefer ubuntu

---

### Post by wewa on 2010-12-06
> type:
sudo sh filenameofdriver.run

IF all is well, you should be prompted to install the drivers.. go yes yes yes yes... blahablah.. yes. hehe


I am doing the 64 bit version on 10.04.
After the sh command, I get:

> NVIDIA Accelerated Graphics Driver for Linux-x86_64 (260.19.21)

The distribution-provided pre-install script failed!
Continue installation anyway?

[Yes] [No]

Is this part of your "go yes yes blah blah?"  I hope so cause I'm about to say yes.

---

