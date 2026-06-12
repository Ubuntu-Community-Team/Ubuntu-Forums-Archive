---
title: "Dual Monitor without FGLRX?"
date: 2005-02-11
forum: General Help
---

### Post by bobmitch on 2005-02-11
Is it possible to configure XFree for a dual monitor setup from my ATI 9800 pro - *without* running the fglrx drivers?

I have been able to create a dual monitor setup using both the ubuntu packaged and also the latest drivers from ati without any problem.

However, due to a problem with the Realtime LSM module and JACK , the audio piping tool ( see [here](http://ubuntuforums.org/showthread.php?t=14974) ), this cannot be done.  (Unless you can solve that issue :)  )

Jack and lsm work well together using the standard non-ati drivers.

HW acceleration is of secondary importance to screen real-estate.

Please help,
Rgds,
mitch

---

### Post by MrRoboto on 2005-02-11
If you use Xorg you can set up a dual monitor environment faster than xinerama using MergedFB.

Put this in xorg.conf in Section "Device"


**Option "MergedFB" "true"**

and
[B]
Option "MetaModes" "1024x768-1024x768"[/B] #this gives the right resolution to both monitor, change them as you need.

to configure  the monitors and other use google  :wink:

[MergerFB](http://dri.freedesktop.org/wiki/MergedFB)


For XFree86 just use Xinerama configuration

---

### Post by bobmitch on 2005-02-11
[QUOTE=MrRoboto]If you use Xorg you can set up a dual monitor environment faster than xinerama using MergedFB.


For XFree86 just use Xinerama configuration[/QUOTE]

I am planning on sticking with XFree86 for now.

I don`t see Xinerama in the package manager - is it an existing extension of XFree?
How do I enable it?

Apolgoies for noobness.  ;)

---

### Post by MrRoboto on 2005-02-11
From [LinuxQuestions](http://wiki.linuxquestions.org/wiki/Using_multiple_monitors_with_XFree86#Xinerama)

[I]Configuration

This section contains some quick info to configure the multihead setups.
Some basic knowledge of the config file is needed for this. The XF86Config page should describe it.
[edit]
Multihead

Each videocard should have a working 'Device' section. (Test this by using it as the single output). Add a matching BusID option to each Device section so it knows which driver to use for each physical device. The proper BusID can be found by using lspci or XFree86 -scanpci. Example BusID line looks like this:

BusID "PCI:1:0:0"

(Note that even AGP cards use the 'PCI:' prefix)
For single videocards that support multihead it depends on the used driver. In most cases these cards have a second entry in lspci/scanpci. Each head on the card should have a seperate Device section, each with the same 'Driver' option but different 'Identifier and'BusID' options. A special option needs to be added for multihead configuration. Each Device sections needs a 'Screen' option with a number. For example:

Screen "0"

This would indicate that this particular device section if for the primary head, the other device sections should have a similar option, but with the number increased. The other configuration options of the driver should be only used in the device section of the primary head.

Each monitor should have a working 'Monitor' section. (Also test these as single output). Now create a 'Screen' section for every monitor-videocard combination.

After this it's time to set up a multihead 'Layout' section in the XF86Config. To get normal Multihead, just add Screen options to your normal Layout. Example:

Screen 0 "Normal"
Screen 1 "TV"
Screen 2 "Fridge-LCD"

etc.
Now if you start up X, you should have seperate X sessions running on each screen.
[edit]
Xinerama

Almost the same as above. Only need to enable the Xinerama extension. This can be done either by starting XFree86 with the '+xinerama' option, or adding 'Option "Xinerama" "On" to the 'ServerFlags' section of the XF86Config.
And you need to specify the position of the screen relative to another. This can be done in the 'Layout' section. Choices are: LeftOf,RightOf,Above,Below,Absolute X,Y, Relative X Y Example:

Screen 0 "Main"
Screen 1 "Secondary" LeftOf "Main"
Screen 2 "TV" relative "Main" 0 2000[/I]


And Check this out [XF86Conf exemple](http://wiki.linuxquestions.org/wiki/Xinerama_for_Radeon_9200)

---

