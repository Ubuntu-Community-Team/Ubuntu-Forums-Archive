---
title: "GUI not loading, heeeeeeelp"
date: 2009-07-13
forum: General Help
---

### Post by pcgstudio on 2009-07-13
Hello,

I have a problem with my GUI not loading, it used to load and then i tried installing nvidia-glx from synpatics and then rebooted it removed a load of files but for some reason it wont go back to the gui

so i remove nvidia-glx and installed nvidia-glx-180 with envyng -t

when i do startx it goes to a black screen

prior to this i couldnt even get to install glx-180 as it said missing files in the modules and everything

but now i got past that, installed the driver, but still i cant get into the gui

xserver is installed too as well as core

---

### Post by pcgstudio on 2009-07-13
im not sure how to launch into recovery mode either, dont know how, even when i put the cd in doesn't give me that option, it just loads straight into the command line

---

### Post by Vakman on 2009-07-13
Okay. When you first turn on the machine and it starts to load the GRUB menu, it gives you by default about 3 seconds. During that time, press ESC and then it will allow you to choose recovery mode.  Then while in recovery mode, choose "xfix" and then after that choose resume normal boot. Let us know how that goes.

---

### Post by pcgstudio on 2009-07-13
i did recovery mode it goes through this massive list then says type your password or do ctrl d, i did both and it does nothing
it is still the terminal and i have to login
didnt load any graphical user interface

I also didn't see any option for xfix

btw using jaunty here 9.04

---

### Post by pcgstudio on 2009-07-13
is there anything i can type in to show a log so it can help identify the problem? i seriously have no clue what it is right now, if i cant even load the gui for recovery mode or for low graphics mode, seems to be quite a big problem for me :S

---

### Post by Vakman on 2009-07-13
There is no GUI for recovery mode. It is text based. But I am not sure why you did not see "xfix" option. When booting the computer, GRUB will start loading, press Esc to enter the GRUB menu and then choose recovery mode. It should bring you to a set of options, somewhere on that list should be "xfix". You said you used EnvyNG to install the drivers?

---

### Post by Vakman on 2009-07-13
Since you can get to the command line try this:
```
envyng --uninstall-all
```
then when that is finished just type reboot and that will restart the system.

---

### Post by pcgstudio on 2009-07-13
Thanks for the response,

I have done as you said, it restarted automatically i just put 0 and now its again back to the terminal

i typed glxinfo and it said unable to open display

---

### Post by Vakman on 2009-07-13
What do you mean you just put 0? 
An try
```
cd "pathtothenvidiainstaller"
```
then
```
sudo sh name_of_the_nvidia_installer --uninstall
```
If you do not know the path try this
```
sudo apt-get remove nvidia-glx
```

---

### Post by pcgstudio on 2009-07-13
Oh i meant that it automatically says press 0 to reboot so i did that.

I didn't know the path so i typed:
sudo apt-get remove nvidia-glx , wasn't installed
and sudo apt-get remove nvidia-glx-180, wasn't installed

---

### Post by Vakman on 2009-07-13
Now we would like the xserver to be back to default and worry about the actually driver installation afterwards.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Will reset the xserver back to it's default.
```
sudo /etc/init.d/gdm restart
```
Will restart the GNOME display manager.

---

### Post by pcgstudio on 2009-07-13
It says xserver is broken or not fully installed, i am guessing it did this after i uninstalled envyng

should i do sudo apt-get install xserver-xorg? first?

---

### Post by Vakman on 2009-07-13
In that case no.
Try ```
sudo apt-get install --reinstall x11-common xserver-xorg
```

---

### Post by pcgstudio on 2009-07-13
legeeeeeend! im back in thanks, now i need to install the drivers,

how would i install the right ones? what caused this in the first place was me trying to get higher than the resolution they offered.

I have an nvidia card 7600gt

---

### Post by Vakman on 2009-07-13
Aha, great. Oh and no problem, glad to help.
Now then xD
```
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.14/NVIDIA-Linux-x86_64-185.18.14-pkg2.run

```
then
```
sudo sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run
```
Try this :)

