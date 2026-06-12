---
title: "need help moving a created Xorg file. please help."
date: 2009-12-04
forum: General Help
---

### Post by black28 on 2009-12-04
hey guys, as you may have seen in many other threads i made i am still trying to get my resolution from 800x600 to 1024x768 and the problem is i have a out of date video driver. so i followed this walk through

[http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283](http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283)

if you notice "post #19" in the link it says 

> Copy and paste this stuff in, move the file over to /etc/X11/xorg.conf, "sudo chmod a+r /etc/X11/xorg.conf" just to be sure it can be read, reboot. Either you get your 1024x768 or it fails to load, in which case go to the shell and move /etc/X11/xorg.conf to /etc/X11/xorg.fail, then reboot again. This will probably work as it forces a resolution your monitor is known to work at, but nobody's perfect

i have created this new xorg file and made the changes. but how do i do what that says? i got the new xorg file saved on my desktop. i am almost done. can someone please assist me on this? i would greatly appreciate it.

---

### Post by audiomick on 2009-12-04
> **black28 said:**
> hey guys, as you may have seen in many other threads i made i am still trying to get my resolution from 800x600 to 1024x768 and the problem is i have a out of date video driver. so i followed this walk through

[http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283](http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283)

if you notice "post #19" in the link it says 



i have created this new xorg file and made the changes. but how do i do what that says? i got the new xorg file saved on my desktop. i am almost done. can someone please assist me on this? i would greatly appreciate it.

In the link you quote, there is the advice to change the permissions on the xorg file, so you can open it and write to it. That is this command:

```
sudo chmod a+r /etc/X11/xorg.conf
```

so, if you type that into the terminal, you should be able to edit the xorg file.

When I was messing around with my xorg.conf, I did it another way, which I prefer.

```

sudo gedit /etc/X11/xorg.conf
```

This opens the file /etc/X11/org.conf in the editor "gedit" with root privileges (sudo). You will be asked for your password.

I prefer to do it this way, as this leaves the permissions on the file unchanged. I don't like changing permissions on system files, as I don't know enough about it to know what is critical and what not, so I try and leave things as the makers intended.


When you have the file open, you can just paste the contents of your new file in.

I would suggest saving the existing file under another name somewhere else before you change anything.

Your video resolution is wrong, but at least the computer runs after a fashion. If your new file is badly enough wrong, you may not be able to start into the graphical desktop. If you have the old file, it is possible to copy it back in from the command line, and at least get back to where you are now.

---

### Post by pbrane on 2009-12-04
EDIT: follow audiomick's instructions.


Run a terminal and type:

