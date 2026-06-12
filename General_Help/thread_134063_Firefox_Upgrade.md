---
title: "Firefox Upgrade???"
date: 2006-02-21
forum: General Help
---

### Post by Heliman on 2006-02-21
Hi gang,

I am new to linux and looking for some help.  Right now I have 3 questions.  I have a P4 3.2ghz computer with 1 gig of ram. 1 Drive for Windows, 1 Drive for Backup, 1 Drive for Linux.  I switch from Linux to Windows through my bios boot panel.  I loaded Ubuntu Breezy with gnome desktop and then later loaded the KDE desktop.  I am currently using the KDE Desktop.  Everything is working except my printer.

1.  I could not find a driver for my Canon Pixma 5000 printer.  I did find turboprint and loaded it.  Turboprint works, however, there is a turbo print logo that prints on every page until I purchase the package.  Are there any other options available?

2.  I installed automatix and noticed that firefox is not running the current version.  I am still running 1.07.  I have read the other threads regarding Firefox and I am a little confused.  What do I need to do to run the latest version.

3.  I think there is a way I can read files from my windows drive, so that I can copy documents and photos from my windows drive to my linux drive.  Could someone point me in the right direction.

Thank you in advance for your help.

Regards,
Heliman:D

---

### Post by batty505 on 2006-02-21
Hey

for  accessing windows files on ubuntu, I can help with that!:) 

I have a couple of windows servers, and samba is already built in.
I just connect to the windows servers with my login ids and pw. works fine
its under; places|connect to server, and work from there.

be careful of the keyring thingie. <g> I thought it was some kind cached pw, kept local, but I didnt write it down. now it wants it everytime I try an mount or connect to that volume.

hth.
Mike

---

### Post by Heliman on 2006-02-21
Bump

---

### Post by o_fortuna on 2006-02-21
[QUOTE=Heliman]Hi gang,

I am new to linux and looking for some help.  Right now I have 3 questions.  I have a P4 3.2ghz computer with 1 gig of ram. 1 Drive for Windows, 1 Drive for Backup, 1 Drive for Linux.  I switch from Linux to Windows through my bios boot panel.  I loaded Ubuntu Breezy with gnome desktop and then later loaded the KDE desktop.  I am currently using the KDE Desktop.  Everything is working except my printer.

1.  I could not find a driver for my Canon Pixma 5000 printer.  I did find turboprint and loaded it.  Turboprint works, however, there is a turbo print logo that prints on every page until I purchase the package.  Are there any other options available?

2.  I installed automatix and noticed that firefox is not running the current version.  I am still running 1.07.  I have read the other threads regarding Firefox and I am a little confused.  What do I need to do to run the latest version.

3.  I think there is a way I can read files from my windows drive, so that I can copy documents and photos from my windows drive to my linux drive.  Could someone point me in the right direction.

Thank you in advance for your help.

Regards,
Heliman:D[/QUOTE]
Since I'm a backwards sort of person, we'll start with number three:

Use the command line (Applications-->Accessories-->Terminal) to type this in:
```
mkdir /media/windows
sudo mount /dev/hda1 /media/windows -t ntfs -o nls=utf8,umask=0222
```
Note that for the above, hda1 is where windows is on your partition table. If you are using a SATA drive, it's probably sda1. And note that you can't write to NTFS from linux, at least not easily. If you want it automatically to appear as an icon on your desktop, do this:
```
sudo gedit /etc/fstab

<<add this to the end of the file>>

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```
This stuff was shamelessly ripped from [MountingWindowsPartitions]("https://wiki.ubuntu.com/MountingWindowsPartitions?highlight=%28ntfs%29")

Number 2: For best results, post in the Automatix thread. Arnieboy has record-speed response time. However, you can probably fix the problem by just running Automatix again and reselecting Firefox 1.5. If it still doesn't work, click on the desktop, click Create Launcher, type in firefox in the name, and type /opt/firefox/firefox in the command box. That should run it, and you can drag it to the panel.

Number 1: Well, I don't use Canon, and I understand that their support for linux stinks. [This]("http://www.linuxprinting.org/pipermail/canon-list/2004q4/001797.html") is all I could find. Try it out, although you won't get great quality, at least you won't have a big logo on all your printing.

---

### Post by Rouge8 on 2006-02-21
Also, if you can try to install Windows 2000/XP in a VMware virtual machine, and you should be able to print through that. ;)

I have a Lexmark printer, and that's what I do. :P

---

