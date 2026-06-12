---
title: "Ubuntu booting to tty1 console!"
date: 2012-09-05
forum: General Help
---

### Post by Cup2078 on 2012-09-05
Hi, my computer keeps booting to a tty1 console and i dont know what to do, il post specs and try get some screens up but for now i dont have much to tell you, im new to linux so i cant be sure like i am on windows! 

thanks in advance,
         Noah Murray.

---

### Post by oldfred on 2012-09-05
Welcome to the forums.

Do you get a grub menu? If not hold shift key from BIOS to get menu.

Do you get a login at command line?
Or can from grub menu you boot the recovery mode? 

May be video issue.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Cup2078 on 2012-09-05
when booting normally i boot to a command line login, when i boot into recovery mode i get a recovery menu, witch i assume is the grub menu you speak of, otherwise no i dont get the grub menu.

---

### Post by oldfred on 2012-09-05
No, recovery mode is another menu to let you run updates or use command line to login and run updates.

You should be able to hold shift from BIOS until grub menu appears.

---

### Post by Cup2078 on 2012-09-05
So being on an HP you mean like while the HP screen is up when i start the computer i press F10? because i did that and when the bios appeared i held down shift for about 60 sec and nothing happens

---

### Post by Cup2078 on 2012-09-05
Wait, ive got it the boot select menu? that comes up before i boot ubuntu, i selected normal ubuntu then it went to tty1.

---

### Post by oldfred on 2012-09-05
Try the nomodeset on linux line in place of quiet splash.

What video card/chip do you have? And what system? Some require other boot parameters in addition to nomodeset or in place of nomodeset.

If you get command line login and login in you can run this:
#To see video:
sudo lshw | grep -A 11 display
#Resolution:
xwininfo -root

Does this give an error?
sudo service lightdm start
#or: gdm, lightdm, xdm, etc depending on what you have

---

### Post by Cup2078 on 2012-09-05
i have a HP pavilion a1747c with 1024MB ram nvidia geforce 6150 LE and AMD athlon dual core 4600+

---

### Post by Cup2078 on 2012-09-05
i think i may have the wrong bit version,the sudo lshw|grep -A 11 display said "width:64 bits" should i download the 64 bit version? i thought my computer was 32 bit

---

### Post by oldfred on 2012-09-05
With 1GB of RAM you probably do not want the 64Bit version anyway. the width may be the width of the video card processor which is not the same as the cpu.

nVidia needs the nomodeset.

Not sure with 1GB and an older video card if the newest versions of Unity work well or not. You may need fallback or gnome-panels in 2d.

You should have a menu like this:

