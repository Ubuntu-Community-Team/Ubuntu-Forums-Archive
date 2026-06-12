---
title: "Script only does anything when launched in Terminal"
date: 2011-12-27
forum: General Help
---

### Post by Cadeyrn on 2011-12-27
UPDATE: This problem has been going through a very large rabbit hole. HP users, read to possibly get your touchscreen, pen eraser, and pressure sensitivity fully working. Screen rotation is still an iffy for me, but you might get it working from the text in here.


I have two scripts that I got from the Ubuntu Wiki to make my HP Touchsmart tm-2 screen automatically rotate when I move the monitor into tablet mode. The scripts work perfectly when I run them through the Terminal, but if I double-click them, use a shortcut I made for them, or set them to launch at boot, they run just fine, but they do nothing. The scripts are attached.

FULL DETAILS:
-Scripts are not .txt (I had to add it to upload them)
-Scripts are owned by root:root with 644 permissions
-Scripts are in /usr/local/bin and launch fine without sudo and with or without typing out the full path
-In KDE's startup settings, I've tried having auto-rotate be a script (with and without the full path typed out), and I've tried having it be a program (with and without the full path and sh typed out)
-I've tried having rotate-display (left, half, right, etc) be shortcuts with and without the full path typed out

I'm completely baffled by this. I've had shell scripts run at start plenty of times, and this is the first time it hasn't worked.

---

### Post by sepo on 2011-12-27
The only thing I can see is the missing interpreter ```
#!/bin/sh
``` at the first line.
Sometimes I add some kind of log to my scripts, to see how they're running (echo ...>log.txt)

ADDED:
And surely let's play with permissions: only root can execute the script with a 644

---

### Post by Lampi on 2011-12-27
just some thoughts after looking at the files and your post:

