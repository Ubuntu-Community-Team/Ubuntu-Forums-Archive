---
title: "How do you install PCSX2?"
date: 2011-03-22
forum: General Help
---

### Post by gstla on 2011-03-22
I'd like to know how to install PCSX2 on my 64-Bit Ubuntu 10.10 Maverick OS. 

pcsx2-0.9.7-r3881-linux.tar.gz - is the version I downloaded, I managed to extract it with the Archive Manager, but I don't really know where to go from here. 

It's more complicated than going to the software center because it's not supported.  From searching around I also see that w/o tweaks it's only possible to use the 32-bit version.  Would it be possible to use the 32-bit version on a 64-bit OS. 

 I'm unsure of this because .exe (32 bit(?) still install in Win7x64 (.msi) extensions.  My research indicated that it could be installed, but it had a few tweaks.  I'd appreciate any help I can get, but please do not post a "_let me google that for you_" I'm posting here because I'd appreciate any help a **real person **(not an outdated forum thread) could possibly provide. 

It'd help if you made it as newbie friendly as possible.  I can copy and past terminal commands, and have so in the past, but I have trouble with things like navigating to directories, how to go about such a thing & so on.

---

### Post by Iacoi on 2011-04-09
Hi! Stumbled upon this post while trying to figure this out myself around the time you posted -- thought I'd head back and let you know what I figured out.

First off - pcsx2 will not run on a 64-bit version of linux. So you have two choices, install a 32-bit version of linux on your comp or run pcsx2 through chroot on your 64-bit installation.

The first option is pretty self-explanatory, and something I figure you can already do seeing how you have ubuntu installed. The second option, chroot, is a little bit more involved but will allow you to run pcsx2 without having to reboot your machine everytime you want to play FFX.

Either way, I'd rather not explain the entire process without knowing if you're even still watching this post after two weeks or if you feel like going with chroot. So... I'll await your response!

[EDIT] As a side note if you're already using a windows os on the same machine you might just want to go ahead and install pcsx2 on that, as the process is much easier.

---

### Post by magnetic651 on 2011-04-09
I am having the same problem, as I am running a 64-bit linux install/  How do you go about running it with chroot??

---

### Post by Iacoi on 2011-04-10
[COLOR="Red"]**NOTE: This string of commands was designed around PCSX2 0.9.7, almost two years ago. This should no longer be used as a copypaste solution, although the method detailed here may still work. As such, I would recommend you do not attempt this without trying to understand the commands used. If that doesn't sound like something you'd be interested in, I'd suggest installing PCSX2 under a Windows OS, or simply try to install the Linux port PCSX2 provides. [Clicky!]("http://pcsx2.net/download/releases/linux.html")**[/COLOR]


Alright! We have a taker.

So I'm going to provide two methods with which you can install pcsx2 on a 64-bit system.

Method A is for people who could honestly care less how and why certain commands run the way they do and just want a quick copy paste solution. It will install a 32-bit version of Lucid Lynx through the utility schroot and then install pcsx2.
Method B is a step by step explanation of Method A that will require a bit more work, but will explain the how and why behind each command.

[SIZE=3]Method A:[/SIZE]
Run this.
```
sudo apt-get install debootstrap schroot ; sudo printf "[lucid_i386]\ndescription=Ubuntu 10.04 Lucid for i386\ndirectory=/srv/chroot/lucid_i386\npersonality=linux32\nroot-users="$USER"\ntype=directory\nusers="$USER > lucid_i386_conf ; sudo cp lucid_i386_conf /etc/schroot/chroot.d/ ; sudo rm lucid_i386_conf ; sudo mkdir -p /srv/chroot/lucid_i386 ; sudo debootstrap --variant=buildd --arch i386 lucid /srv/chroot/lucid_i386 http://archive.ubuntu.com/ubuntu ; xhost +LOCAL: ; schroot -c lucid_i386 -u root ; cd $HOME ; printf "#! /bin/bash\nexport DISPLAY=:0.0\nsh "$HOME"/.pcsx2-read-only/bin/launch_pcsx2_linux.sh" > pcsx2 ; sudo cp pcsx2 /srv/chroot/lucid_i386/bin/ ; sudo chmod 700 /srv/chroot/lucid_i386/bin/pcsx2 ; printf "#! /bin/bash\nxhost +LOCAL:\nschroot -c lucid_i386 -u root" > start32bit ; sudo cp start32bit /bin/start32bit ; sudo chmod 700 /bin/start32bit ; rm pcsx2 start32bit ; sudo dpkg-reconfigure locales ; sudo apt-get install language-pack-en ; locale-gen en_US.UTF-8 ; clear ; exit
```At some point in running the aforementioned code your terminal prompt will switch from the typical 
user@ComputerName:dir$ to 
(lucid_i386)root@ComputerName:dir#

