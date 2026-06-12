---
title: "Dual Monitors?"
date: 2012-03-09
forum: General Help
---

### Post by Russianeer on 2012-03-09
I have been trying to figure out how to enable dual monitors for the past few hours but still have not figured it out. Could I get some assistance from the community on how to do this?

This is the output from xrandr:
```
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 2624 x 1200
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
DFP3 connected 1360x768+0+0 (normal left inverted right x axis y axis) 406mm x 229mm
   1360x768       60.0*+
   1280x768       59.9  
   1280x720       59.9  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
DFP4 connected 1600x900+0+0 (normal left inverted right x axis y axis) 442mm x 249mm
   1600x900       60.0*+
   1440x900       75.0     59.9  
   1152x864       75.0     60.0  
   1280x768       75.0     59.9  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     67.0     59.9  
CRT1 disconnected (normal left inverted right x axis y axis)

```This is my xorg.conf
```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
        SubSection "Display"
                Modes "1600x900"
                Virtual 2624 1200
        EndSubSection
EndSection

Section "Module"
        Load    "glx"
EndSection

```I would like DFP4 to be to the left of DFP3. How would I do this?

Any help will be appreicated :)

---

### Post by Herman on 2012-03-09
I usually just type 'displays' in the dash search bar, or just 'dis' for short.
Then I look for the 'Displays' icon and click on it for the 'Displays' dialog box.

EDIT: I use Ubuntu and I noticed your thread says 'Kubuntu' on top. Sorry, I hope something similar can be found in Kubuntu, most likely it will have some other name like Kdisplays or something.

---

### Post by anaconda on 2012-03-09
Do you have a nvidia graphicschip

if you do it is easy. Just run nvidia-settings and enable 2 screens from there.

You might need to install it first..

---

### Post by Russianeer on 2012-03-09
> **anaconda said:**
> Do you have a nvidia graphicschip

if you do it is easy. Just run nvidia-settings and enable 2 screens from there.

You might need to install it first..
I use an ATI HD Radeon 6850.

---

### Post by Herman on 2012-03-09
Try taking a look at the following thread in Kubuntu Web Forums, [ATI 5570 Dual Issues]("http://www.kubuntuforums.net/showthread.php?54707-ATI-5770-dual-issues&highlight=ati+%2Bdual+monitors").
The second post give this link,  [http://www.riedquat.de/blog/2011-08-14-01](http://www.riedquat.de/blog/2011-08-14-01) which looks like it might (maybe) help you.

---

### Post by Russianeer on 2012-03-09
> **Herman said:**
> Try taking a look at the following thread in Kubuntu Web Forums, [ATI 5570 Dual Issues]("http://www.kubuntuforums.net/showthread.php?54707-ATI-5770-dual-issues&highlight=ati+%2Bdual+monitors").
The second post give this link,  [http://www.riedquat.de/blog/2011-08-14-01](http://www.riedquat.de/blog/2011-08-14-01) which looks like it might (maybe) help you.
Not sure why I put Kubuntu as the tag, I use Xubuntu, but I trie[FONT=monospace]d[/FONT] to run  "sudo amdcccle" and changing the settings, but when I modify the settings, nothing happens, and I still have 2 cloned monitors.

Edit: I installed grandr and ran it, attempted to change the monitor "Output Layout" from "Clone" to "Extend" and the option was simply grayed out. When I try to change the position of the monitors in grandr, I get a message saying:

```
user set screen width 1600, larger than max width 2624, set to max width
```This must be somehow connected to my xorg.conf file.

---

### Post by oldos2er on 2012-03-09
I changed the thread tag for you.

---

### Post by Russianeer on 2012-03-09
Alright well I changed Xubuntu to ubuntu to see if the problem went away. Once I installed ubuntu went to settings, extended the monitors and everything seemed to work out of the box. Then, I installed the ATI driver and that's when everything went to hell (which is probably why it didn't work for Xubuntu). So I guess for now I am stuck without a driver.

---

