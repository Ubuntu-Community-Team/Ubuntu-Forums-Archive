---
title: "Trouble with display"
date: 2010-02-20
forum: General Help
---

### Post by pfao on 2010-02-20
Hey, I am brand new to ubuntu, well linux in general, and I've just installed it on my Toshiba Portege R100. It's a fairly old computer, but I've read that it supports ubuntu quite well.
My problem is with the display. It was first of all only giving me a maximum of 800x600 resolution, which only took up a section of the screen in the center. So, after searching on the internet for a bit, I found a fix for it, and I got it to run at the proper 1024x768 resolution. However, what I was finding was that every time the screen dimmed after being left idle for a few seconds, the screen would zoom in on the top left corner of the screen, and it would show up in a sort of "double-vision", the screen would be displayed twice, just shifted slightly off to the side, so it was unreadable. I can't seem to find anyone else who has been having this problem, and any help would be greatly appreciated!
Thanks!
-pfao

---

### Post by GSF1200S on 2010-02-20
> **pfao said:**
> Hey, I am brand new to ubuntu, well linux in general, and I've just installed it on my Toshiba Portege R100. It's a fairly old computer, but I've read that it supports ubuntu quite well.
My problem is with the display. It was first of all only giving me a maximum of 800x600 resolution, which only took up a section of the screen in the center. So, after searching on the internet for a bit, I found a fix for it, and I got it to run at the proper 1024x768 resolution. However, what I was finding was that every time the screen dimmed after being left idle for a few seconds, the screen would zoom in on the top left corner of the screen, and it would show up in a sort of "double-vision", the screen would be displayed twice, just shifted slightly off to the side, so it was unreadable. I can't seem to find anyone else who has been having this problem, and any help would be greatly appreciated!
Thanks!
-pfao

What video card do you have? Can you post the results of

/etc/X11/xorg.conf

Also, try disabling visual effects in System>Appearence to see if that helps for now

---

### Post by 2hot6ft2 on 2010-02-20
Have you checked for restricted (proprietary) drivers?
System > Administration > Hardware Drivers

---

### Post by pfao on 2010-02-20
Alright, I checked " /etc/X11/xorg.conf" the file is completely empty. It opens the reader, but it is empty.
The video card is a "Trident XPm32 LP graphics controller". Also, I checked the appearances thing, and visual effects was already disabled.

I checked the hardware drivers, there are no proprietary drivers.

---

### Post by GSF1200S on 2010-02-20
Ok, first, try:
```
sudo apt-get update
```
and try to open the hardware drivers dialog again.

Did you disable visual affects? Sounds almost like a compiz issue to me. Thats not something that X usually does without compositing.

---

### Post by pfao on 2010-02-20
Alright, I did the 

sudo apt-get update

And it ran through a huge list of different web addresses, then said "Reading package lists... Done"

Then I checked the "Hardware Drivers" window again, and everything was empty (as before) and it just said "No proprietary drivers are in use on this system" at the top.

And nope, I didn't set the visual effects off manually. But this is a fairly old computer, might it have turned them off automatically because the hardware could not support it?

---

### Post by knave on 2010-02-21
Check [this]("http://electronicrandomness.blogspot.com/2008/02/toshiba-portege-r100-upgrade-and.html") page out.  Specifically:

"Next I set out to solve the problem where brightness changes to the LCD backlight, from unplugging AC power for example, would cause the display to zoom into the upper left quarter of the screen. Ctrl+alt+f1 followed by ctrl+alt+f7 would get the screen back to normal but I needed it to work correctly. The solution was to force the VESA BIOS Extension (VBE) Mode to 1024x768 resolution as well. This was accomplished by editing the /boot/grub/menu.lst file by uncommenting the defoptions line and changing it to defoptions=quiet splash vga=791. Then a sudo update-grub updates all active kernels with the default options we just specified."

Lots of good stuff on that page.

EDIT:  Also, you can simply go to "Power Management" and set the screen to *never* dim, whether on battery or AC.  I find myself using this lappy plugged in permanently as Ubuntu only gives around 45 minutes anyway...

---