644 rights: it's not enough, you need 755 for executables (rwx-rx-rx)
also make sure you chown executables in /usr/local/bin to root:staff
both scripts are missing the shebang (#!/bin/bash, #!/bin/dash or #!/bin/sh)

the last one should be the root cause why everything is failing on autostart, but not when you invoke it in a terminal

---

### Post by Favux on 2011-12-27
Hi Cadeyrn,

If you are using Oneiric you can dispense with the eraser lines.  Oneiric has xf86-input-wacom-0.11.0 as the default.  However with Natty or Oneiric you will need to fix the Portrait orientation rotation bug by updating your xf86-input-wacom.

Also Magick Rotation should work for you if you are interested:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation) - has FAQ for fixing Portrait rotation bug
General tablet PC rotation info.:  [http://ubuntuforums.org/showpost.php?p=6274392&postcount=1](http://ubuntuforums.org/showpost.php?p=6274392&postcount=1)

---

### Post by Cadeyrn on 2011-12-27
Favux: Synaptic isn't finding a package with "xf86-input-wacom" in its name. I found a wacom package my computer has installed that "rotates the stylus and multi-touch screen along with the display". That explains why my screen can rotate perfectly even though I read somewhere that the touch screen doesn't rotate.

Thanks to sepo and Lampi's suggestions, the script now runs at startup fine, but now the rotate-display script is giving me unexpected operator errors with any of its variables. An example:

```
$ rotate-display half
[: 24: half: unexpected operator
[: 24: half: unexpected operator
[: 24: half: unexpected operator
Rotating to: normal (NONE)
```

I tried reverting any and all changes sepo and Lampi had me make, but it just doesn't work, despite that it did before.

---

### Post by Favux on 2011-12-27
Sorry, Ubuntu calls the xf86-input-wacom package xserver-xorg-input-wacom, like it did with the old linuxwacom package.  Do you mind telling us what release of Ubuntu you are using?  That would be helpful.
> I found a wacom package my computer has installed that "rotates the stylus and multi-touch screen along with the display".
Could you provide a little more information on this?  I don't know what it is or what you mean.

---

### Post by Cadeyrn on 2011-12-27
I'm running Natty, and the package I found and mentioned in the last post is in fact xserver-xorg-input-wacom. I'll try updating that from 0.10.11 to 0.11.0 and report back.

EDIT: I found a PPA and installed 0.11.99. Thanks for the tip, because now my eraser works! Sadly, screen rotating still doesn't, with or without the scripts.

P.S. Pressure sensitivity also still doesn't work, though GIMP can recognize and configure it. Does my screen not have pressure sensitivity? I'm not sure.

---

### Post by Favux on 2011-12-27
Which PPA?  Anyway 0.11.99 has the Portrait bug fix, it was submitted a couple of commits prior to the 0.11.99 tag.  So you should be good there.

What is the output of:
```
xinput list
```
in a terminal?  And also?:
```
xsetwacom list
```
Yes, you should have 256 levels of pressure.  Are you changing the stylus to screen in Gimp's extended input device?

---

### Post by Cadeyrn on 2011-12-27
The PPA is [https://launchpad.net/~irie/+archive/wacom](https://launchpad.net/~irie/+archive/wacom)

The output is:
```
$ xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Finger touch               id=9    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=12   [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Pen stylus                 id=14   [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Pen eraser                 id=15   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; HP Webcam                                 id=10   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=11   [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                            id=13   [slave  keyboard (3)]
$ xsetwacom list
Wacom ISDv4 E3 Finger touch             id: 9   type: TOUCH     
Wacom ISDv4 E3 Pen stylus               id: 14  type: STYLUS    
Wacom ISDv4 E3 Pen eraser               id: 15  type: ERASER
```

Could this be related to the unexpected operator errors I was suddenly getting?

Yes, the stylus is set to Screen. After reading your post, I tried setting it to Window, but that didn't make the pressure sensitivity work.

---

### Post by Favux on 2011-12-27
Irie's PPA is getting a little old because he hasn't updated it in a while.  But you should be OK.

I suspect your problem is that you don't yet have the rotate-display file working correctly.  Either the interpreter (shebang), permission, or auto-start.  You're not using the automatic part, the auto-rotate file yet, correct?  Because you are using *rotate-display half*.

You don't want to use Magick Rotation?  If not I'd rather use Red_Lion's original auto-rotation script.  That's method 2 in the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  I suspect that is what your current scripts, the auto-rotate part anyway, is based on.  I really don't want to debug it because while I understand what the author was doing I find it overly complicated.  I don't see a reason to use *xinput list* or ultimately to have it split in two files.  Even though it lets you just put the *rotate-display half* command in a launcher or another rotation direction in a another launcher.  And I don't agree with telling you to install these two files in /usr/local/bin.  The reason that is needed is so the *rotate-display direction* command works without specifying the path.

Either way, Magick Rotation or Red_Lion's script, you'll want to install CellWriter.  Xournal while you're at it.

Pressure is a bit of a puzzle.  It could be hardware like a damaged nib.  Are you able to show pressure in say Windows?

---

### Post by Cadeyrn on 2011-12-28
Went to Windows 7 x64 with all drivers installed, and Windows Journal had a setting to enable pressure sensitivity. When I did, it worked fine. And as I mentioned before, GIMP can see that my hardware supports pressure sensitivity, but it acts like the setting is disabled or something. Perhaps the next step is to see some raw data to find out if Linux sees the pressure sensitivity. How would I do that? I imagine it's some kind of Terminal command? I'd check the Input Devices configuration for a calibration check, but it doesn't know I have a touchscreen (even though my entire system knows).

As for screen rotation, Windows didn't want to rotate, either. When I entered tablet mode, it just faded an icon on and off the center screen of a finger on a touchpad and a red X. I'm going to try Magick Rotation next, because those two scripts still won't work when I revert the files back to the way they were when they did work (delete interpreter, 644, owned by my user and group).

EDIT: Aha! Pressure sensitivity works in Xournal. So it's an issue with GIMP. I'll google it.

---

### Post by Favux on 2011-12-28
Alright, so something weird is going on with pressure.  To get raw data on an input device use evtest:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Evtest](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Evtest)

For any of these auto-rotation methods to work you need wmi, and hp-wmi auto-loading.  So check:
```
lsmod
```
in a terminal and make sure they are in there.


Edit:  Ah, Gimp specific.  Hopefully we can deal with that.

---

### Post by Cadeyrn on 2011-12-28
Googling the GIMP issue did nothing. I did find two people with my problem, but neither of them got any help. One was told that either their hardware is damaged, their GTK isn't set up for sensitivity, or their drivers are not properly installed, but since Xournal works fine, none of those can apply to me.

Magick Rotation can't rotate the screen, and I think it can't even tell that I'm going into tablet mode, because if I put a command into "Run before switch to tablet", it doesn't run. That would be Magick Rotation's fault, as the scripts can tell that I'm entering tablet mode; they just can't rotate the screen.

EDIT: Tried magick-rotation in the Terminal, and even with a -v, but I'm getting no terminal output when I (try to) rotate the screen or enable/disable the touch screen.

---

### Post by Favux on 2011-12-28
Do you see pressure in MyPaint also?

Did you check for hp-wmi in lsmod?

---

### Post by Cadeyrn on 2011-12-28
Pressure works in MyPaint as well. It's definitely a problem with GIMP. You're showing me a lot of awesome programs.

---

### Post by Favux on 2011-12-28
Well least I can do while we struggle with rotation.

What video chipset do you have?
```
lspci | grep VGA
```
If Nvidia are you using the proprietary driver?

---

### Post by Cadeyrn on 2011-12-28
I'm on Intel HD graphics. Unlike every other Touchsmart tm2, this one does not have a problematic [with Linux] ATI card--just the Intel graphics. Here's the output:

```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

I did have the NVidia proprietary driver installed at one point because I copied this installation from my old laptop, but I've already fixed all of my graphics drivers up (including uninstalling the NVidia one) to fix other issues I had in the past. I doubt that matters much, since the rotation worked and then stopped working without me touching the NVidia driver packages.

---

### Post by Favux on 2011-12-28
lol  You lucked out by not having the ATI videochipset too, for sure.

OK, some of the early Intel videochipsets needed the:
```
Option "RandRRotation" "on"
```
in the xorg.conf too.  But that shouldn't be an issue with yours.

---

### Post by Cadeyrn on 2011-12-28
I'm running the last tm2 they made before switching to iPad clones, but I'll try adding that anyway.

EDIT: It didn't help, but just now I tried changing the screen orientation with KDE's display settings, and it worked. The scripts and Magick Rotation still don't work, but at least now I have a temporary solution until we fix it, and proof that the screen isn't borked.

Here's a note: when I change the screen rotation manually, Rotation Magick automatically hides and shows CellWriter. So it can detect the screen rotation. Still iffy on whether it can detect tablet mode.

---

### Post by Cadeyrn on 2011-12-29
I found the xrandr -o [inverted, normal, left, right] command and made shortcuts on my panel, so now I have a manual screen rotation setup that's just as easy as an automatic one. As for the pressure in GIMP, I don't know if we'll be able to fix that. If I never do, at least now I can use MyPaint to draw the things and then paste them in GIMP.

Thanks for all the help. You've been amazing. I suppose if you still have more ideas, we can continue this.

---

### Post by Favux on 2011-12-29
Sure.  We need to do some more diagnostics.

Assuming you are seeing hp-wmi in the lsmod output go ahead and run this command in a terminal with screen in laptop:
```
cat /sys/devices/platform/hp-wmi/tablet
```
and then again when the screen is rotated to tablet:
```
cat /sys/devices/platform/hp-wmi/tablet
```
Then run again when back in laptop.  The outputs should be something like 0,1,0, post them.

---

### Post by Cadeyrn on 2011-12-29
Yay, my tablet mode sensor isn't broken!

```
$ cat /sys/devices/platform/hp-wmi/tablet
0
$ cat /sys/devices/platform/hp-wmi/tablet
1
$ cat /sys/devices/platform/hp-wmi/tablet
0
```

---

### Post by Favux on 2011-12-29
Yep, that be a swivel hinge signal for sure.  So you should be able to at least use the Method 2 automatic rotation script.

Now check in /etc/udev/rules.d.  Is there a file called 62-magick.rules?  Are there contents in it, i.e. it isn't empty?  Magick Rotation should have installed it.

---

### Post by Cadeyrn on 2011-12-29
It's there and not empty.

```
# Magick Rotation's udev rules for tablet PC's using an OEM-WMI or OEM-ACPI
#
# These rules were compiled for the Ubuntu/Debian GNU/Linux distribution, but others may,
# and indeed are encouraged to, use them also.
#
# Should you do so, PLEASE CO-ORDINATE ANY CHANGES OR ADDITIONS to 62-magick.rules with
# Jayhawk so that we can present users with a standard set of device nodes which they
# can rely on.

KERNEL!="event[0-9]*", GOTO="magick-rotation"

SUBSYSTEM=="input", ATTRS{name}=="HP WMI hotkeys", MODE="640", GROUP="magick", SYMLINK="input/magick-rotation"
SUBSYSTEM=="input", ATTRS{name}=="Dell WMI hotkeys", MODE="640", GROUP="magick", SYMLINK="input/magick-rotation"
SUBSYSTEM=="input", ATTRS{name}=="ThinkPad Extra Buttons", MODE="640", GROUP="magick", SYMLINK="input/magick-rotation"

LABEL="magick-rotation"
```

Oh, I missed that link you posted on page 1. I have to drive for a few hours right now, but I'll try these new methods soon.

---

### Post by Favux on 2011-12-29
That looks good so far.  So let's make sure the symlink that should be is established is working and that the TM2t is putting out usable output.  When you get a chance in a terminal enter:
```
sudo evtest /dev/input/magick-rotation
```
Starting with the screen in laptop again swivel to tablet and back to laptop.  Use ctrl-c or ctrl-z to exit.  You should see output like:
```
Input driver version is 1.0.0
Input device ID: bus 0x19 vendor 0x0 product 0x0 version 0x0
Input device name: "HP WMI hotkeys"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 138 (Help)
    Event code 148 (Prog1)
    Event code 153 (Direction)
    Event code 224 (Brightness down)
    Event code 225 (Brightness up)
    Event code 226 (Media)
    Event code 358 (Info)
  Event type 5 (?)
    Event code 1 (?)
    Event code 5 (?)
Testing ... (interrupt to exit)
Event: time 1292260147.412318, type 5 (?), code 1 (?), value 1
Event: time 1292260147.412360, -------------- Report Sync ------------
Event: time 1292260151.669418, type 5 (?), code 1 (?), value 0
Event: time 1292260151.669457, -------------- Report Sync ------------
```
The part we're primarily interested in is:
```
Testing ... (interrupt to exit)
Event: time 1292260147.412318, type 5 (?), code 1 (?), value 1
Event: time 1292260147.412360, -------------- Report Sync ------------
Event: time 1292260151.669418, type 5 (?), code 1 (?), value 0
Event: time 1292260151.669457, -------------- Report Sync ------------
```
Which should appear after you rotate the screen.  But post the whole thing please.

---

### Post by Cadeyrn on 2011-12-30
Confirmed, Magick Rotation won't notice tablet mode.

```
$ sudo evtest /dev/input/magick-rotation
Input driver version is 1.0.1                                               
Input device ID: bus 0x19 vendor 0x0 product 0x0 version 0x0                
Input device name: "HP WMI hotkeys"                                         
Supported events:                                                           
  Event type 0 (Sync)                                                       
  Event type 1 (Key)                                                        
    Event code 138 (Help)                                                   
    Event code 148 (Prog1)                                                  
    Event code 153 (Direction)                                              
    Event code 224 (Brightness down)                                        
    Event code 225 (Brightness up)                                          
    Event code 226 (Media)                                                  
    Event code 240 (Unknown)                                                
    Event code 358 (Info)                                                   
  Event type 4 (Misc)                                                       
    Event code 4 (ScanCode)                                                 
  Event type 5 (?)                                                          
    Event code 1 (?)                                                        
    Event code 5 (?)                                                        
Testing ... (interrupt to exit)
```

It never gave more output when I switched modes a few times.

---

### Post by Favux on 2011-12-30
Thanks for doing that Cadeyrn!  That seems to be an important finding.  The hp-wmi.ko should be reporting the mode, laptop or screen, both ways.
> Confirmed, Magick Rotation won't notice tablet mode.

Correct, because Magick now reads the type 5 Event key value 0 or 1 from "HP WMI hotkeys".  And what evtest is showing us is that for some reason the hp-wmi.ko on the TM2t no longer provides that key value although it does still have the Event type 5, i.e. tablet mode switch.  It just isn't supplying us actual information.  That's why you aren't seeing the extra output when rotating the screen.

Magick used to read the /sys/devices/platform/hp-wmi/tablet, and that part is still working.

We had TM2t's reporting Magick worked for them.  But recently several, including you, said it isn't working.  I thought we had reports of it still working after we changed to reading "HP WMI hotkeys" but perhaps I am mistaken?  I don't think I've ever had enough follow up with diagnostics to figure that out at this point.

The only thing I'm coming up with right now is this is likely a BIOS problem.

What you could do is check what BIOS version you have and its date.  It would also help if you checked HP's site and see what BIOS versions and their dates are out there.  It is possible you have a BIOS that was partly broken and a more recent one would fix things.  Or perhaps it is the other way around and more recent BIOS's broke things.  So it would be helpful to have an idea on the BIOS situation.

It is possible that the hp-wmi.c just needs a little adjustment to the code to get things working again.

I'll need to digest this a bit.  Ouch.  :(

---

### Post by Cadeyrn on 2011-12-30
I'll try the other methods. I'd rather not risk updating my BIOS when I already have buttons for rotating the screen.

---

### Post by Favux on 2011-12-30
Sure I can understand that.  But I would still appreciate it if you could tell me your BIOS version and the date it was released.  That would start giving me something to work with.

I'd like to point out you could still use Magick Rotation if you wanted to.  It would just have to be version 1.1 or earlier.  And for Natty and Oneiric you'd have to manually whitelist it so its icon appears in the system tray.

---

### Post by Cadeyrn on 2011-12-30
Here's the BIOS version I'm running:

```
$ sudo dmidecode --type 0
# dmidecode 2.9
SMBIOS 2.6 present.                                                         
                                                                            
Handle 0x0000, DMI type 0, 24 bytes                                         
BIOS Information                                                            
        Vendor: Insyde                                                      
        Version: F.25                                                       
        **Release Date: 02/18/2011**                                            
        ROM Size: 2048 kB                                                   
        Characteristics:                                                    
                PCI is supported                                            
                BIOS is upgradeable                                         
                BIOS shadowing is allowed                                   
                Boot from CD is supported                                   
                Selectable boot is supported                                
                EDD is supported                                            
                Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)  
                Japanese floppy for Toshiba 1.2 MB is supported (int 13h)   
                5.25"/360 KB floppy services are supported (int 13h)        
                5.25"/1.2 MB floppy services are supported (int 13h)        
                3.5"/720 KB floppy services are supported (int 13h)         
                3.5"/2.88 MB floppy services are supported (int 13h)        
                8042 keyboard services are supported (int 9h)               
                CGA/mono video services are supported (int 10h)             
                ACPI is supported                                           
                USB legacy is supported                                     
                BIOS boot specification is supported                        
                Targeted content distribution is supported                  
        **BIOS Revision: 15.25**                                                
        Firmware Revision: 131.32
