---
title: "Nvidia SLI question"
date: 2012-09-01
forum: General Help
---

### Post by Styrka on 2012-09-01
Hello all. I have to admit that I've been gleaning information from the Ubuntu forums for quite some time now but I have finally run into an issue that I just can't seem to find the answer I'm searching for. I have just recently finished installing 12.04 and completed updates and such. I've just barely finished installing wine, playonlinux, and various assortments of games which are all working great. However, the issue I have is when I try to find anything about SLI capabilities. I have an intel 980 with 2 nvidia GTX 560tis in my machine. I have two main questions about this setup. The first deals with the Xorg.conf file that I've heard and read so much about...mine is completely blank with the exception of a paragraph of information that I don't understand.

"Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

I've seen other Xorg.conf files that have much more information than this and I was wondering why mine is completely blank. 

The second question I had deals with enabling SLI. I ALWAYS find information for people who have 2 cards and want 2 monitors, but I don't have that setup. I just have 2 cards with one monitor and I'm just trying to setup AFR or SFR for better gaming fps. It seems simple, but I've searched for quite some time for help with this and I can't find anyone in this same situation.

One last bit of information. I also read that I could edit the Xorg.conf file (having made a backup of course) by typing some simple commands. Whenever I type in anything in the CLI to edit this file I get this message:


Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.


ERROR: Unable to write to directory '/etc/X11'.

I have no idea what this means as I'm pretty new to the Linux and Ubuntu world. Any help with this would be greatly appreciated. Thanks again.

---

