---
title: "Shared Printer Authentication Popup Question"
date: 2010-07-20
forum: General Help
---

### Post by MikeyDL on 2010-07-20
I'm running Ubuntu 10.04 desktop on vmware on one of my computers.  I have a local printer in Win7 shared with windows permissions set to allow printing and management for the everyone group (and it's shared).  I've got the printer setup on the Ubuntu desktop as an smb printer (smb://dirk/LexmarkE260).  It works fine except for an annoying authentication popup that keeps coming up for every print job.  I've tried to save the password (checkbox) but it keeps popping up regardless.  The print driver is a generic PCL5e driver (the lexmark one messes up on PDF files).  

Any tips or ideas how I can save the authentication information so I don't have to keep entering my domain/user plus password for each print job?

---

### Post by MikeyDL on 2010-07-21
I've been fiddling with permissions on the windows side more but can't seem to get this annoying thing to stop.

Also can't seem to find a place to enter permissions in the printer options dialog.  The funny thing is that the lexmark driver doesn't do this but I can't print out PDF's with it :(

---

### Post by Morbius1 on 2010-07-21
The Windows printer is set up to allow access to everyone so I don't know why it's asking for a password.

Two possibilities that come to mind:

(1) There's a windows bug that goes back to WinNT. Windows gets confused over the concept of guest so you have to make it explicit to it:

```
 gksu gedit /etc/cups/printers.conf
```Look for a line that looks like this:

>  DeviceURI smb://dirk/LexmarkE260and change it to
>  DeviceURI smb://[COLOR=Blue]guest[/COLOR]@dirk/LexmarkE260You'll have to restart cups:
```
sudo service cups restart
```(2) You've got "Windows Live Sign-In Assistant" installed on the Win7 Box:
[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)

---

