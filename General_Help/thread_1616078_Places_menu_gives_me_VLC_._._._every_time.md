---
title: "Places menu gives me VLC . . . every time"
date: 2010-11-07
forum: General Help
---

### Post by cloyd on 2010-11-07
The strangest thing has happened. I was burning a mp3 cd for my car stereo with brasero. I had to slow the thing down as slow as it would go to get a good disc, and while brasero was loaded, I clicked on one of the mp3 files within brasero. It opened with VLC. Now, all the top half of the item in my "Places" menu . . . home, desktop, documents, etc, open VLC and try to load a file and then give an error message because usually it is not a media file. What happened? How do I fix it? Using 10.10.  Gateway MD7818U.
I'll keep working on it . . . but I could use some help.
output of lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation WiFi Link 5100
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller (rev 10)
07:09.0 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 03)
07:09.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)


Edit. I've tried removing the menu from the panel and then adding it back. No change.

---

### Post by papibe on 2010-11-07
There's a way to reset all your gnome settings to its defaults (Warning: if you have spend time customizing your desktop you may want to avoid it).

Press Alt-Ctrl-F1
Login to your account in text mode. Then
```
$ sudo service gdm stop
$ rm -rf .gnome .gnome2 .gconf .gconfd .metacity
$ sudo service gdm restart
```
If you have kubuntu, change gdm for kdm. Try changing the file association again.

Good Luck!

---

### Post by cloyd on 2010-11-07
Well, the situation as it is is totally unacceptable. I can get to my files in gnome with the computer icon . . . that is the only one which works. Then, if I try to create a new link to any folder, the option is greyed out.  Then . . . get this. I used "sudo nautilus" and it would let me create a link to a folder. However, when I tried to use that new link . . . guess what? VLC. I like VLC but I need other things.

I will probably use you advice in a few minutes. Customizing the desktop won't take that long. Just wish I knew what happened.

---

### Post by papibe on 2010-11-07
Well, it looks pretty bad. Tell us later if you were able to fix it.

Good Luck!

---

### Post by cloyd on 2010-11-07
Well, I reset everything. Still get VLC. Somebody have any idea?

---

### Post by cloyd on 2010-11-07
Ok something else. I can create a link to a folder within nautilus. Without sudo.  I can move the link onto the desktop and it works. But when I place a link on a panel or in docky, the it takes opens VLC.

More . . . uninstsall VLC, all is all right again. But reinstall VLC . . . things are haywire again. Any ideas?  I'd just get rid of VLC, but I really like it for video. And I like my lauchers and links in panel . . . I like conky and the otherwise clean screen.

---

### Post by Quackers on 2010-11-07
Can you create a new user then log out and log in as that new user? How are things then?

---

### Post by cloyd on 2010-11-07
I may try that in a little while. Right now, I tried uninstalling VLC with apt-get purge. Now, I am reinstalling it.

---

### Post by cloyd on 2010-11-07
That worked. Now . . . how to access all my old files and such from the other user account . . .

---

### Post by Quackers on 2010-11-07
I don't know about that, unfortunately. It may be a case of comparing settings. It may be a case of deleting the old user and creating a new one with the same name but I would wait for clearer advice first. I have no idea if that could be a serious problem to your system!!!! Hopefully somebody will be along soon with better info.

---

### Post by garvinrick4 on 2010-11-07
Just open nautilus and right click a directory and choose open with other application then choose open with file browser and check mark the box open all folders like this with this. 
 You were just opening VLC with right click on music or video directory and VLC starting opening everything. Open VLC then choose to open directory and navigate to directory and open when using VLC.
 
terminal 
```
nautilus
```or ALT/F2 and type in nautilus  file browser will open.

---

### Post by cloyd on 2010-11-07
I thank you very much. I was setting up a new account, and trying to understand how to move things over and permissions were giving me a hard time.  . . . as I did move some, I may have a bit of cleaning up to do. Again, thanks.

---

