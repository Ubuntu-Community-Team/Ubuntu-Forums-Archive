---
title: "Wubi Lucid cannot enable graphics effects."
date: 2010-05-03
forum: General Help
---

### Post by gaalaaant on 2010-05-03
I am running Wubi 64 bit Lucid on a Toshiba Satellite A215 S7422.  In Karmic I was able to use desktop effects on max, with cube desktops and all the bells.  I can no longer enable them, and after running Compiz-check I received a fail on  "Checking for hardware/setup problems."  The given reason was "Software Razterizer in use."  Any idea what the rasterizer is/does?  Would disabling it affect any other processes?  Help Appreciated.  



PS: If anyone can link to an article explaining how to switch from W7 Bootloader to Grub 2 (Which I already have installed) it would be greatly appreciated.

---

### Post by clhsharky on 2010-05-04
Hi gaalaaant

Software Razterizer is software rendering of 3D

Post

```
glxinfo | grep -i render
```

Sharky

---

### Post by gaalaaant on 2010-05-04
Here you go man
```
direct rendering: Yes
OpenGL renderer string: Software Rasterizer

``` 
Man you are just like helping me out all over the place.

---

### Post by clhsharky on 2010-05-04
HI

I try to help any one that I can.
I'm old and slow but do what I can.

I need to know whats in your boot string.
~/ect/default/grub
This line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
That mine, need to see what yours says.

Sharky

---

### Post by gaalaaant on 2010-05-04
Here you go:


```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```


I guess we have that working then.

---

### Post by clhsharky on 2010-05-04
HI gaalaaant

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Its good.

Did you ever have 9.10 on your system?
Have you tried to fglrx?
PM me
Sharky

---

### Post by gaalaaant on 2010-05-04
I did at some point  under wubi but there was a screw up in the middle of the upgrade and I had to reinstall wubi.  I had fglrx in my old distro, I'll try installing it again.

---

### Post by clhsharky on 2010-05-05
gaalaaant

No problem fglrx can flushed out and radeon reinstalled.

Sharky

I looked over your xorg log, you have old packages.
Could explain some of your problems. Still fixable.

---

### Post by gaalaaant on 2010-05-05
Awesome! That's what I love about Ubuntu; everything is fixable.

---

### Post by clhsharky on 2010-05-05
gaalaaant


Your xorg is showing karmic or older, check system/about Ubuntu.

Sharky

---

### Post by gaalaaant on 2010-05-05
Here is the first line of the doc:

"You are using Ubuntu 10.04 LTS
                - the Lucid Lynx - released in April 2010 and supported until April 2013."
	What you say may not be wrong because my install stalled like 2x so I had to do a full reinstall of wubi but maybe bits stayed old after the update.  

So what now?I tried "sudo apt-get upgrade", but xorg didn't come up in the list of what was updated.  As to my other (grub) problem, I will try using upgrade to install grub in the proper location.

Edit: Tried ```
sudo dpkg-reconfigure -phigh xserver-xorg

```

nothing happened.


Edit 2: Just purged and currently reinstalling (have to burn another Lucid DVD, lent mine to friend) xorg.  I'll post back results.

---

### Post by gaalaaant on 2010-05-05
Okay NOT GOOD.  So I was reinstalling xorg and it prompted me to pop in my Lucid CD (I don't understand why it doesn't just download the new files) and as I reached over, I grazed the two supports I use to keep my laptop open under my shelf, causing my laptop to close, without any graphics drivers, and freeze.  Now, even though I HAVE a lucid CD, after I use install xserver-xorg, it still says files are missing and it won't boot to a graphical interface.  Is there anyway to fix this?

---

### Post by clhsharky on 2010-05-06
gaalaaant


Can you start up in safe graphics?

Make sure your source is correct, heres mine.

```
# deb cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Alpha amd64 (20100113)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ lucid main restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu/ lucid-security main restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ lucid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid-security multiverse

```

 use
```
gksudo gedit /etc/apt/sources.list
```

to correct yours, than save.

```
sudo apt-get update
sudo apt-get upgrade
```

You can delete yours  and copy/past
mine.

To install radeon

```
 sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
sudo restart gdm
```

For your grub.

```
gksudo gedit /etc/default/grub
```

find
> GRUB_TIMEOUT=10
and add ```
#
```
in front so it now this
```
#GRUB_TIMEOUT=10
```
save
then run
```
sudo update-initramfs -u -k all
sudo update-grub
```
restart

I didn't mean for you to do this alone.


Sharky

---

### Post by gaalaaant on 2010-05-06
I am not sure what safe graphics is, but if you mean the graphical thing with the blue box then sure I will try that right as I get home from school.

---

### Post by gaalaaant on 2010-05-06
I am not sure how to get the source code in since I am running a terminal and don't know how to get to the internet.

---