---

### Post by pcgstudio on 2009-07-13
am running an nvidia 7600gt, so pleased to see my desktop again lol i only just recovered 6gb of music after 5 years of not having access to it and linux got it back for me from my mp3. lol so pleased.

---

### Post by Vakman on 2009-07-13
Sorry, didn't realize you said it in the previous post. Look to my previous post for steps to install. I would be pleased as well lol.
Oh... don't follow what I just said :P 
That was for x64 if you have that great, if not then follow this
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/NVIDIA-Linux-x86-185.18.14-pkg1.run
```
```
sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run
```

---

### Post by Vakman on 2009-07-13
Let me know how that goes. The alternative is just to install the one in the restricted hardware driver section. not sure what version that is.

---

### Post by pcgstudio on 2009-07-13
I got an error on that package said thats for x86_64 platofmr and im running x86, do you have the source for the other? cheers

is it this one?

```
http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/NVIDIA-Linux-x86-185.18.14-pkg1.run
```

---

### Post by pcgstudio on 2009-07-13
i tried that and it says you seem to be running an xserver and then it failed?

"you appear to be running an X server; please exist X before installing."

---

### Post by Vakman on 2009-07-13
Yeah, the second one I sent will work. I sent it since I realized that I sent you the x64 version.
So to clarify 
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/NVIDIA-Linux-x86-185.18.14-pkg1.run
```
```
sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run
```
Is what you will want.

---

### Post by pcgstudio on 2009-07-13
thanks just trying that but it says I'm running X, how do i exit that?

edit its working now, i think just in the bluebit

okay thats installed just restarted gnome again

---

