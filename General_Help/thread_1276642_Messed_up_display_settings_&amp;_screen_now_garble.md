---
title: "Messed up display settings &amp; screen now garbled after boot.  HELP!!!"
date: 2009-09-27
forum: General Help
---

### Post by Blakeman on 2009-09-27
OS is Ubuntu 9.04, video card is ATI Fire GL V5600 using proprietary ATI drivers (which just barely work, but are very finicky).  I turned on my dual monitor (or turned off “mirror monitors”) and adjusted my monitors’ resolution.  Looked a little funny after my adjustments, but selected OK anyway.  Upon reboot, I can see BIOS just fine, GRUB works fine, and I can see the UBUNTU title with progress bar under it, but then everything goes to h@ll when the desktop pops up.  I can tell it is the desktop, but it is seriously pixalized and partially blanked out.  Sufice to say I cannot see enough intelligent data to do anything, particularly get back to my “display settings” to correct my little issue.

OK, so what now?  I am a Windows guy so a little extra clarification is likely required by you Linux gurus. I could really use some help here folks.  I appreciate the help, thanks, -blake

---

### Post by DJonsson2008 on 2009-09-27
you likely will need to restore your xorg.conf file,
especially if your gui is not working well you will
need to drop to command prompt using alt-f1 and get
to your etc/X11 directory...

do you know any dos commands? for now 

ls = dir (list directory)

cd = cd (change directory)

so cd /etc/X11

now things get touchy

so backup your xorg.conf

cp xorg.conf.bad.bak

and then open it up to edit it.

sudo gedit xorg.conf

be careful what you change, but if you 
can quickly identify your resolution 
setting in the script edit it back to what it was
save and try rebooting.

Below is my section "Screen" if I was in your
situation I'd try changing the to revert in my 
subsection "Display"

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

---

### Post by DJonsson2008 on 2009-09-27
to clarify the line 
Virtual	1024	768
in the subjection "Display"
is the switch I'd revert.

NOTE: remember to backup your xorg.conf files.
      once you have something that works back it
      up naming it something like xorg.conf.1024.works.ok.bak

---

### Post by Blakeman on 2009-09-27
I am able to get to the command prompt and navigate to the etc/X11 directory.  I have made a copy of the xorg.conf file.  I get the following error with your command to edit the file:

Command:  sudo gedit xorg.conf

Result: (gedit:2235): Gtk-WARNING **: cannot open display:

What am I doing wrong?  Thanks again for the help, -blake

---

### Post by DJonsson2008 on 2009-09-27
sounds like gnome isn't loaded 
you will need to use another editor.
 
nano instead of gedit...

nano xorg.conf

---

### Post by Blakeman on 2009-09-27
Well the Nano helped, but the editing the file did not.  Fortunately I was able to copy and restore and older xorg.conf file and get the system back up and running.  Thank you for the help.

For those other Windows to Ubuntu users, here is what I did:

To correct display settings when booting:

1) Reboot computer, get through BIOS to Grub

2) Select (recovery mode)

3) In the Recovery Menu, select ROOT (drop to root shell prompt)

4) Change directories to X11, thus type:

	cd /etc/X11

5) Backup xorg.conf file, thus type:

	cp xorg.conf xorg.conf.bad.bak  

(note, this is telling the OS to copy (cp) the selected file (xorg.conf) and name the copied file (xorg.conf.bad.bak)

6a) If so required & you know what you need to type, edit xorg.conf, type:

	nano xorg.conf

6b) Instead of editing, look for older display configurtion backup, thus type:

	dir

7) Look for any BAK files (i.e. xorg.conf...bak) or I chose to utilise my file with the date in its name:

	xorg.conf.20090925184943

8) I then copied and renamed the file as the default display setting, thus type:

	cp xorg.conf.20090925184943 xorg.conf   

(note that you would change the first part to be copied to match the name of your backed up file)

9) Reboot the computer, thus type:

	reboot

---

### Post by DJonsson2008 on 2009-09-28
One warning that should always be
in this discussion -- is that I've yet to see
it happen but at least in theory it seems somebody
can fry their monitor if they ratchet up their 
resolution too high in the process of messing with
xorg.conf. 

Thats why I was reluctant to mention restoring 
xorg.conf via a previous backup, on this thread.

If you make any change to your Xorg.conf monitor settings
make sure they are within range of the MFG specs. As well
if restoring a previous conf its best to take a look at it 
first and make sure one is within mfg specs for the display.

If in doubt it may be wise to error on the side of caution with
a lower resolution and refresh rate, backup that xorg.conf after testing and then migrate to higher/res refresh rates within the display model mfg specs.

---

