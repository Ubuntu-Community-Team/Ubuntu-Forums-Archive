---
title: "Out of the blue kernal issues"
date: 2006-02-16
forum: General Help
---

### Post by kudu on 2006-02-16
I installed the latest update to Cedega (v5.1) and suddenly my Nvidia 3d acceleration went kabluie. Couldn't turn it on no matter what. Finally had to resort to reinstalling ubuntu from scratch. I was running linux-image-2.6.12-10-686 whithout any problems until the Cedega update fiasco. Nvidia worked fine.  Now I can't get the 686 kernal to run properly, the xserver coughs on it. However, the 386 kernal works fine. How do I fix the xserver so it will be happy with the 686 kernal ? I've installed ubuntu several times in the past without any problems. Why now all of a sudden is anyones guess.

I tried installing via synaptic but I'm going to give it another shot using apt-get and see if that works. If anyone can pass on some good tips fixing the xserver from the command line, I'd appreciate it. I might try building my own custom 686 kernal next.

---

### Post by gibson on 2006-02-16
I dont think you have the nvidia modules in your kernel... you need to add these every time you recompile/upgrade your kernel.  easy way to check is open your /etx/X11/xorg.cong and change nvidia to nv, then run the old 

> /etc/init.d/gdm restart

if that works then it means you have to put the drivers into your kernel.

easy way is

> sudo apt-get install nvidia-glx

but i recommend method 2 from this cool guide, 

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

hope this helps and i have understood your problem properly.... it is late :)

all the best

---

### Post by rjwood on 2006-02-16
You should not need to be reinstalling so often or even at all for that matter. Don't panic when you have a shell. 

I suggest doing some of these 'how to's' on the forums to get used to the command line. That way when you lose you gui you won't feel lost.. The link recomended is a great 'how to'. 

Good Luck!!

---

### Post by kudu on 2006-02-16
[QUOTE=gibson]I dont think you have the nvidia modules in your kernel... you need to add these every time you recompile/upgrade your kernel.  easy way to check is open your /etx/X11/xorg.cong and change nvidia to nv, then run the old 



if that works then it means you have to put the drivers into your kernel.

easy way is



but i recommend method 2 from this cool guide, 

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

hope this helps and i have understood your problem properly.... it is late :)

all the best[/QUOTE]


First off...THANKS FOR THE REPLY!

I have the drivers installed. From the shell resulting from xserver failure to load, I logged in and tried "sudo apt-get install nvidia-glx" and got back "latest version already installed." I also tried "sudo nvidia-glx-config enable" but it didn't help.

The 386 kernel is loading properly. It's only the 686 kernel that won't load correctly.

As for reinstalling, I like to do it from time to time just to clean out all the junk that accumulates from all the constant installing and uninstalling of different packages and all their dependencies. Besides...it's fun...when it's intentional.

I've never had this problem before, always been a snap to install the 686 kernel. I'm using the synaptic nvidia package...7667 I believe. Nothing changed, just all of a sudden the sucker doesn't want to work.

---

### Post by kudu on 2006-02-16
I tried "sudo dpkg-reconfigure -phigh xserver-xorg" which essentially reverts xorg.conf to default settings and it worked. But if I try to install the nvidia drivers using "sudo apt-get install nvidia-glx" it says I already have them installed. What the heck ??

---

### Post by gibson on 2006-02-17
Could you post the "Device" and "Modules" part of your xorg.conf file?

I had a problem like this a while back, however, that was in Libranet and i cant remember that far back to reacall what i did.

Could you also state which nvidia card you have?

The guide i mentioned before has a little list of cards which you should use with the driver in the repository, anything newer... use the one from nvidia.

hth

---

### Post by kudu on 2006-02-17
[QUOTE=gibson]Could you post the "Device" and "Modules" part of your xorg.conf file?

I had a problem like this a while back, however, that was in Libranet and i cant remember that far back to reacall what i did.

Could you also state which nvidia card you have?

The guide i mentioned before has a little list of cards which you should use with the driver in the repository, anything newer... use the one from nvidia.

hth[/QUOTE]

Sure thing. Here they are:

Section "Module"
##	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"[PHP][/PHP]
##	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
EndSection

As you can see I have a GeForce 6800 GT card and I have been running it perfectly for last several months using the 686 kernel and the synaptic 7667 driver. So I don't know why it won't all of a sudden. Also, it's working perfectly right now with the 386 kernel.  :confused:

---

### Post by gibson on 2006-02-17
OK, rather than doing the apt-get install from the repo of the driver, please try method 2 from the how-to i posted above... i had a similar problem and method 2 did the job for me...

failing that.... look firther down that post and there are yet more suggestions...

I still feel that the nvidia modules are not in your 686 kernel

hope this helps

---

### Post by gibson on 2006-02-17
AAH - forget what ive said.... for all intents and purposes i think i have been a blithering idiot.

see this post, people appear to be having your problems...

[http://www.ubuntuforums.org/showthread.php?t=131657](http://www.ubuntuforums.org/showthread.php?t=131657)

sorry could not help more...

all the best and good luck

gibson

---

