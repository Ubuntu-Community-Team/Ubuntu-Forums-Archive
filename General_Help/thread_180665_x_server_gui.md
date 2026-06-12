---
title: "x server gui?"
date: 2006-05-22
forum: General Help
---

### Post by way2evil on 2006-05-22
i tried installing ubuntu on a 15gb partition with a dual boot of xp pro. when i install ubuntu on the partition it says x server graphical interface did not install properly and it is disabled. then ubuntu logs into the command prompt and says re enable it when it is properly configured. what do i do now? specs?

inte p4 3.2ghz ht
2gb ram
250gb
now i now it could be vid card driver
xfx geforce 7600gs

any advice?? thanks guys

---

### Post by bluevoodoo1 on 2006-05-22
```
sudo dpkg-reconfigure xserver-xorg
```

For the driver select "nv" or even "vesa." 

Then start the graphical login:
```
sudo /etc/init.d/gdm restart
```

Then follow this guide to get the "nvidia" driver working...
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

---

### Post by way2evil on 2006-05-22
well i did that, thank you, but when i run the second command, it says xserver gdm is disabled. how do i reenable it? thanks

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=way2evil]well i did that, thank you, but when i run the second command, it says xserver gdm is disabled. how do i reenable it? thanks[/QUOTE]

you could try...

```
startx
```

---

### Post by way2evil on 2006-05-22
nope, i do startx then gdm restart and it still gets the same error. also, when i installed ubuntu the ubuntu logo was not there. it was a huge white space where you press enter or type server. it works fine on my other computer (old old old) so i am guessing the problem is in the computer and not ubuntu. thanks for any info

---

### Post by bluevoodoo1 on 2006-05-22
You could also try running...

```
lspci
```

and look for a line that deals with your video card, to see if it is even being recognized. Make sure the BusID shown is the same as the results of this command...

```
sudo cat /etc/X11/xorg.conf | grep BusID
```

(if they are the same, but there are extra 0's look below)

If they are not the same, run "sudo dpkg-reconfigure xserver-xorg" again and make sure you enter the correct BusID.

You might have to reformat the BusID from the lspci command here's an example...

line from lspci that deals with my video card:
0000:02:09.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500]

and the way it should be formatted...
brian@ubuntu:~$ sudo cat /etc/X11/xorg.conf | grep BusID
	     BusID		"PCI:2:9:0"


I hope that made sense. Other than that I'm pretty much out of ideas...

---

### Post by way2evil on 2006-05-22
welp i guess you found the problem. it says vga compatible (forgot acutal line) but it said something like not compatible or not recognized. it did say nvidia. so what do i do now? get a driver for linux?

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=way2evil]welp i guess you found the problem. it says vga compatible (forgot acutal line) but it said something like not compatible or not recognized. it did say nvidia. so what do i do now? get a driver for linux?[/QUOTE]

Well, the first steps we did configured a basic driver, but the problem is that the card is not being recognized. Do you have another available slot to plug it into?

On a side note... What brand and model is your motherboard?

---

### Post by way2evil on 2006-05-22
Its an HP. The board is an Asus Grouper whatever that is. Its a PCI-E card so no, i dont have another slot

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=way2evil]Its an HP. The board is an Asus Grouper whatever that is. Its a PCI-E card so no, i dont have another slot[/QUOTE]

Well, specifics here would be best. But I'm out of ideas. I hope someone reading this has some more ideas. 

You might also post something here... 
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)
because the author of that thread is very knowledgeable about nvidia cards and related issues.

---

### Post by way2evil on 2006-05-22
thanks, i will post there, but do you think i should install a driver using method 1?

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=way2evil]thanks, i will post there, but do you think i should install a driver using method 1?[/QUOTE]

Yes.

---

### Post by tseliot on 2006-05-23
Type:
sudo nano -w /etc/X11/xorg.conf

get to the Section Device and set the driver to "vesa"

CTRL+X to exit (save the file)

Then type:
sudo /etc/init.d/gdm restart

If it doesn't work, try setting the driver to "vga" (instead of vesa) and repeat the same process.

If that doesn't work can you post the Section Device of your /etc/X11/xorg.conf?

---

### Post by way2evil on 2006-05-23
THANK YOU SO SO SO MUCH. it works great now. but can you tell me how to adjust my monitor position through ubuntu? thanks

---

### Post by tseliot on 2006-05-23
[QUOTE=way2evil]THANK YOU SO SO SO MUCH. it works great now. but can you tell me how to adjust my monitor position through ubuntu? thanks[/QUOTE]
1) Now you can use the graphcal interface but I suggest you to install the latest Nvidia driver so as to use 3d acceleration and have a better quality in videos.

Try my script for an automatic installation of the driver:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

2) Once you install the driver the screen should be in the right position. If not, you should use the commands (buttons) on your monitor to set the position manually. Every monitor has those buttons.

---