[https://help.ubuntu.com/community/Grub2/Submenus](https://help.ubuntu.com/community/Grub2/Submenus)

---

### Post by Cup2078 on 2012-09-05
Ive got a menu like that, without the mouse, and i dont have the previous versions button.

---

### Post by oldfred on 2012-09-05
If you follow the procedure for nomodeset does it boot?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Cup2078 on 2012-09-05
No it just took me to the console login again :/

---

### Post by Sanitylost on 2012-09-05
I had a problem with this when i tried updating my drivers for the nvidia card. Try installing gdm and see if this helps you bypass the tty1 screen. ```
 sudo apt-get install dgm
```. 
This should take you to a selection screen after the installation completes. Dgm is the old style display system before 12.04.  If you want to go back to the original open the terminal and type:
```

sudo apt-get purge lightdm
sudo apt-get remove lightdm
sudo apt-get autoremove
sudo apt-get install lightdm

```This will bring back the selection screen from earlier. Choose lightdm and things should go back to normal. I hope this helps.

---

### Post by Cup2078 on 2012-09-05
unable to locate package dgm

---

### Post by Sanitylost on 2012-09-05
stupid typo...gdm.

---

### Post by Cup2078 on 2012-09-05
Oh lol thanks XD

---

### Post by Sanitylost on 2012-09-05
Did it work?

---

### Post by Cup2078 on 2012-09-05
at the first selection screen should i hit gdm?

---

### Post by Sanitylost on 2012-09-05
yes

---

### Post by Cup2078 on 2012-09-05
okay

---

### Post by Cup2078 on 2012-09-05
Okay ive done all that, should i reboot?

---

### Post by Sanitylost on 2012-09-05
yes, you should get the gui login screen. It will look different than the original login screen, but your username and password are the same.

---

### Post by Cup2078 on 2012-09-05
nope still tty1 console login screen...

---

### Post by Sanitylost on 2012-09-05
Did something happen that precipitated the tty1 screen just appearing. Did you update a driver? Program? anything like that?

---

### Post by Cup2078 on 2012-09-05
Nope i just installed it on a secondary partition.

---

### Post by Sanitylost on 2012-09-05
Ok, so if this is your first install and you've never even used the actual linux system correct?

---

### Post by Cup2078 on 2012-09-05
I installed it in my old laptop, but i didn't use it much, so yes this is a first for me.

---

### Post by Sanitylost on 2012-09-05
It may be something as simple as a corrupted installation folder. It's a real annoyance, but sometimes it happens. If you're dual booting you can use wubi to install linux onto the open partition. Or you may need to create a new installation drive and reformat your hard drive. I would check around and see if anyone else has encountered this problem to try and avoid having to do that.

---

### Post by Cup2078 on 2012-09-05
i could try and wipe the partition and re-install it, you think that would work? i cant reformat because the windows side has really important files that i cant back up...

---

### Post by Sanitylost on 2012-09-05
I would look around, but it may be less frustration to just reformat the partition and use wubi, if you're using ubuntu, to install linux on to the partition, make sure you choose the correct partition because it will wipe your drive with windows on it if you're careless and tell it to.

---

### Post by angry_johnnie on 2012-09-05
Once your computer gets to the tty1 console, type

```
startx
```

and press enter.

It may complain if xinit is not installed.  You could also try:

```
sudo service lightdm start
```

and enter

or

```
sudo service gdm start
```

and enter.

---

### Post by Cup2078 on 2012-09-05
I get the error, disconnected from plymouth

---

### Post by Cup2078 on 2012-09-06
Okay im getting confused now, i wiped the partition and re-installed ubuntu and it worked from 2D mode in recovery, so i installed updated nvidia drivers and restarted, now it just boots to tty1 from recovery and regular mode!

---

### Post by oldfred on 2012-09-06
Which nVidia driver did you install. It often gives a couple of choices and your system needs the older one?

---

### Post by Cup2078 on 2012-09-06
The newest ones, umm the second option i picked the one that said i needed it to use unity.... im not sure what i selected.
it worked, kina on the default drivers except the display was shifted over to the lefr like a millimeter and some of the taskbar is chopped off and the console text nearest to the left is also chopped off.

---

### Post by Cup2078 on 2012-09-06
Okay im re-installing yet again!

---

### Post by angry_johnnie on 2012-09-06
What kind of video card do you have?  If it's an older nvidia card, you may need to use the legacy driver (96).

It's strange that the nouveau driver didn't work with it.

---

### Post by Cup2078 on 2012-09-06
Yeah its pretty old, GeForce 6150 LE.

Think i should try the legacy drivers? and if i should how do i install them?

---

### Post by angry_johnnie on 2012-09-06
If you're able to get to a 2d unity session or a low graphics mode, open software centre and look for nvidia 96, or see if the additional drivers applet offers it.

On the other hand, if it did work with the default nouveau driver, except for the issues you mention, try adjusting the display on the monitor itself.  Try adjusting size and position from the monitor itself, it may be just that.

---

### Post by Cup2078 on 2012-09-06
Okay im in 2D session, im just nervous that il eff it up again......

---

### Post by Cup2078 on 2012-09-06
okay its not there

---

### Post by oldfred on 2012-09-06
It looks like series 6 is supported by the standard nVidia driver.

But one version 295.40 released was bad. But my install now has 304.43, so that should not be an issue anymore.

NVIDIA 295.49 Fixes Linux Performance Regression
[http://www.phoronix.com/scan.php?page=news_item&px=MTA5NjQ](http://www.phoronix.com/scan.php?page=news_item&px=MTA5NjQ)
Fixing the performance regression of the 295.40 driver that affected GeForce 6 and GeForce 7 series hardware.

---

### Post by Cup2078 on 2012-09-06
Its running just fine in 2D mode, but its off center, here are some screens;

[http://imgur.com/98bTy](http://imgur.com/98bTy)

[http://imgur.com/AND39](http://imgur.com/AND39)

---

### Post by Cup2078 on 2012-09-06
Okay so now ive updated drivers to current edition, now i get a black screen of boot!!!! IDK WHAT WENT WRONG!

---

### Post by oldfred on 2012-09-06
Does recovery mode work? To at least get back to a command line?

---

### Post by Cup2078 on 2012-09-06
Yeah it goes back to the command line

---

### Post by oldfred on 2012-09-06
Can you try this, 

sudo apt-get --reinstall nvidia-current
sudo modprobe nvidia


gksudo nvidia-settings

---

### Post by Cup2078 on 2012-09-06
re install
E:Invalid operation nvidia-current
gksudo
(gksudo:2262): Gtk-WARNING **:cannot open display:

---

### Post by oldfred on 2012-09-06
You have to start gui before the gksudo command will work.

But the first is saying nvidia-current is not valid?

Try this:
sudo apt-get update
sudo apt-get remove nvidia-current
sudo apt-get remove nvidia-common
sudo apt-get remove nvidia-settings
sudo apt-get remove --purge nvidia-*

sudo apt-get install nvidia-current
sudo apt-get install nvidia-common
sudo apt-get install nvidia-settings

sudo apt-get update
sudo apt-get upgrade
sudo reboot

---

### Post by Cup2078 on 2012-09-06
Okay i did all that, its working to boot to tty1 on regular boot, but still not able to get GUI

---

### Post by oldfred on 2012-09-06
So we are back to where we were at post #1. Do you get any error messages, indicating something else is wrong? You can remove quiet splash from linux line in grub menu and try to see the lines scroll by for errors.

Did you retry 
sudo service lightdm start
or: gdm, lightdm, xdm, etc which ever is installed.

While your system should be ok for full Ubuntu, maybe there is something and you really need on of the lighter weight versions.

---

### Post by Cup2078 on 2012-09-06
ok when i booted up again to try those, it did the black screen thing then and i had to do CTRL+ALT+F1 to go to tty1

---

### Post by Cup2078 on 2012-09-06
Okay i tried to start lightdm and it didnt work, and this is the splash when starting up;

[http://imgur.com/WxT6f](http://imgur.com/WxT6f)

---

### Post by oldfred on 2012-09-06
It looks like it is loading. But I have no idea after that.

We can look in log files and see if any errors are reported.
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
dmesg is the one I look at first.
 sudo nano /var/log/dmesg
sudo nano /var/log/lightdm/lightdm.log

I look for out right errors, long times between entries, or some driver trying to load repeatedly and then failing.

Also if forcing shutdown remember the elephants.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by Cup2078 on 2012-09-07
here are some screens of the log files;
[http://imgur.com/67gAz](http://imgur.com/67gAz)
[http://imgur.com/HLlDT](http://imgur.com/HLlDT)
[http://imgur.com/6bXSX](http://imgur.com/6bXSX)
they where hard to take cause the files where so big.

---

### Post by oldfred on 2012-09-07
You can post screen shots with the little paperclip icon in the edit panel above.

This is my output:

```
[+0.01s] DEBUG: Launching process 1476: /usr/bin/X :0 -auth /var/run/lightdm/ro$
[+0.01s] DEBUG: Waiting for ready signal from X server :0
[+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/$
[+2.03s] DEBUG: Got signal 10 from process 1476
[+2.03s] DEBUG: Got signal from X server :0
[+2.03s] DEBUG: Connecting to XServer :0
[+2.03s] DEBUG: Automatically logging in user fred
[+2.03s] DEBUG: Started session 1571 with service 'lightdm-autologin', username$
[+2.11s] DEBUG: Session 1571 authentication complete with return value 0: Succe$
[+2.11s] DEBUG: Autologin user fred authorized
[+2.13s] DEBUG: Autologin using session gnome-fallback

```Yours just errors out, I cannot clearly read to to see if it says why. 

Did we try this?

sudo dpkg-reconfigure -phigh xserver-xorg

And if that does not work lets go back to the failsave version.
copy failsafe to xorg to use vesa as default, may need nomodeset again.
sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf

---

### Post by Cup2078 on 2012-09-07
sudo dpkg-reconfigure -phigh xserver-xorg didnt give any output, il restart and try the second option

---

### Post by Cup2078 on 2012-09-07
Okay even with nomodeset on it is still at a black screen after i select it from grub :/

---

### Post by oldfred on 2012-09-07
I do not understand why nomodeset is not even working. On my system I have to use nomodeset until I install nVidia driver.

You may need other boot options in addition to nomodeset, but I have no idea how users know which ones. Some experiments, others find similar systems and what they posted as to what works.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by Cup2078 on 2012-09-07
It seems to work in 2D mode if i re-install, do you think i should re-install and go from there?

---

### Post by oldfred on 2012-09-07
I would leave it in 2D mode then. 

Older systems do have issues with the 3D modes.

---

### Post by Cup2078 on 2012-09-07
okay, il re-install i know my graphics card can run 3D, it runs CSS and TF2 quite well, is there any hope for me to run 3D mode? and if there isn't is there a way to set 2D mode as default?

---

### Post by oldfred on 2012-09-07
I think I am running 2D and do not really notice much difference. I have gnome-panel or fallback. It is more like the old versions with top bar and menus.

Whichever you boot into at the login and select with the icon in the upper right corner of the login panel will be how it logins in every time until you change it.

---

### Post by Cup2078 on 2012-09-07
Okay thanks, im excited to start using ubuntu!

thanks for helping me fix this, i cant really figure out what else to do so im gonna make up words for how happy i am.... SPLENDUFFOROUS!

---

