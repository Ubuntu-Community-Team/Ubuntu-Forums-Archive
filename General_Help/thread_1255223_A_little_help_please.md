---
title: "A little help please"
date: 2009-09-01
forum: General Help
---

### Post by Dalek Draco ON LINUX on 2009-09-01
Hi all, I'm back for more help lol.  I've got my system going well (or I've messed up things so badly that it works anyway :P).  A few questions, I'm trying to install BitDefender antivirus, but when I run it in terminal (i had to click open with 'bash', after running around trying to find out how to make it open lol).  Anyway....when I open it in the terminal, it makes me tap enter until all the licence agreement has appeared, and then says enter 'accept', which I do, then it says 'dpkg: requested operation requires superuser privilege  Could not complete the installation of the package, aborting.'  It's a .deb.run file...I went to terminal and typed su and then it asked for a password (but my login password didnt work). Please can someone help.  Also on a completely different issue, the beep noise when I shut down is annoying, I've got every setting that it could possibly be off, and it still beeps when I shut down.  And just to be a pain in the ****, firefox says its v3.0.13, but last time I was on windows I'm pretty sure it was v3.5 odd, is my firefox outdated? it wont let me check for an updated version through help.  Oh almost forgot (everyone runs away in frustration) does anyone know if pidgin messenger works with webcams (video calling like on msn) or if not, of another program available to replace it.   Finally...I hope....could someone PLEASE tell me what the difference is between the programs you can get from add/remove, and the ones you get from synaptic package manager? Driving me insane....thanks.

---

### Post by dearingj on 2009-09-01
Regarding Firefox: The one you have installed in Ubuntu is 3.0.13. You can install firefox by installing the firefox-3.5 package in Synaptic.

Regarding the difference between Add/Remove and Synaptic: I don't think there is a difference, except that Add/Remove is designed to be more user-friendly whereas Synaptic has more advanced features for more advanced users.

---

### Post by 3rdalbum on 2009-09-01
Firstly, you don't need an anti-virus program on Linux, unless you transfer documents to and from Windows computers and you don't want to pass their viruses back to them.

Secondly, "su" doesn't work on Ubuntu. You either prefix a command with "sudo", for instance:

```
sudo apt-get dist-upgrade
```

Or you open a root terminal:

```
sudo -i
```

If you absolutely must have an anti-Windows-virus program, and you don't want to use ClamAV that's in the repositories, then you need to run the BitDefender installer as root, with sudo.

---

### Post by muteXe on 2009-09-01
Or
```

gksudo <appName>

```
if you're wanting to open a graphical application.

---

### Post by Dalek Draco ON LINUX on 2009-09-01
Thanks I've managed to get Bitdefender installed, the sudo thing worked.   Just need to know  a) if there is good alternative to pidgin that someone can recommend, that works with webcam viewing.  b) how to stop the damn BEEP when I press shut down (I've turned all sound options off and it still does it. Quite embarrassing in a lecture).  Thanks in advance.

---

### Post by Dalek Draco ON LINUX on 2009-09-02
bump...:D

---

### Post by theozzlives on 2009-09-02
If you install gnome-alsamixer, there's an option to mute the system beep. Don't knoe about the cam as I've never used or needed one.

---

### Post by P4man on 2009-09-02
Put pcspkr is the modprobe blacklist.
```

gksudo gedit /etc/modprobe.d/blacklist.conf
```

add:
```
blacklist pcspkr
```

edit: wojox' solution might work too ROFL :)

---

### Post by wojox on 2009-09-02
If alsa-mixer doesen't work, open a terminal:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Then add at the end of the file:

```
blacklist pcspkr
```

You have to reboot for it to work.

Same here sorry don't use video camera thigymajigs.

---

