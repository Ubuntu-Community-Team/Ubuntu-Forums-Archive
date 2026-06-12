---
title: "GNOME &amp; Nvidia drivers help"
date: 2012-08-12
forum: General Help
---

### Post by Scozzar on 2012-08-12
So I tried GNOME, didn't like it and ended up deleting it by going through the software center.  But for some reason, the GNOME and GNOME 2D options still exist at the login screen.  How do I remove these?

Next question, I have a Nvidia 540m graphics card in my laptop, but Ubuntu refuses to list it under the "Details" tab.  All it says is "unkown" and I don't even know if it's working the way it should be.  Updates say that they are downloading "nvidia-current" but it still isn't showing it.

Also, is there any routine maintenance that needs to be done to Ubuntu?  I run updates and use BleachBit to clean it out, but other than that, what else?

---

### Post by Scozzar on 2012-08-13
Bump!  Anyone?

---

### Post by bogan on 2012-08-13
Hi!, **Scozzar,**  [Forum Code requests no 'Bumps' at less tan 24 hours intervals.]

Please Post: ```
lspci -nnk | grep -iA3 VGA # [COLOR=DarkOrange]*Edit: iA3 corrected to '-iA3'*[/COLOR]
sudo apt-cache policy nvidia-current
```This will tell if, what & which version is installed & available. ```
gksu nvidia-settings
``` [or DASH>Nvidia Xserver Settings in Unity] Will show if used and other info.

System Details failing to show Screen, Video card & driver correctly, is a known bug in 12.04.

If the above show nvidia-current is not being used, you may need to Activate it in Additional Hardware.

**Routine Maintenance: **
Update Grub &/OR Grub Customizer.
Run:```
sudo apt-get update
sudo apt-get clean
sudo apt-get autoremove
```After multiple Kernal Updates, delete no longer wanted Kernal Images and headers, and other crud. [Ubuntu Tweak has a Janitor function specfic to this task.]

Chao!,** bogan**.

---

### Post by Scozzar on 2012-08-14
Sorry about the bump so early!  I thought that this thread being on the 4th page with no replies was out of hope...

Anyway, here is the first: 


nvidia-current:
  Installed: 302.17-0ubuntu1~precise~xup2
  Candidate: 302.17-0ubuntu1~precise~xup2
  Version table:
 *** 302.17-0ubuntu1~precise~xup2 0
        500 [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) precise/main amd64 Packages
        100 /var/lib/dpkg/status
     295.40-0ubuntu1.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted amd64 Packages
     295.40-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted amd64 Packages
-----------------------------------------------------------

Using "gksu nvidia-current"

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

-----------------------------------------------------------------

Ubuntu tweak?  Sorry, but I'm still quite a novice XC

---

### Post by bogan on 2012-08-14
Hi!, **Scozzar,**

When you Post the output of commands, copy/paste from the terminal to the 'New Reply' edit box, highlight it and select the '#' symbol above the text box, to enclose it in a 'Code' format, making it much easier to read.

You Posted:>  Using "gksu nvidia-[COLOR=Red]current[/COLOR]"

"You do not appear to be using the NVIDIA X driver.  Please edit your X  configuration file (just run `nvidia-xconfig` as root), and restart the X  server."I assume that was a typo for "nvidia-settings".

Did you try running: ```
sudo nvidia-xconfig
```as suggested in that response?

Did you act on:> If the above show nvidia-current is not being  used, you may need to Activate it in Additional  Hardware/Drivers.It will probably show as 'Post release update, or some such.

You did not Post the output of```
 lspci -nnk | grep -iA3 VGA
```Please do so.
[COLOR=DarkOrange]*Edit: iA3 corrected to '-iA3'*[/COLOR]
Ubuntu-Tweak is a program that allows many adjustments to the Ubuntu settings, but is not included in the default installation. To get it do the following in a terminal:```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```It will then be available in Dash, or from a Terminal.

