---
title: "nVidia Drivers"
date: 2011-04-20
forum: General Help
---

### Post by Miykel on 2011-04-20
G'Day;  I'm running Ubuntu 10.10 and have a new Gigabyte VGA card which requires nVidea drives, all good, download and activate then reboot, no good, end up at a dos like screen, or terminal type of screen, enter commands etc. but no GUI, with out the nvidea drivers the display only occupies about 80% of the screen at max resolution setting, the drivers are  GeForce GT440, any thoughts would be appreciated.
  Kind Regards Miykel

---

### Post by realzippy on 2011-04-20
Which driver version did you install?
(can't find one for your card..)

270.26 supports:
GeForce 400 series:
GTX 465, GTX 460, GTX 460 SE, GTX 470, GT 430, GTS 450, GTX 480

---

### Post by HappyLinux on 2011-04-20
Please check out my thread for a possible solution on this matter.

[http://ubuntuforums.org/showthread.php?t=1669256](http://ubuntuforums.org/showthread.php?t=1669256)

---

### Post by realzippy on 2011-04-20
*Please check out my thread for a possible solution on this matter.*


you run a GTS 450,OP a GT 440...

---

### Post by Miykel on 2011-04-20
G'Day guys and thanks for the replies;

    Realzippy ;  Could you explain a little as to what you mean by " you run a GTS 450. OP a GT440" please.
    I got the drivers using   "System/Administration/Additional Drivers", so I can only suppose they are the correct drivers and latest version.
  Kind Regards  Miykel

---

### Post by realzippy on 2011-04-20
Thought you might had installed a manually downloaded beta-driver from
the nvidia "choose-your-driver-page":
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
..which could have caused your boot problem since some kernel modesetting
(disabling default nouveau-driver) is necessary when manually installing
a nvidia-driver.
But you installed with Additional Drivers tool,so this is done automatically.
According to Nvidia there is no valid driver for your card;
the GTS 450 is supported,the GT 440 is not.
Suggest you some googling  [I]linux + GT440
[/I] or ask Nvidia  about not listed driver.....
....to "restore " system (if not already done),boot in recovery mode ("shift" during boot),low graphics option,uninstall driver.
Then you could also have a look at your log-files. (Xorg.0.log/Xorg.1.log),maybe there is a hint..

Btw,what happens when you log in at the "dos-like-shell" with username+password,and type:

```
sudo nvidia-xconfig
```
and
```
startx
```
?

---

### Post by Miykel on 2011-04-20
G'Day  Realzippy;  It seems very odd when the drivers were installed through the additional drivers tool, I assumed that was the best way to go, however, I do believe the drivers are new so possibly they are not yet suitable for linux, but at the nVidea sit it shows Linux drivers for this VGA, must look further.
   I had no idea about the shift key during boot into recovery or the codes to uninstall the drivers, the only thing I was able to do in the DOS screen was to log in and type  sudo reboot to get out of it, I then booted into W& and deleted the partition and reloaded the OS.
    Is it possible the  additional drivers tool selected the wrong drivers  ???
Kind regards  Miykel

---

### Post by SeijiSensei on 2011-04-20
Reboot, then log in with your username and password and run 

```

sudo nvidia-xconfig
[Enter your password when prompted]
startx

```

If it fails, copy the errors that you see on the screen and post them here.

---

### Post by Miykel on 2011-04-20
G'Day again guys,  well no luck,  I tried those codes in the DOS screen but no help, went to recovery mode with shift key >> run in failsafe graphics mode, and got into the OS, went to installed software and uninstalled the nvidia drivers ( I think ) but after reboot back to DOS screen, damn. I like to get to the bottom of this just for the sake of learning something new, while I was in the OS I tried to get a log of the fault but have no idea how to I tried  /etc/x11/xorg.conf  but was told  no such file  (??) is there some thing needed at the front of the code /etc
  Much appreciate the help you have provided so far, 
 Kind Regards  Miykel

---

### Post by realzippy on 2011-04-21
Miykel,just see that the 
beta driver 270.41.06 supports the GT440.
Could swear that yesterday it was not listed;anyway,easiest way to install this driver is -as *HappyLinux* suggested- do add
[Xswatppa]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") to your system's software sources,like this:

1.Make sure you have uninstalled not-working Nvidia driver
  (System-Administration-AdditionalDrivers);reboot.

2.Open terminal,run:

```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```
this updates your system.In case of a included linux-kernel-update,
reboot again before going on!

3.Run:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```
then again
```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```
..after you have done this,again install the driver from
System-Administration-AdditionalDrivers
(..now this installs the beta driver from xswat,formerly it was
the 260.xx driver)
4.Reboot & pray

---

### Post by Miykel on 2011-04-21
G'Day guys and thanks so much for all your help.
  realzippy I run the codes you posted then installed the drivers via additional drivers tool, interesting to note, before the upgrade there were 3 drivers presented, which I tried one at a time, but after the upgrade there was only one, which gave me a little glimmer of hope, but (there's always a but) to no avail, after the reboot I ended up at the DOS screen again, one thing though, I've become very proficient at accessing the OS and uninstalling the driver lol .
 
 I guess I'll just have to do with the generic graphic drivers for now, once again thank you all for your help
 Kind regards Miykel

---

### Post by realzippy on 2011-04-21
After install-attempt and dropped to the "dos-thingy"
(btw,we call it "the shell"),you could log in and run:

```
sudo nvidia-xconfig
```

and 

```
startx
```


the (error-)output would give us a clue about what's going wrong..

---

### Post by Miykel on 2011-04-21
G'Day realzippy I tried that when you posted it earlier, must have forgotten to post a reply ( seniors moment ) but nothing happened, logged in, password etc.,  entered code and it just went to the  $  symbol again entered startx same result  (???), got pretty good at recovery though.
   All very peculiar possibly the OS and the VGA are to new or something  ( ???)
    Having trouble with vlc playing dvds now but will start another thread about that.
   "If it was easy it wouldn't be worth doing"
  Kind regards Miykel

---

### Post by dino99 on 2011-04-21
sudo rm /etc/X11/xorg.conf

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo apt-get install nvidia-current
sudo apt-get install nvidia-common
sudo apt-get install nvidia-settings

reboot (sudo shutdown -r now)

---

### Post by realzippy on 2011-04-21
@dino

Why should OP run you commands?
Wether his "apt-get" nor "dpkg" is broken;also no need to remove xorg.conf
since OP (read whole thread?) is able to boot in recovery mode and can uninstall not working nvidia-driver via jockey-GUI.
Also all versions of nvidia-current were tested....
?

---