```

Glad I was about to help you fix a bug. I think I'll start using 1.1, then. Also, my service manual and the HP Customer Care site for my laptop don't have a BIOS version anywhere, so I don't think we'll find a control group here.

EDIT: Aaaaaaand it works.

---

### Post by Favux on 2011-12-30
Good!

Thanks for the BIOS info.  Now I have a version number and date as a baseline.

So the HP TM2t BIOS:
```
        Version: F.25                                                       
        Release Date: 02/18/2011
```
does not supply hinge switch info. through "HP WMI hotkeys".

---

### Post by cbe665 on 2012-02-07
hey, sorry if im late to the party, but i have the same machine and a couple scripts that i had modified from here and there around the web. they work great for me as far as handling rotation and auto rotation. i used xmodmap to map the button on the side of the screen(keycode 161 on mine) to f13(mapping it to rotatewindows made my system crash when i tried to use it) and told my desktop manager to run the command "rotate ccw" when pressed. i also added auto-rotate to my startup programs, and set permissions on both to 755. These scripts make Linux handle rotation the same way it was in windows, including turning off the keyboard and touchpad when in tablet mode(saves power and reduces the amount of heat produced. Also, prevents accidental keypresses) and opens cellwriter when orientation isn't normal(waay better than the win7 onscreen keyboard) Still some tweaks I intend to make, and will post when done if anyones interested. I had a question about brightness on boot, but that doesn't belong in this thread.

---

### Post by Cadeyrn on 2012-02-07
Thanks! I would use these, except I've grown rather fond of the Magick Rotation set-up I have because my touch screen doesn't turn off when I close the screen, and on my desk I have my desktop and its keyboard set up behind my laptop, so my left arm tends to rest on the laptop when I use the desktop. Magick Rotation's click-to-disable-touch-screen feature is completely essential. I don't know how I lived without it, constantly accidentally shutting down my laptop and such.

---

### Post by Favux on 2012-02-08
Hi cbe665,

Welcome to Ubuntu forums!

Thanks for sharing the scripts.  Wow rotate.sh is fancy!
> including turning off the keyboard and touchpad when in tablet mode(saves power and reduces the amount of heat produced.
That is a good idea.  Why not in the automatic rotation script too?

One word of caution though.  I tend not to use ID # in scripts because they can change, usually when another usb device is plugged in.  So "device names" are preferable because they don't change.  But not much of a problem, obviously, with a tablet PC.

---

### Post by cbe665 on 2012-02-08
Ah. I hadnt considered that they might change, but if they stay the same then it should work on the touchsmart tm2. I actually hadnt thought of using device names instead, and supposed if it didnt match up with someones devices, they could edit the script as needed for their machine, but if i can make it more efficient, then thats all the better. I didnt turn off the keyboard and touchpad in the auto rotate because it calls the rotate script, but i actually need to move those to the auto rotate because it didnt dawn on me until after i posted that sometimes i use the laptop in portrait while open, like an actual notebook. Also, i found that once you use the rotate button, the auto-rotate script stops working, but i think that should take care of itself if i make the scripts independent of each other. So, the scripts still need work, but thats just as they were when i posted them. Like i said, if theres interest among tm2 users, ill post updates later. Actually, i need to get some work done today, but after work ill tinker some more

---

