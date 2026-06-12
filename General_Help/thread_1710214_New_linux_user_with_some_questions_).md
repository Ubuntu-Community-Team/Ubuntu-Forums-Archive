---
title: "New linux user with some questions :)"
date: 2011-03-19
forum: General Help
---

### Post by Vodkaholic on 2011-03-19
Hi all well ive finaly got rid of windows (not sure yet if that's a good thing yet)
Anyway ive installed ubuntu everything seems so very very new lol

Right my problems :(
I can't seem to find 2.1 sound channel in the sound pannel, My sound is also very "scrachy" sounding

Is there a way to Change the "X - +" buttons on all windows to the right like windows is >.> am so lost with that simple move.

Also everytime I bring a window/brower up there always stuck on the very top left hand side, I there a way to make it remmber where ive left them?

Also lol (sorry) Is there a windows snaping app or anything like that, I miss this so much with my multiy monitors

And Last but not least :D Is there a way to get rid of the passwords >.> my god every 10 seconds its asking me to enter for this and that very very annoying...

Many Thanks
VK

Edit also :C some and only some youtube video's are White and nothing happens but some work.

---

### Post by Mashvv on 2011-03-19
simply i would like to answer you with

I have no clue what you are talking about,
 except for the password part i would like to tell you that the password is a smart move to [COLOR="Red"]KEEP[/COLOR] and you can set it to be applied automatically if it annoys you that much!

---

### Post by sanderd17 on 2011-03-19
I'm not a sound man (I also don't know a thig about the youtube videos), but I can help with the rest.

To change the window buttons (-+x) to the right, just change the window theme. Only the radiance and ambiance themes place those buttons on the left. I like the elementary theme: [http://www.webupd8.org/2010/03/new-version-of-elementary-gnome-theme.html](http://www.webupd8.org/2010/03/new-version-of-elementary-gnome-theme.html) (follow the instructions for lucid, they aren't changed) but you can choose any thme you want, just google for theme+ubuntu or something.

For window placement, install the compiz settings manager (search for it in the software center). Open it and go to the bottom for the window placement. I don't think that you can let it remember the placement, but there are some choices you can try.

I don't know what you mean with "snapping" but compiz has almost everything for window management.

As a final thing: you don't want to get rid of the passwords, any way, when you configured your computer, you won't need to type passwords that much. It is possible to get rid of the passwords, but we're not allowed to tell it on this forums. It's what we call activating or creating a root account.

---

### Post by TomBrown2009 on 2011-03-19
Window title bar buttons:  Press Alt+F2 to bring up Run Application window. Type gconf-editor into the box, click Run to bring up Configuration Editor. Browse to apps - metacity - general, look for button_layout on the right panel. Change the value in the button_layout from close,minimize,maximize: to menu:minimize,maximize,close and press the Enter key.

---

### Post by Topsiho on 2011-03-19
The password thing is what makes Linux safe from viruses.
You only have to enter the root password when you are doing something that only a root (administrator) is allowed to do, such as installing programs, and configuring system settings and files.
My wife, who has no root privileges, only has to enter her password when logging in.

The reason that viruses have no chance in Linux is that they don't know the root password, and so can not install themselves on your computer.
Unless of course you circumvent this by working as root, or something as stupid as that.

So please don't ask on this forum to tell you how to make your Linux as virus prone as Windows :)
And also please get rid of bad Windows habits, such as installing from warez sites and such. Even a really good OS such as Linux can be jeopardized by bad administration.

Topsiho

---

### Post by thunderbirdje on 2011-03-19
> **Vodkaholic said:**
> Hi all well ive finaly got rid of windows (not sure yet if that's a good thing yet)


Me too! Don't worry, I am running it now for 1,5 weeks and was quite scared in the beginning. It will work out and you will discover nice features: like I had to print a picture with certain dimension and you just can set it by opening the pic and printing it with the dimension. As well as you can invert the screen's colors ("Windows" key + M) so you can finally read some stuff on your laptop in the sun or just give your eyes more rest while reading PDF-files... So many nice features you will love! :D

But it is a challenging (and still is). However there are a lot of nice people out here to help :D

---

### Post by cheesekiller on 2011-03-19
I first put Ubuntu on my netbook 3 months ago.    Now I run everything on Ubuntu including the computers that my business uses. (except one computer that is used for quickbooks, But i possibly see virtual box correcting that in the near future)

---

### Post by Vodkaholic on 2011-03-22
Thanks for the info :)

Ive got the Ati Catalyst Contol Center up and there is no one to set a default monitor..

Has anyone any idea how I can do this?
Editing the montior.xml gives me a tty1 log in screen after I reboot >.>

---

### Post by coweatyou on 2011-03-22
> **Vodkaholic said:**
> Thanks for the info :)

Ive got the Ati Catalyst Contol Center up and there is no one to set a default monitor..

Has anyone any idea how I can do this?
Editing the montior.xml gives me a tty1 log in screen after I reboot >.>
Is there any reason you need to use the ATI driver.  The proprietary FGLRX driver available from the Ubuntu dev's is much less buggy then the one off the ATI site (it took me 2 reinstalls to get the ATI driver working correctly).

If you need the ATI drivers, did you run 'aticonfig --initial' after installing the driver?

---

### Post by Vodkaholic on 2011-03-22
> **coweatyou said:**
> Is there any reason you need to use the ATI driver.  The proprietary FGLRX driver available from the Ubuntu dev's is much less buggy then the one off the ATI site (it took me 2 reinstalls to get the ATI driver working correctly).

If you need the ATI drivers, did you run 'aticonfig --initial' after installing the driver?

Hmm when I installed ubuntu this popup box poped up saying Additional Drivers, So I just clicked Activate. Was that the right thing to do?
aticonfig --initial? hmm no ive not done anything to do with this (no idea what it is also)

Thanks

Edit the drivers seem to work but I just can't change the default monitor.

---

### Post by coweatyou on 2011-03-22
> **Vodkaholic said:**
> Hmm when I installed ubuntu this popup box poped up saying Additional Drivers, So I just clicked Activate. Was that the right thing to do?
aticonfig --initial? hmm no ive not done anything to do with this (no idea what it is also)

Thanks

Edit the drivers seem to work but I just can't change the default monitor.

Good, you are using the right driver.  Can you show us the text of your xorg.conf file?

---

### Post by Vodkaholic on 2011-03-22
```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "0-DFP4"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "75"
	Option	    "Position" "1680 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP4" "0-DFP4"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
	SubSection "Display"
		Virtual   2960 1050
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   2960 2960
		Depth     24
	EndSubSection
EndSection

```

Thanks

---

### Post by Vodkaholic on 2011-03-22
Was that the right file?
Thanks

---

