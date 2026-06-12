---
title: "Karmic Koala Intel 945GM Compiz Problems"
date: 2009-11-02
forum: General Help
---

### Post by moc02 on 2009-11-02
Hi,

I had been eagerly awaiting the release of Karmic Koala with the improvements for Intel Chipset Graphics. I have the following:

 Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller

I had previously had loads of problems with the restricted size of the desktop and getting the settings working to get dual monitor set up but Karmic has improved that. I had not bee able to get the the dual monitor set up working with the gnome display manager in karmic so I had to revert to using an xorg.conf file as follows:

Section "Monitor"
    Identifier      "VGA"
    Option        "LeftOf"     "LCD"
    Option "PreferredMode"  "1440x900"
EndSection

Section "Monitor"
    Identifier      "LCD"
    Option         "RightOf"      "VGA"
    #Options LeftOf, RightOf, Above, Below specify monitors&#65533; relative position
    # This optional entry specifies  whether  the  monitor  should  be
    #     turned  on  at  startup.  By default, the server will attempt to
    #     enable all connected monitors.
    #Option "Enable"  "true"
    #This optional entry specifies the initial rotation of the given monitor.
    #     Valid values for rotation are "normal", "left", "right", and "inverted".
    # Option "Rotate"  "left"
EndSection

Section "Screen"
    Identifier      "Default Screen"
    Device        "Intel 945G"
    Monitor       "LCD"
    DefaultDepth  24
    SubSection "Display"
        Depth          24
        Modes         "1280x1024"  "1024x768"   "640x480"
        Virtual    2720 900
        # This optional entry specifies the virtual screen resolution to be used.
        # If this entry is not present, the virtual screen resolution will be set to
        # accommodate all the valid video modes given in the Modes entry.
        # There is a known issue that DRI doesn't work on pre-965 if maximum is larger than 2048x2048.
    EndSubSection
EndSection

Section "Device"
    Identifier      "Intel 945G"
    Driver         "intel"
    Option          "monitor-VGA" "VGA"
    Option          "monitor-LVDS" "LCD"
    Option        "AccelMetod"    "EXA"
    # Using the name of the output defined by the video driver plus the identifier of a
    #     monitor section, one associates a monitor section with an output by adding an
    #     option to the Device section in the following format:
    #     Option "Monitor-outputname" "monitor ID"
    #Option         "monitor-TMDS-1" "dvi"
EndSection

So I had my dual monitor working and then got compiz going over the weekend. Brought it back into work and now compiz will not start when I have the dual monitor set up. I get the following error when i try compiz at the command line:

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (2720x900) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 

Here it is saying my max size is 2048x2048 I think so compiz cannot work. This had been an issue with previous versions of ubuntu as the virtual desktop size was restricted to this. However the new acceleration method for the intel chipsett (EXA if I am not mistaken) was meant to fix this. xrandr clearly shows my max size to be 4096 x 4096 so I am not sure what is going on.

Has anyone any ideas or know how to fix this?

Or has anyone been able to follow what my problem is?

Thanks,

Mark

---

### Post by HiRez_L on 2009-11-03
I was unable to get multi-monitors to work in Karmic (they worked fine in Jaunty) on my Dell Latitude D820 with the Intel 945GM graphics chip.  I followed your xorg.conf, and several others I found online nothing worked.  Every time I would try to go into the displays control panel and turn on the second monitor and turn mirroring off, my system would freeze hard, requiring the 10-second power-button hold reboot.  I finally got this to work by going under my home dir, under/.config, and editing monitors.xml.  My original monitors.xml:
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="TMDS-1">
      </output>
      <output name="TV">
      </output>
      <output name="VGA">
          <vendor>PNR</vendor>
          <product>0x5780</product>
          <serial>0x0000b5c6</serial>
          <width>1280</width>
          <height>1024</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="LVDS">
          <vendor>SHP</vendor>
          <product>0x13bd</product>
          <serial>0x00000000</serial>
          <width>1024</width>
          <height>1280</height>
          <rate>60</rate>
          <x>1280</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
  </configuration>
  <configuration>
      <clone>no</clone>
      <output name="VGA1">
          <vendor>PNR</vendor>
          <product>0x5780</product>
          <serial>0x0000b5c6</serial>
          <width>1280</width>
          <height>1024</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="LVDS1">
          <vendor>SHP</vendor>
          <product>0x13bd</product>
          <serial>0x00000000</serial>
      </output>
      <output name="DVI1">
      </output>
      <output name="TV1">
      </output>
  </configuration>
</monitors>
  My modifications:
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="TMDS-1">
      </output>
      <output name="TV">
      </output>
      <output name="VGA">
          <vendor>PNR</vendor>
          <product>0x5780</product>
          <serial>0x0000b5c6</serial>
          <width>1280</width>
          <height>1024</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
      <output name="LVDS">
          <vendor>SHP</vendor>
          <product>0x13bd</product>
          <serial>0x00000000</serial>
          <width>1440</width>
          <height>900</height>
          <rate>60</rate>
          <x>1280</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
  </configuration>
  <configuration>
      <clone>no</clone>
      <output name="VGA1">
          <vendor>PNR</vendor>
          <product>0x5780</product>
          <serial>0x0000b5c6</serial>
          <width>1280</width>
          <height>1024</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
      <output name="LVDS1">
          <vendor>SHP</vendor>
          <product>0x13bd</product>
          <serial>0x00000000</serial>
          <width>1440</width>
          <height>900</height>
          <rate>60</rate>
          <x>1280</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="DVI1">
      </output>
      <output name="TV1">
      </output>
  </configuration>
</monitors>

I also changed the Virtual line in xorg.conf from Virtual 2720 900  to Virtual 2720 1024

---

### Post by moc02 on 2009-11-03
Hi HiRez_L,

Thanks for the reply.

Can you tell me if you now have compiz working in your dual monitor set up?

I can get the dual monitors to work but it is just that compiz will only work when I am not using dual monitors and if I am it fails back to metacity.

Thanks,

moc02

---

### Post by P4man on 2009-11-03
> There is a known issue that DRI doesn't work on pre-965 if maximum is larger than 2048x2048.

You have a pre-965 card and your desktop is larger than 2kx2k with both monitors enabled. What xrandr says is irrelevant, you can obviously enable larger desktops, just not while using DRI (or vice versa)

I believe the new rendering method is UXA rather than EXA, but dont quote me on that. Have a look here:
[https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)

---

