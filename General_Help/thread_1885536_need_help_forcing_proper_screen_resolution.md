---
title: "need help forcing proper screen resolution"
date: 2011-11-23
forum: General Help
---

### Post by Namtellum on 2011-11-23
Hey guys, recently did a fresh install of 11.10 and am having trouble getting the proper screen resolution. I've tried to follow some guides to no avail. I'm trying to force 1920x1200 and here is what I've tried.

```
xrandr --newmode "1920x1200_60.00"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
```
result:
> xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19

```
xrandr
```
result:
> xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1360 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0  
   1360x768       60.0  
  1920x1200_60.00 (0x17b)  193.2MHz
        h: width  1920 start 2056 end 2256 total 2592 skew    0 clock   74.6KHz
        v: height 1200 start 1203 end 1209 total 1245           clock   59.9Hz

```
lspci |grep VGA
```
result:
> 05:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9300 GE] (rev a1)

and my xorg looks as follows:
> Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
   Identifier    "Default Screen"
   Device    "VirtualBox graphics card"
   Monitor    "Configured Monitor"
DefaultDepth    24
   SubSection "Display"
         Depth     24
         Modes     "1920x1200"
   EndSubSection
EndSection

So it looks to me that from my xrandr that 1920x1200 should be an option but the display menu only gives a max of 1024x768. If anyone can give me any pointers I would greatly appreciate it as I have been searching for a solution for several days.

---

### Post by RoyLongbottom on 2011-11-23
[FONT=Verdana]Google for Linux 1920 x 1200 and it looks as though it is not supported[/FONT]
[FONT=Verdana][/FONT] 
[FONT=Verdana]Roy[/FONT]

---

### Post by raja.genupula on 2011-11-23
> **Namtellum said:**
> Hey guys, recently did a fresh install of 11.10 and am having trouble getting the proper screen resolution. I've tried to follow some guides to no avail. I'm trying to force 1920x1200 and here is what I've tried.

```
xrandr --newmode "1920x1200_60.00"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
```
result:


```
xrandr
```
result:


```
lspci |grep VGA
```
result:


and my xorg looks as follows:


So it looks to me that from my xrandr that 1920x1200 should be an option but the display menu only gives a max of 1024x768. If anyone can give me any pointers I would greatly appreciate it as I have been searching for a solution for several days.

I am not much aware of these things , but some times if i have problem with my screen my monitor have button named as Auto that helps me to fix auto screen size with good zoom .

---