### Post by clhsharky on 2010-05-06
gaalaaant

If  you can get to a terminal run the install radeon code.

You can continual update once you can boot up in gdm.

Waiting to hear back.


Sharky


Up date first than radeon.
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo restart gdm
```

---

### Post by gaalaaant on 2010-05-06
Kay i cannot get to safe graphics mode, though I did figure out that the extra boot options (2.6.32-generic instead of 2.6.34-generic) is the Lucid but still with wavy graphics.  Sorry I went off on my own, it wasn't impatience I just figured I wanted to contribute to fixing it too, and that I would have to learn this stuff sometime.  Ill try to install radeon.

EDIT: Tried to install radeon from that first long post, and it didn't work.  Every try to get packages from the internet failed.  I don't think it can connect.  I will try to install radeon from the way you described in the second post but I have doubts about that working basically because I think it is having trouble connecting to the net when it is running as terminal.  For some reason even when I had it running graphically, apt-get upate would warrant a request to insert the CD.  If this helps at all, I notice that during boot it says repeatedly "Failed to Allocate GEM..."  I am not sure what comes after that.

---

### Post by clhsharky on 2010-05-06
gaalaaant

I did a fresh in stall yesterday on another hd because I really didn't know any more what was default on Lucid. I originally installed Lucid at A2 and with all my testing with every upgrade, every kernel, every video driver.
 I allways do a upgrade and a clean install, but I think testing was enough upgrade for this release. Any ways my tester never broke all the way up to kernel 2.6.34.rc6 G3D drivers,xorg1.8,mesa7.8.
On fresh install Compiz works out of the box on our chip, Google Earth runs good, my v machine with XP is good, simple games like extreme tux racer is good. It only took 1 hour to install OS and my apps including all the restricted extra. And I must say, not one problem on complete install.

If you still have no luck can still do a fresh install. All though I would uninstall wubi from within windows, clean with maybe CCleaner, and defrag, be for fresh install. Wubi is fine.

Fixing is learning, just didn't want you to get to frustrated.

Let me know where your at and what you want to do with Lucid.

Sharky

---

### Post by gaalaaant on 2010-05-06
I am about to run that stuff, just had to print it.  I really like using Wubi because the one time I used PartitionMagic and that other software, all my stuff got deleted.  I don't want to mess around with partitions on my only PC which is why Wubi is a godsend.  I think if this next thing doesn't work I'll just uninstall Wubi and reinstall it.  Or would you suggest just making a new partition?


Edit: Yes again, nothing installed, for some reason it can't take packages from the internet.  So what's you opinion?  Just install from disk and repartition?  Use wubi again?

---

### Post by clhsharky on 2010-05-06
gaalaaant

Wubi is fine, your install got messed up on upgrade, it happens.
I'm sure your system is still fixable, but having a good Lucid first, make things better on down the line.

If you reinstall make sure W7 is clean and proper.

Any questions?

Sharky

---

### Post by gaalaaant on 2010-05-06
Umm no questions.  And other than this one little hiccup I've been loving it.  So you're saying uninstall and then reinstall?

---

### Post by clhsharky on 2010-05-06
gaalaaant


> So you're saying uninstall and then reinstall?
NO

 Did you get it working or what?

Sharky

---

### Post by gaalaaant on 2010-05-06
Umm no, none of what has been suggested works.  I am having trouble in that it won't install packages from the net.  On every install from a link, it says FAILED next to it or ERROR

---

### Post by clhsharky on 2010-05-06
gaalaaant

The source list isn't right, does every thing look right to you compared to mine?
You can also venue and change it in Ubuntu tweak.
I must say clean install would be faster.

Sharky

---

### Post by gaalaaant on 2010-05-06
Sharky I cannot find my source list (if that's what that first REALLY LONG thing was with the scroll bar) because when I boot I can't get into safe graphics mode and therefore can't do gksudo or gedit.

---

### Post by clhsharky on 2010-05-06
gaalaaant


Sorry man.

I would do a clean install.

Sharky

---

### Post by gaalaaant on 2010-05-06
mneh it's cool. I just have to re-download wubi real quick.

---

### Post by gaalaaant on 2010-05-06
I reinstalled, and now the 2 extras dont pop up, but for some reason this is listed as Ubuntu 2.6.32 instead of .34.  Strange but no worry.  The wiggling is back so maybe that's tied to the number because the old .32 was the wiggling one too.  I will apply the fixes from the old post to fix it.

Edit: I saw that in the old thread you suggested (which fixed it) to install the .34 rc6 kernel.  Anyway to get rid of the 32 afterwards?  Just for computing cleanliness' sake just wondering.

---

### Post by clhsharky on 2010-05-06
gaalaaant


GOOD
Is compiz working?

Ubuntu tweak is very good removing kernels and many other tweaks.
You may also remove old kernels in synaptic.


Sharky

---

### Post by gaalaaant on 2010-05-06
I am still working on the wiggling thing, since i had to restart to install updates.  Will post back with results.

---

### Post by gaalaaant on 2010-05-06
Okay, wiggling's gone.  

Now 3 Questions (Apparently all the guys in my family love listing):

1.  Should I try all of those things that you mentioned while I only had terminal?  Because graphics effects still don't work.

2. Apparently Grub was not installed during my install.  The above commands; will they help me get grub running?

3. What resolution is higher 1440x900 or 1280x1024?  Because now my monitor lists the latter, and while it looks nicer, the panel and bottom bar disappear when i enable it.

Many thanks for all the help Sharky.

---

### Post by clhsharky on 2010-05-06
gaalaaant


Start with these

```
glxinfo | grep -i render
sudo update-initramfs -u -k all
sudo update-grub
```

Default is best on monitor, was it 1440x900.
Why do you say grubs not running, you booted right.

Sharky

---

### Post by gaalaaant on 2010-05-06
Okay, did that.  Should i go on to the previously mentioned stuff?

---

### Post by clhsharky on 2010-05-06
gaalaaant

Results from

```
glxinfo | grep -i render
```

> Should i go on to the previously mentioned stuff

What exactly do you mean? For which problem.

Sharky

---

### Post by gaalaaant on 2010-05-06
Results:

```