**sudo cp ~/Desktop/xorg.conf /etc/X11/**

This assumes you have the file named **xorg.conf** and is on your Desktop.

If your file is not named xorg.conf then type 

**mv ~/Desktop/your_file_name ~/Desktop/xorg.conf**

then the first command.

Then type the command in the instructions, sudo chmod ...

---

### Post by audiomick on 2009-12-04
The suggestion from pbrane is also good, but still make a copy of the existing file first.

---

### Post by sdowney717 on 2009-12-04
use gui tools is better

gksu nautilus
opens file manager with super user privileges
just navigate around and open with gedit cut copy paste etc...

---

### Post by black28 on 2009-12-04
okay, so in terminal this is all it is doing....
> 
(username)-desktop:~$ sudo cp ~/Desktop/xorg.conf.new /etc/X11/
(username)-desktop:~$ sudo chmod a+r /etc/X11/xorg.conf
(username)-desktop:~$ 


the first tiime i typed " sudo cp ~/Desktop/xorg.conf.new /etc/X11/" it asked for password i put it in then it went to "(username)-desktop:~$ " 

so i typed in "sudo chmod a+r /etc/X11/xorg.conf" then it just went back to  "sername)-desktop:~$ "  

what is wrong? it's on my desktop saved as "xorg.config.new....

---

### Post by bit mad on 2009-12-04
The commands won't confirm that they've been successful, but it just goes back to the prompt again ready for another command. Try this to see if the copy worked, your file should now be amongst this lot
**ls /etc/X11/**

---

### Post by black28 on 2009-12-04
sorry im still newbish...how can i find that out?

---

### Post by black28 on 2009-12-04
okay, if you went through the link i got all this from, it says reboot when done...i did and nothing happend. still didnt check if it was in here ( /etc/X11/). those of you who are experienced and understand the walkthrough i posted can anyone help me through this? i've been trying to get my resolution higher for the last 3-4 days. lol. it's a Trident Microsystems Cuberblade Video Card, and i don't wanna buy a new one.... all help is greatly appreciated!

---

### Post by black28 on 2009-12-04
anybody?

---

### Post by ed-koala on 2009-12-04
sdowney717's suggestion is excellent.

in terminal, type :

```
gksudo nautilus
```

You can now edit/move/copy files as root graphically. Look around, move files where you need them, rename as you need, etc. Right clicking a file and choosing to open with gedit will edit with root privileges too.

---

### Post by black28 on 2009-12-04
okay, i tried>  gksu nautilus it asks for Admin password and then does nothing...any other suggestions please?

---

### Post by audiomick on 2009-12-04
The 
```
gksu nautilus
```
command should have opened the file manager (nautilus), same as when you click on the "places" menu, but with the difference that you have root privileges in that instance of it.

go to the xorg config file and see if it has got your new version in it. If it hasn't, save what is there to somewhere else for safety's sake, and copy the new one in there. The instructions to do this are all already in this thread.;)

---

### Post by black28 on 2009-12-04
my bad guys, i'm just really lost doing this. but okay, so the original xorg.config file is saved in a folder as a archive here: 

filesystem/usr/share/man/man5/xorg.conf.5.gz 

when i double click "xorg.conf.5.gz" it opens as a "read only" archuve creator file thing with xprg.config.5 in it. i have my "tweaked file" xorg.config.new file saved on desktop. i drag n drop it on the archive thingy and it asks to create a new archive. i click yes and navigate it's saving file all the way to "filesystem/usr/share/man/man5/xorg.conf.5.gz " and it can't because its a read only. it says i don't have permission. how can i get permission? also when i drag the xorg.config,5 file to desktop it creates a copy, but still without permission i cant do anything to the file in the archive thingy. *sighs* can anyone get me through this? sorry to ask so much....just wanna get the resolution and understand a little more. thanks.

p.s 
gksu nautlius doesnt open anything.

---

### Post by bit mad on 2009-12-04
That's weird, as an "Applications... Accessories... Terminal" command like this :
**gksudo nautilus /etc/X11/**
- should bring up the folder in a window marked "X11 - File Browser" and allow you see what's there, copy the desktop file xorg.conf there, and double-click it to view/edit it! :)

---

### Post by black28 on 2009-12-04
here goes...lol i'll update,

---

### Post by black28 on 2009-12-04
okay. **gksudo nautilus /etc/X11/ **in terminals does the same thing....ask's for admin password. typed it in and pushed Enter. it shows a on the toolbar "starting Administrative Applications" then terminal goes back to:
(username)-desktop:~$ and the "starting Administrative Applications" just disappears. any other options/suggestions?

---

### Post by audiomick on 2009-12-04
hallo.

Firstly, I must apologize for having made typing error (now corrected) in my last post. The command is not "nautlius", but rather

```
gksu nautilus
```

as Black28 had correctly posted it. Try it again, paying attention to the spelling. Your system would have to be fairly seriously broken for that not to work.


This 

> filesystem/usr/share/man/man5/xorg.conf.5.gz 

is **_not_** the  xorg.config file that your system loads at start, and therefore not the one you should be trying to change. This is an archive, possibly created automatically by the x-server. I don't really know.

Run

```
ls /etc/X11/
```

in a terminal, as has already been suggested.

You will see something like this:
```

mick@ubuntu-desktop:~$ ls /etc/X11/
app-defaults             X                                    Xresources
cursors                  xinit                                Xsession
default-display-manager  xkb                                  Xsession.d
fonts                    [COLOR="Red"]xorg.conf[/COLOR]                            Xsession.options
ja_JP.eucJP              xorg.conf.backup                     XvMCConfig
ja_JP.UTF-8              xorg.conf.dist-upgrade-200906041338  Xwrapper.config
rgb.txt                  xorg.conf.dist-upgrade-200911051538
mick@ubuntu-desktop:~$
```

"ls" means "list". This is a list of the contents of the folder "X11" which is in the folder "etc" which is right up a the top of the file system structure in "/".

This will be in blue, green and black, or something like that. The colours indicate whether the entry is a folder, a file or what have you.

I have highlighted what you need in red here. It is black in the terminal output.


So, if you have nautilus, the file manager, running from the "gksu nautilus" command, you need to go the the X11 folder in the etc folder. xorg.conf is in there, as "ls /etc/X11/" has shown us. 
Right click and open with gedit.
Make a safety copy, called whatever you want, e.g. in your normal documents folder.

Copy the contents of the new file over the contents of old file.


A way to do this:
right click on the new file, open in editor, select all and copy.

then

open the old file in gedit as described above, select all and paste.

If the "gksu nautilus" didn't work,
try it using

```
sudo gedit /etc/X11/xorg.conf
```

good luck. I have to go to work now, so wont be able to check back until tonight or tomorrow.

---

### Post by ed-koala on 2009-12-04
I'm thinking you might be the victim of a current Nautilus bug that is/has been recently fixed.  Try opening System Monitor (System - Administration - System Monitor) and scroll down the list. If you see Nautilus, highlight it and click End Process.

If you had one running, this might now allow the gksudo nautilus to open a new Nautilus.

(Actually, I doubt this is the problem, but it never hurts to check)

---

### Post by bit mad on 2009-12-04
What does this give you?
**nautilus --help**
Should be a list of command line options for calling nautilus from the command line.

---

### Post by black28 on 2009-12-04
checked system monitor and there wasnt anything... terminaled : **nautilus --help **and it said not installed (smacks forehead!) so it's installed now. and it opens this file browsing window after password showing desktop on open window with other folders... i'm guessing this is it obviously since nothing opened before. i'm gonna run through this and i'll update you guys on where it goes. thanks alot.

---

### Post by black28 on 2009-12-04
when i put in ls** /etc/X11/** in terminal this is the list it gave me. 

app-defaults             X           xorg.conf.new     XvMCConfig
cursors                  xinit       Xresources        Xwrapper.config
default-display-manager  xkb         Xsession
fonts                    xorg.conf   Xsession.d
rgb.txt                  xorg.conf~  Xsession.options

why are both xorg.conf and xorg.conf.new in it?

---

### Post by black28 on 2009-12-04
my xorg.conf file resolution part looks like this. it was originally 800x600. i tried 1440x900, and now going for 1280x720. i have a 19" samsung flat screen that i use for my ps3/linux pc now. i've re-booted after changing the xorg.conf file in etc/X11/ and nothing happens. if anyone knows if there is anything wrong please help. or be able to change the resolution higher than 800x600. its running a Trident Microsystems Cyberblade Video Card and the drivers are not supported. i've read about a "generic" driver for this card and something about vesa. thanks for all your help getting me this far. please let me know if you got any ideas...thanks


Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Depth        1
        Viewport 0 0
        Modes      "1280x720"
    EndSubSection
    SubSection "Display"
        Depth        4
        Viewport 0 0
        Modes      "1280x720"
    EndSubSection
    SubSection "Display"
        Depth        8
        Viewport 0 0
        Modes      "1280x720"
    EndSubSection
    SubSection "Display"
        Depth        16
        Viewport 0 0
        Modes      "1280x720"
    EndSubSection
    SubSection "Display"
        Depth        24
        Viewport 0 0
        Modes      "1280x720"
    EndSubSection
EndSection

could it be that the X11 file has both xorg.conf and xorg.conf.new? should i delete the xorg.conf.new?

or could it be that i do not have that "generic" driver installed and hardware driver shows no drivers?

---

### Post by bit mad on 2009-12-04
Well I'm glad we're getting somewhere.
*xorg.conf.new* is created by commands like these which try to set things up as best they can :-

[COLOR=Blue][COLOR=Sienna]Ubuntu :[/COLOR]
  sudo dpkg-reconfigure -phigh xserver-xorg
[/COLOR][COLOR=Blue][COLOR=Red]Other distros :
[/COLOR]  sudo X -configure
  sudo system-config-display --noui[/COLOR]

As for *xorg.conf* itself, we'll I've reached the limits of how I can help. I had trouble with my Dell and Intel Graphics *(hardly a rare combo I would have thought!)* because it wouldn't give me the option to go above 800x600 at a flickery refresh rate.

Given that the intel driver was supposedly installed and things really should have been working, I simply edited the *xorg.conf* file, looked for the Monitor and Screen sections, and replaced them with this general purpose wide range of sync frequencies and the rez options I wanted :

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       31-65
        VertRefresh     50-120
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
             SubSection      "Display"
                Viewport        0 0
                Depth           24
                Modes      "1152x864" "1024x768"
             EndSubSection
EndSection
```

For some reason this sorted it out, and finally allowed the display res changing dialog to control the res properly. It's such a general purpose setup that it might be worth trying, just add extra "NNNNxNNN" Modes to that line as you want. Good luck :)

---

### Post by black28 on 2009-12-04
yah man, i'm gonna try this out [http://ubuntuforums.org/showthread.p...Install&page=2]("http://ubuntuforums.org/showthread.php?t=806835&highlight=manual+TRident+Ubuntu+Install&page=2") it's referring to my vid card. when i first seen it i was like wth is that?! i never seen anything like that. buy after all you guys helping and playing around with it i get it pretty good now. lol i'm like what?! it's this easy? lol... but i'll update y'all if i succeed. thanks again for all the help.

---

### Post by bit mad on 2009-12-04
Good luck - setting up your screen properly can still be a right of passage, even with Ubuntu, it seems! ;)

---

### Post by black28 on 2009-12-04
ok. lol. something went wrong. changed the xorg.conf file again, and pasted this in...

> Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
  BusID "PCI:1:0:0"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  Option "DPMS"
  HorizSync 28-51
  VertRefresh 43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Trident Microsystems CyberBlade XPAi1"
	SubSection "Display"
		   Depth 8
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 16
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 24
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 32
		   Modes "1024x768"
	EndSubSection
EndSection

thats what i used. notice his is **Trident Microsystems CyberBlade XPAi1** mine is **Trident Microsystems CyberBlade il** i pasted and changed the names of the video cards. re-booted and now it shows the xubuntu loading screen then goes straight to shell mode asking for desktop and password and into sudo. thank god i made a back up. lol how can i restore that backup file through sudo?

---

### Post by bit mad on 2009-12-04
Presuming you have a backup copy in the same folder...
change to the right folder: **cd /etc/X11**
verify if you like: [B]pwd
sudo cp backup-xorg-conf xorg.conf

[/B]restart and cross your fingers :)

---

### Post by black28 on 2009-12-04
hmmm, i didnt put it in there. it's in the default documents somewhere in home or something on desktop. file named "xorg.conf Original" how would i navigate to that and load that? wait i have the working edited one saved on the desktop named as xorg.conf.new....how about this?

---

### Post by bit mad on 2009-12-04
There is another possibility, try some other distros on Live CD / USB keys, and if you find one that works well with your screen, copy the xorg.conf from there!
I vaguely remember Mandriva One gave me almost the right config, and I was going to try copying from that as my next attempt to get things working, but I got it going before I got to that point.

---

### Post by bit mad on 2009-12-04
> **black28 said:**
> hmmm, i didnt put it in there. it's in the default documents somewhere in home or something on desktop. file named "xorg.conf Original" how would i navigate to that and load that?

starting from the destination folder /etc/X11 you'll just need to include the path of the source folder,  i.e. /home/black28  if that's what you log in as, or /home/black28/Desktop/ for the desktop.

So the copy command becomes [COLOR=Red][I]**LIKE**
[/I][/COLOR]**sudo cp /home/black28/Desktop/backup-xorg-conf xorg.conf**

---

### Post by black28 on 2009-12-04
i burnt the whole Xubuntu 9.1 ISO to disc, i can re-install but it's pretty long. will do that if all else fails. can i recover from the cd? changing bios to boot cd and stuff?

---

### Post by black28 on 2009-12-04
tried "sudo cp /home/black28/Desktop/backup-xorg-conf xorg.conf"  
   & 
"sudo cp /home/black28/Desktop/backup-xorg-conf xorg.conf.new"

the file on desktop is xorg.conf.new didnt work though. both say no such file or directory.

---

### Post by bit mad on 2009-12-04
Do you log in as **black28** then? You have to replace that bit of the command with your login name, and the final parts of the command should be  **/xorg.conf.new xorg.conf**
- so that it copies  **xorg.conf.new** in **/home/yourlogin/Desktop** to become** xorg.conf** in **/etc/X11/ **where you've issued the command from.