### Post by pfao on 2010-02-21
Awesome!
Thanks so much for that link! I've got the resolution to work properly. However, I'm still having the trouble with the screen zooming in at the top. I tried to follow the instructions provided there, but it says to open the "/boot/grub/menu.lst file" however this file does not seem to exist on my computer!
Is there any way I can create the file? Or work around this?
The instructions provided are for ubuntu 9.04,, however I have installed 9.10, could this be the problem?

---

### Post by knave on 2010-02-22
Ah I was wondering about that.  I remember getting the resolution sorted in Karmic but had some suspend issues so I'm back on 9.04.  I will have a look at my brother's R100, he's using Mint 8, which is based on 9.10.

---

### Post by pfao on 2010-02-23
Alright so I've just decided to give 9.04 a try, and I've found that file.
However, I have no idea what he means when he says to "uncomment the defoptions line".
Could you help me out with that?
Also, the "fnfx" application he says to install doesnt seem to work. When I try to install it using the command "sudo apt-install fnfxd", it comes back to me saying "E: Couldn't find package fnfxd". And looking at the link he provides, I can't seem to figure out how I could go about installing it manually.

---

### Post by knave on 2010-02-24
In most config files you'll see a lot of hashes at the beginning of lines (#).  These basically make anything on that line invisible to the program that the config file is for.  Does that make sense?

Basically, uncommenting a line means deleting the "#" at the beginning of the line.

I remember fnfx being a hassle.  Gimme a few hours and I'll get back to you :-)

---

### Post by pfao on 2010-02-27
Alright sweet thanks!
Ok I've got fnfxd to work somehow, not really sure, oh well!
And as for the uncommenting, thanks! It's working now!
One question though: in that particular file, a lot of the lines had two # in front of them. To uncomment, would I just remove one or both?
I kept trying it a couple of different ways before I finally got it to work, but I'm still a little confused!

---

### Post by knave on 2010-03-02
> **pfao said:**
> One question though: in that particular file, a lot of the lines had two # in front of them. To uncomment, would I just remove one or both?

To that, I have no idea sorry!  I just tend to wing it with these things!

Glad you got the fn keys working, I totally forgot to get back to you sorry!
 Now *I* have a question for *you* :-)

How did you install Ubuntu on your laptop?  Wubi?  I used [this]("http://crunchbanglinux.org/forums/post/39955/#p39955") method and it's fantastic if you want to just have Ubuntu on there and nothing else.  I have also put in a solid state drive it's like new!  I loooooove this laptop.  Completely silent, too.  Although that changes when using flash or video...

---

### Post by pfao on 2010-03-06
Honestly, its the weirdest thing. Everywhere I look on the internet says that the R100 does not support booting from a USB CD drive. However, this particular one does and always did. My dad used it before me and he was always able to reformat it just by putting the disk in the external CD drive, and booting from that. When he first gave it to me, I did the same thing, it booted fine from the USB CD drive.
But, this time, I wanted to dual boot windows and Ubuntu, but I couldn't get the Windows boot CD to work. However, I popped in the Ubuntu disk, and it booted straight from that, no issue.
So I'm not sure if it's my particular laptop, or the CD drive (It's a Targus, not sure of the exact model), but it's always booted no problem from this USB CD drive.

EDIT: Actually it's an external USB DVD drive, not CD. Not sure if that would have anything to do with it, but who knows?

---

### Post by pfao on 2010-03-06
Oh, also, you mentioned something about flash and video?
I'm having a bit of an issue with that, not sure if that's what you're talking about, but I can't play any flash video in full screen, it goes really slow. It works mostly fine not in full screen though, just slightly slower than it should. Now, it always worked fine back on windows, so I don't know if you've got the same problem, or if you've figured out a solution?

---

### Post by knave on 2010-03-07
I have read somewhere that the most recent bios (1.6) supports USB Drive booting, but like all those other folks out there, I have had no luck.  That is really great to hear that you're having luck though :-)  I have been thinking about Windows for the sole purpose of playing Starcraft and Baldur's Gate with no issues.  And the first Half Life!

As for flash video, it's generally just poor.  I actually meant the laptop is silent except when playing a flash game online or watching video, then the fan fires up and goes really loud.  All normal though, the CPU temp stabilises at around 56 Celcius.

But yes, fullscreen Youtube is unwatchable...

---