When this happens, run the following:
```
printf "## sources.list\n\ndeb http://archive.ubuntu.com/ubuntu lucid main restricted\ndeb-src http://archive.ubuntu.com/ubuntu lucid main restricted\n\ndeb http://archive.ubuntu.com/ubuntu lucid-updates main restricted\ndeb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted\n\ndeb http://archive.canonical.com/ubuntu lucid partner\ndeb-src http://archive.canonical.com/ubuntu lucid partner\n\ndeb http://archive.ubuntu.com/ubuntu lucid universe\ndeb-src http://archive.ubuntu.com/ubuntu lucid universe\ndeb http://archive.ubuntu.com/ubuntu lucid-updates universe\ndeb-src http://archive.ubuntu.com/ubuntu lucid-updates universe\n\ndeb http://archive.ubuntu.com/ubuntu lucid multiverse\ndeb-src http://archive.ubuntu.com/ubuntu lucid multiverse\ndeb http://archive.ubuntu.com/ubuntu lucid-updates multiverse\ndeb-src http://archive.ubuntu.com/ubuntu lucid-updates multiverse\n\ndeb http://security.ubuntu.com/ubuntu lucid-security main restricted\ndeb-src http://security.ubuntu.com/ubuntu lucid-security main restricted\ndeb http://security.ubuntu.com/ubuntu lucid-security universe\ndeb-src http://security.ubuntu.com/ubuntu lucid-security universe\ndeb http://security.ubuntu.com/ubuntu lucid-security multiverse\ndeb-src http://security.ubuntu.com/ubuntu lucid-security multiverse" > /etc/apt/sources.list ; apt-get update ; apt-get install gcc-4.3 gcc-4.3-multilib g++-4.3 g++-4.3-multilib cmake libasound2-dev libbz2-dev libgl1-mesa-dev libglew1.5-dev libglu1-mesa-dev libgtk2.0-dev libjpeg-dev libsdl1.2-dev libsoundtouch1-dev libsparsehash-dev libwxbase2.8-dev libwxgtk2.8-dev libx11-dev nvidia-cg-toolkit portaudio19-dev zlib1g-dev subversion jockey-gtk ; export DISPLAY=:0.0 ; dbus-daemon --system ; jockey-gtk ; svn checkout http://pcsx2.googlecode.com/svn/trunk/ .pcsx2-read-only ; cd .pcsx2-read-only/ ; cmake CMakeLists.txt -DCMAKE_BUILD_TYPE=Release -DCMAKE_BUILD_STRIP=TRUE ; make ; make install ; exit
```The above code will take about 30 minutes to run and install about 600 Mb of software. It will create two new commands:
start32bit -- enters a 32-bit environment, must be run as superuser either through sudo or su
pcsx2 -- runs pcsx2 in the aforementioned 32-bit environment

I'll put Method B in my next post.

---

### Post by Iacoi on 2011-04-10
[COLOR="Red"]**NOTE: This string of commands was designed around PCSX2 0.9.7, almost two years ago. This should no longer be used as a copypaste solution, although the method detailed here may still work. As such, I would recommend you do not attempt this without trying to understand the commands used. If that doesn't sound like something you'd be interested in, I'd suggest installing PCSX2 under a Windows OS, or simply try to install the Linux port PCSX2 provides. [Clicky!]("http://pcsx2.net/download/releases/linux.html")**[/COLOR]

