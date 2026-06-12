---
title: "Set Nvidia Extension Limit to OFF , How ?"
date: 2011-06-20
forum: General Help
---

### Post by FrostBlue on 2011-06-20
Hi 
I have a GeForce 8700m and have recently upgraded to Natty with the latest driver 275.09.07 from Nvidia.

I have a software which cannot open a new file as it just crashes. Someone on Windows set Extension Limit to OFF in Nvidia settings and the problem went away for them.

I cant find that setting in Nvidia server settings. How do I set it up. Do I have to add something to xorg.cong ?

Thanks.

---

### Post by FrostBlue on 2011-06-20
Okay I found these two links
[http://www.nvnews.net/vbulletin/showthread.php?t=142835]("http://www.nvnews.net/vbulletin/showthread.php?t=142835")

[ftp://download.nvidia.com/XFree86/Linux-x86/195.22/README/knownissues.html#extension_string_size]("ftp://download.nvidia.com/XFree86/Linux-x86/195.22/README/knownissues.html#extension_string_size")

And I am also getting a Signal 11 error when the application crashes.

So I tried 
export GL_ExtensionStringVersion=17700 

But no change,the application still crashes.

---

### Post by pqwoerituytrueiwoq on 2011-06-20
i thought the latest was the 270 series
*checks*
seems there was a update 
*downloads*
you can check 
[FONT=Courier New].nvidia-settings-rc[/FONT] located in your home folder
still downloading
edit:
 forgot to ask what app is it?
edit:
signal 11 
i got that form google earth before i reported the bug to google now it works

---

### Post by FrostBlue on 2011-06-20
HAHA...wow,Love your post,the application is Maya2012,which used to work fine on Maverick.
I found the file in home folder but dont know where to put the command and well, what command exactly.

Heres whats in the file

#
# /home/jay/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Tue Jun 21 03:50:31 2011
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes
Timer = Graphics_Card_(GPU_0),Yes,1000
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000

# Attributes:

0/CursorShadow=0
0/CursorShadowAlpha=64
0/CursorShadowRed=0
0/CursorShadowGreen=0
0/CursorShadowBlue=0
0/CursorShadowXOffset=4
0/CursorShadowYOffset=2
0/SyncToVBlank=0
0/LogAniso=0
0/FSAA=0
0/TextureSharpen=0
0/AllowFlipping=1
0/FSAAAppControlled=1
0/LogAnisoAppControlled=1
0/OpenGLImageSettings=1
0/FSAAAppEnhanced=0
0/RedBrightness=0.000000
0/GreenBrightness=0.000000
0/BlueBrightness=0.000000
0/RedContrast=0.000000
0/GreenContrast=0.000000
0/BlueContrast=0.000000
0/RedGamma=1.000000
0/GreenGamma=1.000000
0/BlueGamma=1.000000
0/DigitalVibrance[DFP-0]=0
0/GPUScaling[DFP-0]=131073
0/OverscanCompensation[DFP-0]=0
0/ColorSpace[DFP-0]=0
0/ColorRange[DFP-0]=0
0/XVideoTextureBrightness=0
0/XVideoTextureContrast=0
0/XVideoTextureHue=0
0/XVideoTextureSaturation=0
0/XVideoTextureSyncToVBlank=1
0/XVideoSyncToDisplay=65536

---

### Post by pqwoerituytrueiwoq on 2011-06-20
i found something but do not feel like reading it
[http://developer.download.nvidia.com/compute/cuda/3_1/toolkit/docs/README_Linux.txt](http://developer.download.nvidia.com/compute/cuda/3_1/toolkit/docs/README_Linux.txt)
so i will let you read it and post your findings :twisted:
glad you found the post amusing it is almost like reading a talking to your self script in mores codewith all the STOPs at the end of every line

---

### Post by FrostBlue on 2011-06-21
Thanks pqwoerituytrueiwoq , but that link has the same information which I found earlier. Not much help. :(

---

