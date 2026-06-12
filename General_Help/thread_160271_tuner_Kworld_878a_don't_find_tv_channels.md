---
title: "tuner Kworld 878a don't find tv channels"
date: 2006-04-14
forum: General Help
---

### Post by zolly on 2006-04-14
My tuner is Kworld Xpert TV-PVR 878 (on PCI, FM radio, BG+DK, serial: VS-TV878RF, conexant 878a). In Windows i use PAL-BG and i have no problems.
I can't use in Linux because no programms can find channels, it shows only dots. I tried with: sudo modprobe card=xxx tuner=yyy, where xxx,yyy are numbers from some tables with configurations.
What can i do?

---

### Post by zolly on 2006-04-17
i use btspy to make a report:
-----------------------------------------------------------------------------------------------------------------
[FONT="Courier New"][SIZE="1"]### BtSpy Report ###



General information:

 Name:kworld 878a

 Chip: Bt878 , Rev: 0x00

 Subsystem: 0x00000000

 Vendor: Gammagraphx, Inc.

 Values to MUTE audio:

  Mute_GPOE  : 0x1c0007

  Mute_GPDATA: 0x000001

 Has TV Tuner: Yes

  TV_Mux   : 2

  TV_GPOE  : 0x1c0007

  TV_GPDATA: 0x080000

 Number of Composite Ins: 1

  Composite in #1

   Composite1_Mux   : 3

   Composite1_GPOE  : 0x1c0007

   Composite1_GPDATA: 0x000002

 Has SVideo: Yes

  SVideo_Mux   : 1

  SVideo_GPOE  : 0x1c0007

  SVideo_GPDATA: 0x000002

 Has Radio: Yes

  Radio_GPOE  : 0x1c0007

  Radio_GPDATA: 0x000001





Add here all the comments you want!

	If your card can decode Stereo TV , and

your card does NOT use one of the following

chips, you will have to "peek" the right

GPDATA and GPOE values to enable Stereo and

SAP audio. The driver already supports the

DPL3518, MSP34xx, PT2254, TDA7432, TDA8425,

TDA9840, TDA9850, TDA9855, TDA9873, TDA9874,

TDA9875, TEA6300 and TEA6420 and does not require

extra information to drive them!



If you are able to get your card working using

this program , please , mail me this file (with

any extra comments you would like to add) to:

[email]ejtagle@tutopia.com[/email] , so I can add native support

to your card in the next driver release![/SIZE][/FONT]
-----------------------------------------------------------------------------------------------------------------

and i put this configuration:
options bttv radio=1 pll=1 gpiomask=0x1c0007 audiomux=0x080000,0x000001,0x080000,0x080000,0x000001

with this configuration my radio start working !!!!!! :-D 
but the problem remains with tv that didn't find any channel. :(

---

### Post by zolly on 2006-04-17
to work with tv(color) and radio it's necesary to find (manualy) the correct tuner (try, reset pc, try again until works). The final configuration is:

options bttv radio=1 tuner=38 pll=1 gbuffers=4 gpiomask=0x1c0007 audiomux=0x080000,0x000001,0x080000,0x080000,0x000001

The End.

---

### Post by zolly on 2006-04-22
PS:
radio works best with: xmms-fmradio and gnomeradio

You can try "options bttv radio=1 pll=1 card=78 tuner=38" but then only radio don't work.

---

### Post by balpeta on 2006-05-06
I have the same problem.

In which file can I put the text "options bttv......."?

---

### Post by zolly on 2006-05-12
Add the line:
options bttv radio=1 tuner=38 pll=1 gbuffers=4 gpiomask=0x1c0007 audiomux=0x080000,0x000001,0x080000,0x080000,0x000001

Attention: i don't know why this post shows the last part of the above line with a space in 0x000 001. It is without that space: 0x000001.
This is a single line, not two lines.

in   /etc/modprobe.d/options
and restart linux.

---

### Post by zolly on 2006-05-13
to see teletext use: "alevt" program together with your tv viewer like "xawtv", and go to the channel where you know that have teletext.

To record a channel to avi, use "xawtv", go to "R record movie" option, put in movie driver: Microsoft AVI format, and maybe other options like frames/sec ... and push "start/stop recording" button.

---