### Post by Vakman on 2009-07-13
Not sure what you mean there. Change of plans. Just open Firefox or whatever browser you use and navigate to [http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.14/NVIDIA-Linux-x86_64-185.18.14-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.14/NVIDIA-Linux-x86_64-185.18.14-pkg2.run) and then save the file. Then open a terminal and type ```
sudo sh nameofthefile.run
``` The easiest way would be to open the terminal and type sudo sh and drag the file to the terminal and it will enter the location automatically. A program that may be useful to you is one called App Runner. The link is [http://hacktolive.org/wiki/Runner](http://hacktolive.org/wiki/Runner) it will allow you to right click on any .run file and run it without you having to open the terminal. Check it out if you like. Anyway follow the steps above first :lolflag:

---

### Post by Vakman on 2009-07-13
Okay so you have the driver installed, I noticed you edited. 
Let's make sure they are installed.
```
glxinfo | grep direct
```
You should get a line back that says "direct rendering: yes".

---

### Post by pcgstudio on 2009-07-13
I'm restarting again but when i restarted gnome the highest setting i had for my screen was 640x480

trying what u posted above sorry didnt see it

---

### Post by pcgstudio on 2009-07-13
I tried the glxinfo | grep direct in the terminal in low graphics mode and it didn't give a return

---

### Post by Vakman on 2009-07-13
In low graphics mode? Why are we in low graphics mode xD
Did I miss something?

---

### Post by pcgstudio on 2009-07-13
When i restarted teh computer it said it was going to load in low graphics mode 

should i restart again and choose a diff option?

---

### Post by Vakman on 2009-07-13
Yes, if it is possible. So tell me what happened? Did you download the drivers off the site and then you went into terminal "sudo sh "nameofnvidiadriver""? And then restarted and it wanted you to boot into low graphics mode?
P.S. Low graphics mode will go to 640x480

---

### Post by pcgstudio on 2009-07-13
I was in the terminal and i went through the installation process using sudo sh, that installed,

I then told gnome to restart and i was then on the login so i logged in, however everything was huge 640x480

so i decided to restart as i thought it would read the new settings or something so i restarted and then it said ubuntu is running in low graphics mod which it has done again

it sayd your screen, graphics car, and input device settings could not be detected correctly.

its saying it again on the second restart

---

### Post by Vakman on 2009-07-13
Try this
```
sudo nvidia-xconfig
```
If not remove the driver, the way we previously have.
And run it again but this time```
sudo sh "nvidiadriverfile.run" --buildandinstallpkg Ubuntu/9.04
```
Not sure if you can do this with nVIDIA drivers but it is worth a shot.

---

### Post by pcgstudio on 2009-07-13
done that, now tried grep direct again:

NVIDIA: could not open the device file /dev/nvidiactl permission denied 
direct rendering: no 
if you want to find out why try setting libgl_debug=verbose

---

### Post by Vakman on 2009-07-13
So try this first to uninstall the driver 
```
sudo apt-get remove nvidia-glx
```
If not reset the xserver to the default. And then try
```
sudo sh "nvidiadriverfile.run" --buildandinstallpkg Ubuntu/9.04
```

---

### Post by pcgstudio on 2009-07-13
how do i reset the xserver to default? 

the driver uninstall said it was not installed so not removed?

sudo dpkg-reconfigure xserver-xorg
?

---

### Post by Vakman on 2009-07-13
Yes. ```
sudo dpkg-reconfigure xserver-xorg
```
Should do the trick. Then we will try the other way. But it said it was not installed meaning you didn't install it I suppose.
For the future to remove any drivers after they are actually installed we will use
```
apt-get purge nvidia
```
to remove any other nvidia drivers.

---

### Post by pcgstudio on 2009-07-13
It said "unrecognized option '--buildandinstallpkg'

---

### Post by Vakman on 2009-07-13
I figured as much. All right. Let see it didn't install earlier when you did it. Let's try EnvyNG again. This time let's choose the driver carefully.
So type
```
sudo apt-get install envyng-qt
```
Then just launch it from Applications > System Tools > EnvyNG
Then list the nVIDIA driver options.
Or we can just use the driver file with App Runner. Just to make sure it is done correctly we will download App Runner and then right click on the nVIDIA driver file and choose run as root.
There is a Howto in the forums for nVIDIA drivers but looks quite long just to install a driver. So we can try that later if this does not work.

---

### Post by pcgstudio on 2009-07-13
thanks the options i have are:

NVIDIA:
180.44-0ubuntu1 (used to have this but was not satisifed with the resolutions, it gave me a limited one and was disproportionate for my screen too so it looked all stretched)
173.14.16-0ubuntu1
96.43.10-0ubuntu1
71.86.08-0ubuntu1 but not compatible

---

### Post by Vakman on 2009-07-13
Which one did you use when xserver failed which we fixed eariler? I would like to say try 173.14.16-0ubuntu1 if that is what you did not use earlier.

---

### Post by pcgstudio on 2009-07-13
i used the top one 180 
just trying the runner right click-scripts-run-gui as root

but it cant install whilst imr unning cas it says i appear to be running an xserver please exit before installing

installed 173 with envy now restarting

---

### Post by pcgstudio on 2009-07-13
its restarted and now at 800x640 but i go to nvidia x server and it says you do not appear to be using nvidia x driver.

---

### Post by Vakman on 2009-07-13
Ah true, xserver must be off so you would have had to 
```
sudo /etc/init.d/gdm stop
```
to stop it. Either way you are using EnvyNG now. So let's see how that goes.

---

### Post by Vakman on 2009-07-13
All right, let's try the simple way. Click System > Administration > Hardware Drivers. And then click "Activate" and then it will need to be restarted. When you open that though just if there is a driver in there.

---

### Post by pcgstudio on 2009-07-13
trying that with version 173 downloading and installing atm, restarting

---

### Post by pcgstudio on 2009-07-13
nah its all massive and ugly wont load nvidia thing either will try 180 again :/

---

### Post by pcgstudio on 2009-07-13
so im on 180 now and its on 1024x768 but its not going higher and i cant load system >preferences> nvidia xserver from the system menu

i click on it and it doesnt load

---

### Post by Vakman on 2009-07-13
Open terminal
```
glxinfo | grep direct
```
Post back the response.

---

### Post by pcgstudio on 2009-07-13
it doesn't give me any response

---

### Post by Vakman on 2009-07-13
```
glxinfo
```
But just tell me up until this.
eg ```
thisislaw@Thisislaw-PC1 ~ $ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4

```
Your's will say nVIDIA (or should) and, yeah just post that for now.

---

### Post by pcgstudio on 2009-07-13
it returns segmentation fault?

---

### Post by Vakman on 2009-07-13
Whoa. I actually have not a clue to why it would do that. Maybe time to follow the long how to. Try this [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)
Post results. This one will probably take a little longer. I will also ask a friend of mine while you are doing this.

---

### Post by pcgstudio on 2009-07-13
lol that does look long will try that

---

### Post by pcgstudio on 2009-07-13
didn't work for me so im back on 180 and 1024x768 the refresh rate is so low, it looks horrible lol

---

### Post by pcgstudio on 2009-07-13
i cant seem to click on the nvidia settings it just wont load :S

if i type sudo nvidia-settings it gives me segmentation fault?

---

### Post by pcgstudio on 2009-07-13
now ive installed 185.18.14 and can load the nvidia settings
but how come it is still at resolution 640x480? any help with that please :D

---

### Post by pcgstudio on 2009-07-13
wahaaay its working now! fantastic :D thanks for the help knew linux would come back

---

### Post by Vakman on 2009-07-13
Yeah. There we go. It took 6 pages but it is working :)
Was beginning to wonder.
Remember to mark the thread as solved.
Enjoy :)

