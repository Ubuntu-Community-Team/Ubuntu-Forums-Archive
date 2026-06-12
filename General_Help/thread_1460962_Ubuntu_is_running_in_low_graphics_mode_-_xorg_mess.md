---
title: "Ubuntu is running in low graphics mode - xorg messed up"
date: 2010-04-23
forum: General Help
---

### Post by Sloppyunderfoot on 2010-04-23
My issue began with my resolution changing to 800x600 in Karmic Koala and then my inability to change it back to anything else. In my haste to fix it before going to work this morning I loaded a new xorg.conf without backing up the old xorg.conf with data not relevant for my monitor and now I'm in limbo.  The good news, I hope, is that I also run 8.04 on the same computer so I do have access to what I hope is proper xorg.conf / I've modified the existing xorg.conf file and I'm still getting the "low graphics mode" message (EE) problem parsing the config file and (EE) Error parsing the config file. Fatal Server Error: no screens found.  Your suggestions are requested and appreciated.  I'm happy to provide any information I can. Thank you

---

### Post by 666f6f on 2010-04-23
Hi Sloppyunderfoot,

Can you post the 8.04 xorg.conf? It'll certainly help.

---

### Post by john newbuntu on 2010-04-24
Hopefully this helps:
[http://ubuntuforums.org/showthread.php?p=8595940](http://ubuntuforums.org/showthread.php?p=8595940)

---

### Post by Sloppyunderfoot on 2010-04-24
Thanks very much for your assistance.
I put the following in yesterday and it worked great.  Today I booted up and I'm back to 800x600.

Section "Device"
  Identifier "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
  Driver "intel"
  BusID "PCI:0:2:0"
EndSection

Section "Monitor"
  Identifier "DELL 1800FP"
  Option "DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor	"DELL 1800FP"
	DefaultDepth 24
	SubSection "Display"
		   Modes "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by Sloppyunderfoot on 2010-04-24
John, thank you for pointing me to this thread.  It worked like a charm until I rebooted the computer and I lost the settings and it went back to 800x600.

---

### Post by john newbuntu on 2010-04-25
Did you make any permanent changes? See the post links below.

This posts suggests changing your resolution in /etc/gdm/PreSession/Default
[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

This one suggests altering /etc/gdm/Init/Default
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

Fortunately/unfortunately, I did not encounter these problems and so I have not tried these.

---

### Post by 666f6f on 2010-04-25
If the relevant posts that John suggested don't help, have a look bellow.

> **Sloppyunderfoot said:**
> I put the following in yesterday and it worked great. Today I booted up and I'm back to 800x600.

1. I'm sorry, not following. Have you tried the xorg.conf you posted earlier? It seems promising.

2. Also, what editor did you use to edit your xorg.conf? I'm asking because gedit takes a backup of the file before editing (unless you've changed that in the prefs). You can find the backup file here /etc/X11/xorg.conf~, if you edited  with gedit.

3. You may also try to work without a configuration file and let the system to be auto-configured. Use the following command to do that: ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Some notes

1. You don't have to restart your system each time you make a change, you only have to restart X. Logging-out and logging back in or hitting Ctrl+Alt+Backspace should be sufficient.

2. For your information, here are some relevant man(ual) pages you can consult:
man intel
man xorg.conf

Usually man pages (and distro manuals, like this: [http://www.freebsd.org/doc/en/books/handbook/x-config.html](http://www.freebsd.org/doc/en/books/handbook/x-config.html)) contain much higher quality and quantity of information than any post you'll find on the internet.

---

### Post by Sloppyunderfoot on 2010-04-25
I edited this one  "/etc/gdm/Init/Default" and the changes did "stick" in the file however, the resolution changed back to 800x600.  I'll try the other, too.

---

### Post by Sloppyunderfoot on 2010-04-25
I did try the xorg.conf that was posted.  I rebooted the machine and it stayed however, I shut the computer down for the evening and when I booted up the next day I was back to 800x600.  I'm pretty sure that I edited the file using vim.  I'm going to edit the /etc/gdm/PreSession/Default file and see what happens. They I'll try the autoconfig.  Thanks very much for your suggestions.

---

### Post by 666f6f on 2010-04-25
OK, sounds a good plan, just keep in mind to keep a backup of the files you edit, it may save you time later.

---

### Post by Sloppyunderfoot on 2010-04-25
I edited the /etc/gdm/PreSession/Default file and have restarted X twice and restarted Ubuntu once.  Resolution has remained at 1024x768 as I wanted.  Hopefully, this has done the trick.  I don't know what happened to cause this issue however, I appreciate everyone's efforts to assist me.. Thanks very much.

---

### Post by 666f6f on 2010-04-26
Great, really glad you solved the problem. Have a nice week!

---