[SIZE=3]Method B:[/SIZE]

**[SIZE=2]Part 1) Setting up the 32-bit environment with schroot[/SIZE]**
First off we're going to set up and download the files required for schroot and corresponding 32-bit environment.
```
sudo apt-get install debootstrap schroot
```Secondly you'll  need to create your schroot configuration file. I'll be using a 32-bit  version of Lucid Lynx for my examples from here on out, so if you plan  on using another version of ubuntu you'll need to replace lucid with  whatever version you wish to install in the following commands.
```
sudo gedit /etc/schroot/chroot.d/lucid_i386_conf
```Enter the  following into the file, making sure to enter your own information.
```
[lucid_i386]
description=Ubuntu 10.04 Lucid for i386
directory=/srv/chroot/lucid_i386
personality=linux32
root-users=USER_NAME
#run-setup-scripts=true
#run-exec-scripts=true
type=directory
users=USER_NAME
```Note: For versions of ubuntu prior to lucid lynx, uncomment run-setup-scripts and run-exec-scripts and name your configuration file hardy_i386.conf instead of hardy_i386_conf

Next, define a directory in which your 32-bit environment will store itself.
```
sudo mkdir -p /srv/chroot/lucid_i386
```Then build the 32-bit environment.
```
sudo debootstrap --variant=buildd --arch i386 lucid /srv/chroot/lucid_i386 http://archive.ubuntu.com/ubuntu
```Finally, enter your newly created 32-bit environment.
```
schroot -c lucid_i386 -u root
```**[SIZE=2]Part 2) Downloading and installing pcsx2[/SIZE]**
[SIZE=1]This part assumes you are continuing directly from part 1, if you are not then enter your 32-bit environment first.

Download an editor with which to edit your sources.list file -- if you're familiar with vi you can use that, for everyone else I would recommend you install nano.
[/SIZE]```
apt-get install nano
```Note that you do not need to run this command as root because you are already recognized as the root user in the 32-bit environment.

Then backup your current sources.list file and open it for editing.
```
cp /etc/apt/sources.list /etc/apt/sources.list.backup
nano /etc/apt/sources.list
```Replace your sources.list with the following, remembering to replace lucid with whichever version of ubuntu you're using.
```
## sources.list

deb http://archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted

deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted

deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu lucid universe
deb-src http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu lucid-updates universe
deb-src http://archive.ubuntu.com/ubuntu lucid-updates universe

deb http://archive.ubuntu.com/ubuntu lucid multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates multiverse

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```Then install pcsx2's dependencies.
```
apt-get update
apt-get install gcc-4.3 gcc-4.3-multilib g++-4.3 g++-4.3-multilib cmake libasound2-dev libbz2-dev libgl1-mesa-dev libglew1.5-dev libglu1-mesa-dev libgtk2.0-dev libjpeg-dev libsdl1.2-dev libsoundtouch1-dev libsparsehash-dev libwxbase2.8-dev libwxgtk2.8-dev libx11-dev nvidia-cg-toolkit portaudio19-dev zlib1g-dev subversion jockey-gtk
```Change your current directory to wherever you want your pcsx2 to reside as an example, you would type the following to go to your home directory.
```
cd /home/USER_NAME
```Then download the newest pcsx2 files.
```
svn checkout http://pcsx2.googlecode.com/svn/trunk/ .pcsx2-read-only
```In the above command, .pcsx2-read-only is the name of the folder in which the downloaded files will reside. You can rename it to whatever you want.

Change directory into the folder in which you downloaded the pcsx2 files.
```
cd .pcsx2-read-only/
```Build the make files
```
cmake CMakeLists.txt -DCMAKE_BUILD_TYPE=Release -DCMAKE_BUILD_STRIP=TRUE
```Build pcsx2 and install
```
make
make install
```Thats it. Whenever you want to use pcsx2 run the following commands.
```
xhost +LOCAL:
schroot -c lucid_i386 -u root

export DISPLAY=:0.0
sh (path to your pcsx2 download folder)/bin/launch_pcsx2_linux.sh
```The first two commands are run from your 64-bit actual ubuntu install, while the final two will run from within your 32-bit environment.