---

### Post by pcgstudio on 2009-07-14
Thanks yeah lol it did take a long while. not sure how to mark it as solved. checking

---

### Post by pcgstudio on 2009-07-19
the problem has respawned again, when i try to click on nvidia server settings it says i do not appear to be using the nvidia x driver.

just did 
cat /proc/driver/nvidia/version

and i definately have 185 according to that, and i did sudo nvidia-xconfig again and restarted...that hasn't done the trick either

When i start gives me an error on loading some nvidia kernel or something and then prompts to use low graphics mode,

---

### Post by pcgstudio on 2009-07-19
seems to be solved again reinstalled the driver, i think it was the kernel, one part of the installation said no kernel was found or something and it had to build one. so i guess maybe it was tht

---

### Post by pcgstudio on 2009-07-29
problem again, i cant get back into the gui, i was trying to fix the driver to get my nvidia to work, i accidentally uninstalled xserver-xorg using remove

but i reinstalled it, hwoever now i cant get get in...reinstalled the drivers and everything followed all these instructions you posted but didnt work still...

terminal is working

---

### Post by pcgstudio on 2009-07-29
bit more details, when i do gdm restart it does nothing doesnt attempt to load gdm

---

### Post by pcgstudio on 2009-07-29
ive tried everything numerous times, started in recovery mode, still nada

---

### Post by pcgstudio on 2009-07-29
i've fixed it, and back in :)

---

### Post by Vakman on 2009-07-30
Just remember to reset the xserver to default, it is
```
sudo dpkg-reconfigure xserver-xorg
```
From last time :P

---

### Post by gigaferz on 2009-07-30
hello, im in trouble right now, even after following several threads

anywyas, when you say "i fixed it"

what do you mean? and how exactly you did it?

---

### Post by Vakman on 2009-07-30
> **gigaferz said:**
> hello, im in trouble right now, even after following several threads
anywyas, when you say "i fixed it"
what do you mean? and how exactly you did it?
What is your problem, a new thread would be better but this will be fine. What is the problem you are having?

---

### Post by gigaferz on 2009-08-02
im running hardy, and i dont know why i decided to update.

so it broke everything. I have a 9600 gt.

  i think i just want to remove everything nvidia from my system then install new drivers.

Ive ben following this thread :

[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

i dont know what is wrong, but something i did notice in this case is this:

fer@fer-desktopQuad:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't findRGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

the card is detected by the system :
desktopQuad:~$ lspci | grep VGA
02:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)

dont worry anyways, its just too much anoyance, i guess ill have to reinstall again or maybe jump to the newest ubuntu.

so i did it , im in 9.04 or something, too much hassle, i mean dont get me wrong, i done stufff since 6.06 , but sometimes it becomes too exhausting

---