So, something like
**sudo cp /home/[COLOR=Red]joebloggs[/COLOR]/Desktop/****xorg.conf.new**** xorg.conf**

---

### Post by black28 on 2009-12-04
i did put my user name in, but just kept putting different files and stuff and i kept saying no such file or directory, i re booted and it started in "low graphics mode" which actually looks like how i had it before just really really sluggish.

---

### Post by bit mad on 2009-12-04
Should have worked, presuming you log in as one word (like **JoeBloggs**) - if it's got spaces in (like **Joe Bloggs**) then you'd probably have to put " quotes around the path and filename combo, or else it will get confused by the space in [B]
/home/Joe Bloggs/filename[/B] 
and would need to be 
**"/home/Joe Bloggs/filename"** I presume - that's what happens in Windows :)

So you've got back into the graphical desktop and can copy the files the easy way again?

---

### Post by black28 on 2009-12-04
got it. yah, it kinda booted up in a windows "safe mode" slow but gets the job done. so it's back to what i had before. but i think theres still some graphics issues. when i first log in it kinda flickers and shows my xorg.conf backup flie i have on the desktop and then refreshes to the real desktop. and shut downs it'll clear the desktop and show my homepage on firefox.

---

### Post by sdowney717 on 2009-12-04
if you have a space, you have to escape it with a '\'

say i have a folder named 'fup pes'
just typing it in wont find it

scott@scott-desktop:~$ cd fup pes
bash: cd: fup: No such file or directory

so then put '\' and it finds it.

scott@scott-desktop:~$ cd fup\ pes
scott@scott-desktop:~/fup pes$

---

### Post by bit mad on 2009-12-05
> **sdowney717 said:**
> if you have a space, you have to escape it with a '\'


Thanks. But "quotes work" too. I created a folder called space name
in my home folder, with a test file in it. 
**ls "space name"** showed the file, and **cd "space name"** worked too.

Cheers :)

---

### Post by black28 on 2009-12-09
okay, hey guys/...been a while now since my PC was having RAM issues!! well i got another desktop today. its a HP Vectra VL400 MT. i did some swaps and brought my old 60GB HDD that i had in the 521c runnung Xubuntu, but re-installed it again. Xubuntu 9.1. so i FINALLY got that screen Resolution i wanted! but now some wired things are that i can't install Nautilus and Flash Plugins using Terminal. it says packages are not there.can anyone explain what' going on?

---

### Post by black28 on 2009-12-09
Also, it seems as if my desktop sits, it kinda goes in to a blank screen after a while kinda like a screen saver or hibernation...then after moving the mouse it is REALLY Slow. can someone tell me how to edit power options on a desktop Xubuntu 9.1? all help is greatly appreciated.

---

### Post by bit mad on 2009-12-09
No idea... but I'd recommend starting a new thread for that :)

---

### Post by black28 on 2009-12-09
lol. so far so good. i found the "Control Panel" of linux, i just turned the Power Options down to never. you wouldnt happen to know anything about my new thread would you? 

 [http://ubuntuforums.org/showthread.php?p=8469231#post8469231](http://ubuntuforums.org/showthread.php?p=8469231#post8469231)

man i love this Resolution!

---