**[SIZE=2][EDIT] Installing your graphics driver[/SIZE]**
From your 64-bit installation, run the following.
```
xhost +LOCAL:
```Then enter your 32-bit environment and run
```
export DISPLAY=:0.0
dbus-daemon --system
jockey-gtk
```Select your driver, install and exit the shell.
Now you're ready to go!

---

### Post by wingnux on 2011-04-27
I get this error when running the first line of Method A:

> I: Base system installed successfully.
non-network local connections being added to access control list
W: No chroots are defined in '/etc/schroot/schroot.conf'
E: lucid_i386: Chroot not found
Generating locales...
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
  pt_BR.UTF-8... up-to-date
  pt_PT.UTF-8... up-to-date
Generation complete.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
language-pack-en is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Generating locales...
  en_US.UTF-8... up-to-date
Generation complete.

wingnux@wingnux-desktop ~ $ 


I'm running Linux Mint 10 64bit (Based on Ubuntu Maverick 10.10).

Solved by running: sudo cp /etc/schroot/chroot.d/maverick_i386_conf /etc/schroot/schroot.conf

---

### Post by ancow on 2011-04-28
> **wingnux said:**
> Solved by running: sudo cp /etc/schroot/chroot.d/maverick_i386_conf /etc/schroot/schroot.conf
That's not a very good idea. This way, you not only lose the example config, it's also less portable and there is a cleaner way of doing it.
The problem is that schroot has become quite picky about the file names in /etc/schroot/chroot.d. Because of that, you want to name the file lucid-i386 (no underscores or dots). This should be fixed in recent versions of schroot, but you won't get one of them for maverick or any previous version of ubuntu.

Here's the modified set of commands which should work with maverick:
```
sudo apt-get install debootstrap schroot ; sudo printf "[lucid_i386]\ndescription=Ubuntu 10.04 Lucid for i386\ndirectory=/srv/chroot/lucid_i386\npersonality=linux32\nroot-users="$USER"\ntype=directory\nusers="$USER > lucid-i386 ; sudo cp lucid-i386 /etc/schroot/chroot.d/ ; sudo rm lucid-i386 ; sudo mkdir -p /srv/chroot/lucid_i386 ; sudo debootstrap --variant=buildd --arch i386 lucid /srv/chroot/lucid_i386 http://archive.ubuntu.com/ubuntu ; xhost +LOCAL: ; schroot -c lucid_i386 -u root ; cd $HOME ; printf "#! /bin/bash\nexport DISPLAY=:0.0\nsh "$HOME"/.pcsx2-read-only/bin/launch_pcsx2_linux.sh" > pcsx2 ; sudo cp pcsx2 /srv/chroot/lucid_i386/bin/ ; sudo chmod 700 /srv/chroot/lucid_i386/bin/pcsx2 ; printf "#! /bin/bash\nxhost +LOCAL:\nschroot -c lucid_i386 -u root" > start32bit ; sudo cp start32bit /bin/start32bit ; sudo chmod 700 /bin/start32bit ; rm pcsx2 start32bit ; sudo dpkg-reconfigure locales ; sudo apt-get install language-pack-en ; locale-gen en_US.UTF-8 ; clear ; exit
```

---

### Post by Iacoi on 2011-04-30
Hey guys, sorry for not responding -- I haven't really been on ubuntu forums at all lately. As for wingnux's issue, I really only made this fix for OP and magnetic651 as a quick brute force solution. But glad to see you guys worked it out!

---

### Post by gstla on 2011-05-04
Thanks for this, I appreciate it tons.

---

### Post by aenertia on 2011-05-06
here is the required all in one command for natty i386 chroot setup:

> 
sudo apt-get install debootstrap schroot ; sudo printf "[natty_i386]\ndescription=Ubuntu 11.04 Natty for i386\ndirectory=/srv/chroot/natty_i386\npersonality=linux32\nroot-users="$USER"\ntype=directory\nusers="$USER > natty-i386 ; sudo cp natty-i386 /etc/schroot/chroot.d/ ; sudo rm natty-i386 ; sudo mkdir -p /srv/chroot/natty_i386 ; sudo debootstrap --variant=buildd --arch i386 natty /srv/chroot/natty_i386 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) ; xhost +LOCAL: ; schroot -c natty_i386 -u root ; cd $HOME ; printf "#! /bin/bash\nexport DISPLAY=:0.0\nsh "$HOME"/.pcsx2-read-only/bin/launch_pcsx2_linux.sh" > pcsx2 ; sudo cp pcsx2 /srv/chroot/natty_i386/bin/ ; sudo chmod 700 /srv/chroot/natty_i386/bin/pcsx2 ; printf "#! /bin/bash\nxhost +LOCAL:\nschroot -c natty_i386 -u root" > start32bit ; sudo cp start32bit /bin/start32bit ; sudo chmod 700 /bin/start32bit ; rm pcsx2 start32bit ; sudo dpkg-reconfigure locales ; sudo apt-get install language-pack-en ; locale-gen en_US.UTF-8 ; clear ; exit



---

### Post by wolffangalchemist on 2011-05-07
> **aenertia said:**
> here is the required all in one command for natty i386 chroot setup:
i'm having a problem with this it installs the chroot fine but i get this when trying to run pcsx2
```
(natty_i386)root@linux-GA-MA785GM-US2H:/home/linux# pcsx2 --
sh: Can't open /home/linux/.pcsx2-read-only/bin/launch_pcsx2_linux.sh

```
any suggestions?

---

### Post by TheManno1 on 2011-05-08
Is this for the latest pcsx2 .9.8

---

### Post by TheManno1 on 2011-05-08
How do you run pcsx2 when the chroot is installed.

---

### Post by ancow on 2011-05-09
> **wolffangalchemist said:**
> i'm having a problem with this it installs the chroot fine but i get this when trying to run pcsx2
```
(natty_i386)root@linux-GA-MA785GM-US2H:/home/linux# pcsx2 --
sh: Can't open /home/linux/.pcsx2-read-only/bin/launch_pcsx2_linux.sh

```
any suggestions?
Personally, I'd guess the compile step didn't run quite successfully. From method B, try doing step "Part 2) Downloading and installing pcsx2". Report any errors that occur.

---

### Post by Mistro on 2011-05-14
\\:D/
I am always surprised with the detailed solution for any problem I face under Ubuntu !
You guys at Ubuntu forums are the best!
thanks alot

---

### Post by DeiwosN on 2011-05-16
Ok, I'm not exactly a very experienced user of Linux, I'll just say to begin with.

Anyway, the problem I'm having with this solution is that when I'm doing the 'make' for PCSX2, it gets to making the plugins and then.. well, the C files have includes for gtk things and all that, but make is treating them like relative paths and will only continue if I copy say the gtk directory into the Src directory, and I'm not really sure if I want to go about doing that for everything included in every plugin.

Is there a way to tell it to look in the right places for these? I don't know how to tell it to do that.

Edit: example output, note that this is after copying said gtk/gdk folders in:

```
[ 40%] Building C object plugins/CDVDlinuz/Src/CMakeFiles/CDVDlinuz.dir/Linux/aboutbox.c.o
In file included from /home/deiwos/.pcsx2-read-only/plugins/CDVDlinuz/Src/Linux/gdk/gdk.h:32:0,                        
                 from /home/deiwos/.pcsx2-read-only/plugins/CDVDlinuz/Src/Linux/gtk/gtkwidget.h:34,
                 from /home/deiwos/.pcsx2-read-only/plugins/CDVDlinuz/Src/Linux/gtk/gtkcontainer.h:35,
                 from /home/deiwos/.pcsx2-read-only/plugins/CDVDlinuz/Src/Linux/gtk/gtkbin.h:35,
                 from /home/deiwos/.pcsx2-read-only/plugins/CDVDlinuz/Src/Linux/gtk/gtkbutton.h:35,
                 from /home/deiwos/.pcsx2-read-only/plugins/CDVDlinuz/Src/Linux/aboutbox.c:49:
/home/deiwos/.pcsx2-read-only/plugins/CDVDlinuz/Src/Linux/gdk/gdkapplaunchcontext.h:30:21: fatal error: gio/gio.h: No such file or directory
compilation terminated.
make[2]: *** [plugins/CDVDlinuz/Src/CMakeFiles/CDVDlinuz.dir/Linux/aboutbox.c.o] Error 1
make[1]: *** [plugins/CDVDlinuz/Src/CMakeFiles/CDVDlinuz.dir/all] Error 2
make: *** [all] Error 2
```

---

### Post by Osmodivs on 2011-06-29
In case I do not want anymore to have the 32 bit enviroment, How do I delete it? I want to uninstall the 32bit enviroment I created following your instructions.

---

### Post by Diablero on 2011-07-16
Hi! Compilation has passed successfully, but unfortunately in 32 bit environment I can not adjust a video card. When I start a command "[FONT=monospace]jockey-gtk[/FONT]" anything in the list is not present and and it is written "No proprietary drivers are in use on this system". But in system i have installed 11.6 Catalyst, using ATI card. Please help=)

---

### Post by ancow on 2011-07-16
Just out of curiosity: is there anything preventing you from manually installing the necessary drivers in the chroot?

---

### Post by Diablero on 2011-07-16
I tried to install manually, but it all the same is not installed, gives out an error, does not know what to it the version to put.

"Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-33-generic:; make sure that the version is being
correctly set by --iscurrentdistro"