Chao!, **bogan**.
[COLOR=#FFFFFF]
[/COLOR]

---

### Post by Scozzar on 2012-08-14
I'm sorry!  Let's try this again...

For "lspci -nnk | grep iA3 VGA
sudo apt-cache policy nvidia-current" I get:


```
 lspci -nnk | grep iA3 VGA
No such file or directory
 sudo apt-cache policy nvidia-current
[sudo] password for (my name)
nvidia-current:
  Installed: 302.17-0ubuntu1~precise~xup2
  Candidate: 302.17-0ubuntu1~precise~xup2
  Version table:
 *** 302.17-0ubuntu1~precise~xup2 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     295.40-0ubuntu1.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/restricted amd64 Packages
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
```----------------------------------------------------------------
For sudo nvidia-xconfig I get

```
WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'
```----------------------------------------------------------------
You suggested I go to "additional hardware" to activate the Nvidia drivers and this is what shows 

```
There are no proprietary drivers in use on this system
```----------------------------------------------------------------

And I'll run those commands for Ubuntu teak right now!  Thank you!  Hopefully I haven't missed anything

EDIT:  Okay  so after running the janitor, I logged out and logged back in and now it's stuck in 640x480 resolution. What gives?  Would it be easier to delete ubuntu and start over again?  I don't have anything of value for ubuntu YET, so I want to make sure everything is running properly and my system to be spick and span.  As of now, whatever I try isn't working.  Using the "xrandr" command doesn't help and using gedit /etc/x11/xorg.conf only brings up a blank page in text editor...
EDIT3:  I logged in to KDE Plasma workspace and it still stuck at 640x480.  I was able to look into the display menu and the only resolution that pops up is that one and "disable" right underneath it.  This seems to be a pretty typical nvidia driver issue....but why would running ubuntu tweak's 'janitor" cause this?

---

### Post by bogan on 2012-08-14
Hi!, **Scozzar,**

I am the one to be sorry!! my error: the lspci command should be:
 ```
lspci -nnk | grep -iA3 VGA
```With a hyphen before the 'iA3'.

After running nvidia-xconfig and it made a new xorg.conf file, did you re-boot and run nvidia-settings again?
[COLOR=Red]
[COLOR=Black]You Posted:[/COLOR][/COLOR]> [COLOR=Red][COLOR=Black] using gedit /etc/[COLOR=Red]x11[/COLOR]/[/COLOR][/COLOR][COLOR=Black]xorg.conf[/COLOR] only brings up a blank page in text editor. If your quote is accurate, that is because it should be 'X11', with an upper case X.

As to why Ubuntu-tweak Janitor should appear to have affected the screen resolution, I have no explanation to offer.

Were I in your situation, before going to a reinstall, I would do the following:

1.: In Synaptic Package Manager - it is not part of the default, if you do not have it:```
 sudo apt-get install synaptic
```I would ensure that the nvidia-current v. 302.17 is in fact installed, as reported by apt-cache, & install it if not.

2.: I would uninstall  & purge nvidia*& reboot to check performance with the default Nouveau driver. If that was not OK, reinstall nvidia-current.

If that did not work, 3,: I would install the latest nvidia driver from Nvidia.com. [ That needs some familiarity with terminal commands but is doable even for a novice.]

Chao!, **bogan.**

---

### Post by Scozzar on 2012-08-14
Okay I ran the synaptics code and there weren't any problems, but how do I purge Nvidia drivers and stuff?

EDIT"  WAIT!  I got it!  I used the answer from this askubuntu question [http://askubuntu.com/questions/155251/why-am-i-stuck-at-640x480-on-an-optimus-hybrid-graphics-system](http://askubuntu.com/questions/155251/why-am-i-stuck-at-640x480-on-an-optimus-hybrid-graphics-system)

But still, I need to make sure my nvidia drivers are working properly.

------------------------------------------------------------------
Okay, so this is after using the 1spci command


```
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
	Subsystem: Toshiba America Info Systems Device [1179:fc31]
	Kernel driver in use: i915
	Kernel modules: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108 [GeForce GT 540M] [10de:0df4] (rev a1)
	Subsystem: Toshiba America Info Systems Device [1179:fc31]
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb
```

---

### Post by bogan on 2012-08-15
Hi!,** Scozzar**,

Right, the lspci output alters things and explains some weirdness: You have integrated graphics as well as an nvidia card & Optimus. - a good example of why you should give full system info when starting a Thread.

You need to use BumbleBee, there are numerous Threads about it in the forum, but coincidently, there is a current one that gives a clear intro, and also involves a GT540M card. 

I do not myself, know a lot about Bumblebee, and I suggest you could well follow **Marric**'s Code and Links, and address any questions about it to him.

[http://ubuntuforums.org/showthread.php?t=2033360](http://ubuntuforums.org/showthread.php?t=2033360)

In view of this, it might be a good idea to carry out you own suggestion of a re-install before installing Bumblebee, to insure any conflicts are removed.

Best of Luck, Chao!,** bogan.**

---

### Post by Scozzar on 2012-08-15
Alright well I think I got Bumblebee installed correctly.  I have another question.  How do I make myself administrator?  I am the only account on Linux but I can't access my root folder because I don't have the necessary permissions

EDIT:  After installing bumblebee, the terminal showed this 


```
Failed to fetch http://ppa.launchpad.net/bumblebee/stable/ubuntu/pool/main/v/virtualgl/virtualgl-libs-ia32_2.3.1-2~preciseppa1_i386.deb  408  Request Time-out
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by bogan on 2012-08-15
Hi!, [B]Scozzar,
[/B]If you can log-in as 'sudo' when using that command, then you do have normal admin rights; Run Dash>User accounts to check. 

For added administration rights use: 'sudo <command>', 'gksu <command>' for graphical apps, or 'sudo -i' if you are doing a lot of commands.

If you need further info on permissions, have a look at:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you are unable to use 'sudo', check your .Xauthority & .ICEauthority files: ```
ls -al ~/.*authority # those are lower case 'L's not '1' or 'i's
```That should give something like this, with your username instead of 'user':>  -rw------- 1 user user 64308 Aug 15 09:41 /home/user/.ICEauthority
-rw------- 1 user user    57 Aug 15 09:41 /home/user/.XauthorityIf they do not have just the '-rw---' in front, or have 'root' instead of 'user'; that is the cause of your problem - whatever that may be, you do not explain what you want to access the 'root' folder for, or with what method.

If that is what you get, then use:```
rm ~/.Xauthority ~/ICEauthority  # for the offending file.
```and then re-boot.

Regarding the BumbleBee error message, have you done what it suggested??

If so, what messages did you get?

Chao!,** bogan.**

---

### Post by Scozzar on 2012-08-15
Yeah, I don't think Bumblebee is working...I typed in "optirun glxgears"  and all it says is:

optirun: command not found


I'm really getting annoyed with this...

---

### Post by bogan on 2012-08-16
Hi!, **All,**

[COLOR=Blue]There is a new nvidia driver full released version 304.37, no longer a 'Beta', available [/COLOR]from nvidia downloads. It supports GeForce 6xxx series cards, and later.

If you have Optimus, Hybrid, with Integrated Graphics as well as a Nvidia card, see the note below.

 This Link is for the 32 bit version, check you get the correct one:
[http://www.nvidia.co.uk/object/linux-display-ia32-304.37-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-304.37-driver-uk.html)

If you already have a nvidia driver installed - not one of the   nvidia-current versions - it is now accessible using: ```
sudo   nvidia-installer --latest 
```  which now returns: v304.37 and the  currently installed version, without altering anything.

So you can now install it with, from a TTY Terminal:  ```
sudo   nvidia-installer -f 
```Which will download it, un-install the   previous version and install the new, creating a new Xorg.conf file.
Or you can download it and run the .run file with 'sh'.

In either case you need to close the Xserver session first, using:   ```
sudo service lightdm stop
```I downloaded and installed it in   an updated version of 12.04 LTS  3.2.0-29-generic - not the pae version -   and it installed and ran  correctly with no problems on a GT 7650  card.

**[COLOR=Blue]For those with Integrated Graphics[/COLOR]**:   Extract from Nvidia's "Supported Products" notes:".... in particular,   notebook and all-in-one desktop designs with switchable  (hybrid) or   Optimus graphics will not work if means to disable the  integrated   graphics in hardware are not available. ...".

Chao!,** bogan.**

---

### Post by Scozzar on 2012-08-18
Well I got the "cannot connect to secondary GPU" so I need to move a file.  How do I do that?  It might be a while, I gotta perform a fresh install again...

Alright, I did a fresh install.  I get the same error...Running "optirun glxgears" gives me:


```
[ 1549.611336] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[ 1549.611483] [ERROR]Aborting because fallback start is disabled.
```

And I'm pretty sure I have the latest drivers installed...

---

### Post by Scozzar on 2012-08-30
Hello?  Anyone?  I just updated and nvidia-current was one of the things being updated and it still doesn't work...As of now, I think I have bumblebee and the error in the previous post is the error I still get.

---

### Post by bogan on 2012-08-31
Hi!,** Scozzar,**

Sorry, I do not know enough about hybrid graphics & Bumblebee to advise on your particular problem; other than that from your earlier Posts it appeared to me that Bumblebee was not installing correctly, but presumably your posting: > As of now, I think I have bumblebee  means you re-installed it after re-installing Ubuntu. Yes??

Hopefully, someone more aware of Hybrid problems will come in.

Chao!, **bogan**.

---