direct rendering: Yes
OpenGL renderer string: Software Rasterizer

```

Umm I meant should I use the directions you mentioned before I reinstalled to take care of the Grub issue.

---

### Post by clhsharky on 2010-05-06
gaalaaant


> direct rendering: Yes
OpenGL renderer string: Software Rasterizer
bummer

please code
```
glxinfo | grep OpenGL
```

> take care of the Grub issue
Yes of course.

Sharky

---

### Post by gaalaaant on 2010-05-06
Here is result:

```
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:

```

---

### Post by gaalaaant on 2010-05-06
Here is result:

```
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:

```

---

### Post by gaalaaant on 2010-05-06
Here is result:

```
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:

```

---

### Post by gaalaaant on 2010-05-06
Here is result:

```
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:

```

---

### Post by gaalaaant on 2010-05-06
Here is result:

```
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:

```

---

### Post by gaalaaant on 2010-05-06
Here is result:

```
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:

```

---

### Post by gaalaaant on 2010-05-06
Here is result:

```
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:

```

---

### Post by clhsharky on 2010-05-06
Wow what happend

Well you do have the right opengl now 'mesa'. I will search for reason your build ended up Software Rasterizer. It happened to me once with KMS in Karmic. Its in my docs. somewhere.
searching

Sharky

> 7.7.1
is correct

> 2.1 
Is not correct except G3D Software Rasterizer on your chip. Should be 1.5 in KMS. You must still be in UMS.

---

### Post by clhsharky on 2010-05-06
gaalaaant

To enable KMS, although it should be default.

Run
```
gksudo gedit /etc/default/grub
```

Add
```
radeon.modeset=1
```
to this line
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
now to be
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=1"

save

```
sudo update-initramfs -u -k all
sudo update-grub
```

restart

Sharky

---

### Post by gaalaaant on 2010-05-07
doing that now.  Couldn't sleep, decided to get back to important things hah.

Edit:  Restarted, desktop effects still can't be enabled.  If it helps: Every time I try to enable them, it says (right after I check the box) "searching for available drivers."

---

### Post by clhsharky on 2010-05-07
gaalaaant

After research last night 'Software Rasterizer, radeon, and compiz, duel screens' xrandr probably not set right.

run
```
xrandr  --output  LVDS --off
sudo restart gdm
```

run
```
xrandr -q
```
post back to check change

Install grandr from repos, utility for changing xrandr. 
Run
```
grandr
``` 
in terminal to start utility.

sharky

---

### Post by gaalaaant on 2010-05-07
xrandr result:


```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192
VGA-0 connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9 +   75.0* 
   1280x1024      75.0     60.0  
   1152x864       75.0     67.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3     56.2  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   1280x800       59.9 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)

```

---

### Post by clhsharky on 2010-05-08
gaalaaant

I see your at native resalution now '1440x900       59.9 +   75.0* '

> xrandr  --output  LVDS --off

was to disconnect laptop screen ,seams its still connected.
Second screen doesn't all ways composite, would like to shut off laptop screen in randr.

Sharky

---

### Post by gaalaaant on 2010-05-08
Umm I was sure I already had it off from that monitor manager thing, but now I am SURE it's off, I actually checked.  

xrandr result:


```

Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192
VGA-0 connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9 +   75.0* 
   1280x1024      75.0     60.0  
   1152x864       75.0     67.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3     56.2  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   1280x800       59.9 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)

```

---

### Post by gaalaaant on 2010-05-11
Still getting an error strangely enough.

---