May be soluiton ih there? [http://code.google.com/p/pcsx2/wiki/ChrootAnd64bStatusLinux](http://code.google.com/p/pcsx2/wiki/ChrootAnd64bStatusLinux)
**Proprietary Driver**

 
[LIST]
[*]NVIDIA
[LIST]
[*]Do not know ^^    *(arcum42 -- I've got an nvidia card, so I'll have to check some time...)*
[/LIST]
[*]ATI/AMD (Note: library paths depend on distributions)
[LIST=1]
[*]Use the 32bits glxinfo to check that direct rendering is enabled
[*]You need to overwrite the libGL.so.* libraries provided by mesa with the 32bits version in fglrx.
[*]You must add the 32bits fglrx_dri.so
[/LIST]
[/LIST]
But unfortunately I do not have not enough knowledge how to do these 3 steps and not to break anything.

---

### Post by ancow on 2011-07-16
About two seconds of googling that error message yields: [http://ubuntuforums.org/showthread.php?t=1550841](http://ubuntuforums.org/showthread.php?t=1550841)

---

### Post by Diablero on 2011-07-16
No, it not that. I think that the decision is here [http://code.google.com/p/pcsx2/wiki/ChrootAnd64bStatusLinux](http://code.google.com/p/pcsx2/wiki/ChrootAnd64bStatusLinux)
[B]
[/B]Proprietary Driver 
[LIST]
[*]NVIDIA
[LIST]
[*]Do not know ^^    *(arcum42 -- I've got an nvidia card, so I'll have to check some time...)*
[/LIST]
[*]ATI/AMD (Note: library paths depend on distributions)
[LIST=1]
[*]Use the 32bits glxinfo to check that direct rendering is enabled
[*]You need to overwrite the libGL.so.* libraries provided by mesa with the 32bits version in fglrx.
[*]You must add the 32bits fglrx_dri.so
[/LIST]
[/LIST]
But unfortunately I do not have not enough knowledge how to do these 3 easy steps and not to break anything.

---

### Post by ancow on 2011-07-16
What I was trying to point out was that the proprietary ATI/AMD driver isn't compatible yet. You might want to install a chroot with 10.04 which the driver is compatible with.

You actually found the workaround, but since I don't have an ATI/AMD card yet, I can't really help you much. It sounds pretty risky anyway. The first step is easy (simply execute "sudo apt-get install mesa-utils" to install it and then run "glxinfo" from the chroot command line). The second and third steps may completely break your 3D capability, so you might want to ask somebody who's already done it, e.g. the person who wrote the wiki entry.

---

### Post by RyDroid on 2011-09-05
I have installed all, without problem.

But, I don't know how to open PCSX2 :
```
rayquaza@spanti:~$ sudo start32bit
[sudo] password for rayquaza: 
non-network local connections being added to access control list
(lucid_i386)root@spanti:/home/rayquaza# pcsx2
sh: Can't open /root/.pcsx2-read-only/bin/launch_pcsx2_linux.sh
(lucid_i386)root@spanti:/home/rayquaza# 
```

---

### Post by pearsy99 on 2011-10-07
Where do I put the bios file? I cannot seem to find the folder I followed your tutorial and installed pcsx2 in chroot on xubuntu 11.04 64 bit. pcsx2 runs but i cannot start it as i don't know where to put the bios can anyone help?

---

### Post by pkersey on 2011-11-24
> **aenertia said:**
> here is the required all in one command for natty i386 chroot setup:

I'd like to share my experience. I have succesfully installed PCSX2 under "**Natty 11.04 64-bit**" through those *schroot* guidelines, but with a few twists.

"Ubuntu Lucid 32-bit" didn't work for me. The packages were all installed, PCSX2 0.9.8 was downloaded and compiled, but then jockey-gtk *failed to detect and install* NVidia drivers. 

So I decided to try "Natty 11.04 32-bit" instead of Lucid.

After downloading the packages, something was wrong yet. Some packages didn't install properly, so jockey-gtk wouldn't open. Then I did "apt-get install synaptic", launched Synaptic, selected the appropriate missing packages (looking at the information provided by the colleague *aenertia*), and the NVidia driver packages.

After that I started *jockey-gtk* and it detected my nVidia driver correctly, but it wasn't activated. Therefore, I activated it. The python script running the jockey interface "broke" when finishing the activation procedure, but after one minute or two I forcefully closed the jockey window and restarted it to check whether the driver was at least activated... and it was. No problem.

Once I had previously compiled PCSX2 using the steps given for "Lucid-32", I didn't need to do that all again. Just executed the "pcsx2" script and it launched.

I know this isn't an emulation forum, but I think the following information might be useful for those trying to configure the application to get the most of it.

I got "God Of War 1" running at 33-45 FPS in windowed mode in my equipment. I don't know how much FPS it was running in full screen, but I had the strange feeling it was running a tad bit faster, believe it or not. 

[I]Intel i5 2500K quad core 3.3GHz  8GB RAM
Nvidia Geforce GTX 560 TI 1GB GDDR5 256-bit[/I]

I achieved that frame rate through the following settings:
- Enabled plugins: Display=ZZOgl 0.3.0, Sound=SPU-2x 2.0.0 (others are default)
- Emulator Settings: "Preset 5 - Aggresive piu" (checkbox at the bottom)
- ZZOgl Configuration: 
   Bilinear filter: normal
   Interlacing: None
   Anti-aliasing: 1x
- SPU2X Configuration:
  Interpolation: 0 - Nearest
  Disable effects processing
  Output settings: defaults (Portaudio / Alsa / Time Stretch / Latency: 300) 
  Advanced Settings: All sliders to the minimum ( 20 / 10 / 5)

Thanks everybody!

---

### Post by dasnk on 2012-01-05
sh: Can't open /root/.pcsx2-read-only/bin/launch_pcsx2_linux.sh

Now how do i uninstall all this junk?

---

### Post by diwo23 on 2012-11-22
hello please how can I delete all this stuff???I installed Method A and I'd like to remove it.Can anyone help me? thanx and sorry for my english...

---

### Post by CharlesA on 2013-01-02
This thread is pretty old and the version of PCSX2 that method works with is depreciated.

This thread is closed.

---

