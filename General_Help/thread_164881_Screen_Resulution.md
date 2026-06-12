---
title: "Screen Resulution"
date: 2006-04-23
forum: General Help
---

### Post by cssutto on 2006-04-23
I have a Sony LCD SDM-HS-95P LCD display and I can not set the resolution properly.

It is like reading the fine print on a used car sales contract.

I want 1280 x 1024.

Thansk for any help.

CSSJR

---

### Post by sinkxdie on 2006-04-23
Im guessing you tried the Screen Resolution tool?
System>Preferences>Screen Resolution
Are there any buttons on the monitor?

---

### Post by cssutto on 2006-04-23
The monitor buttons will not work because the computer is over riding it.

I tried sudo gedit /etc/X11/xorg.conf

Added 1280x1024 and rebooted, but it is still the same.

That tile looks like this:  

I added the first line, as suggested in another thread and when that did not work, changed the orignal first line, all with no results.

So the question is, which line is it reading from?  I would think each of these lines would have a different resolution so that in the Gnome screen page, one would have a choice.

At any rate, this is very very hard on the eyes.

CSSJR


Section "Device"
	Identifier	"ATI Technologies, Inc. FireGL Mobility 7800 (M7 LX)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. FireGL Mobility 7800 (M7 LX)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		1
		Modes		"1280x1024""
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by JasonL on 2006-04-23
You have to put the resolution for every single mode. so replace all 1600x1200 with 1280x1024

---

### Post by cssutto on 2006-04-23
That totally crashed Gnome.

I get the command line and the message that X is not set up correctly.

This will have to be fixed from the command line and I have no idea how.

CSSJR

---

### Post by sinkxdie on 2006-04-23
Did you try 
```
startx
```? 
That probably didn't work. 
Place the output of that here.
As an alternative you can try 
```
sudo apt-get update
sudo apt-get dist-upgrade 
```
                 ...Assuming you have root permissions.

---

### Post by sinkxdie on 2006-04-23
Also if it helps,
My xorg.conf file
[http://pastebin.com/678121](http://pastebin.com/678121)

---

### Post by e-rebus on 2006-04-23
[QUOTE=cssutto]I have a Sony LCD SDM-HS-95P LCD display and I can not set the resolution properly.

It is like reading the fine print on a used car sales contract.

I want 1280 x 1024.

Thansk for any help.

CSSJR[/QUOTE]

You can try adding Horizontal and Vertical refresh rates of your monitor, like so:

	Section "Monitor"
	  Identifier  "Samsung"
	  Option      "DPMS"
	  HorizSync    30-81		# horizontal refresh frequencies
	  VertRefresh  56-75		# vertical refresh frequencies
	EndSection

I had the same problems with resolution on my Samsung 173p, that fixed them.

Hope this helps.

---

### Post by cssutto on 2006-04-23
Update will not work.

It was my understanding that you have to have a connection out to update, and I have a wierd modem problem that is such that I will probably never get it to work from the command line.

Unless there is a command line method of fixing x, I probably will have to do a complete reinstall and with my modem problem, all of those updates take an entire day.

Not to pleasing.

CSSJR

---

### Post by robglinka on 2006-04-23
Well you have two options. If you used gedit, it auto backed up your last save as xorg.conf~ (note the tilde).

So you can always revert back to your last save with - 

```

cd /etc/X11
sudo cp xorg.conf~ xorg.conf

```

If that doesn't solve the problem... your second option is to edit your xorg.conf file from the command line. Now is a great time to learn how to use the best application ever, vi.

Oh, and a little tip. If you're going to be working with config files. Always back them up before you start changing them. Save your last known working config file before you edit it.

Log into your ubuntu install, then type 
```

cd /etc/X11
sudo cp xorg.conf xorg.conf_backup
sudo vi xorg.conf

```

You might want to hit [www.google.com](www.google.com) and look around for a vi manual. You're going to have to use i to insert text, x to delete text, and the esc. button to change from insert mode to normal mode.

vi is a bit complicated to learn, but you're going to need it if you want to edit txt files without a gui.

-rob

---

### Post by JasonL on 2006-04-24
Is it at all possible you type something slightly wrong? One little mistake can mean that the xserver cannot read the .conf file. Try

```
sudo nano /etc/X11/xorg.conf
```

And just check it over for errors. If not did you make a backup of your xorg.conf, this should be made everytime before you edit it. Hope this helps.

---

### Post by cssutto on 2006-04-24
Rob:

Gone since last night and just got back and saw your


Code:
cd /etc/X11 sudo cp xorg.conf~ xorg.conf

That got me back to an operating system, even though the resolution is not correct.

Thank you.

I though of another way while I was gone, but your way worked so I did not try it, but I could have copied my post showing the file as it was before it crashed to a floppy and from the command line copied the floppy into the destination file.

I think from now on I will copy to a floppy because that is one simple command.

Until I lean more about linux.

Thank you.  You saved my hide.

CSSJR

---

### Post by cssutto on 2006-04-24
Rob:

This got me back to where I was, so I have a working system anyway.


Code:

cd /etc/X11 sudo cp xorg.conf~ xorg.conf



Still have not got the resolution where I want it.

Thatks.

CSSJR

---

### Post by robglinka on 2006-04-24
If you know you're only going to be using one resolution all the time, you can give this a shot. I don't know if it will work for sure with you monitor.

Just remember, backup your xorg.conf file before you edit it, so you can revert back if X doesn't start.

Also, the quickest way to test the xorg.conf is to log out to the login screen, then hit <ctrl><alt><backspace> and Xorg will restart.

Replace the relevent sections with this:
```

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 30-82
VertRefresh 56-76
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. FireGL Mobility 7800 (M7 LX)"
Monitor "Generic Monitor"
DefaultDepth 24
Subsection "Display"
Depth 24
Modes "1280x1024"
EndSubsection
EndSection

```

---

### Post by cssutto on 2006-04-24
Rob:

That worked perfectly on the first try.

I really appreciate it.

The resolution I had was enough to make a guy go blind.

CSSJR

---

