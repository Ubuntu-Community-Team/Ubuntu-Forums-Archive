---
title: "Autopackage .package install?"
date: 2011-01-21
forum: General Help
---

### Post by casbahdk on 2011-01-21
The school that I work at uses smartboards that have a Linux version of the software (SMART Notebook), but it is only provided as an autopackage .package [Autopackage]("http://www.autopackage.org/") hasn't been supported for some years now and I am using Linux Mint 9 LXDE (Ubuntu 10.4). How can I install the software?

---

### Post by nothingspecial on 2011-01-21
I pretty sure the autopackage installer is included in the smartboard tar.gz download.

What have you actually got at the moment? Have you unpacked it?

---

### Post by casbahdk on 2011-01-21
Thanks for the quick reply. It is a .package file. It can be opened in a text editor like Leafpad or Gedit. It looks like a shell script, but I can't see whether somehow the software is included or if it is downloaded. You can see what I have been able to extract [here]("http://pastebin.com/UcFqkL7h").

---

### Post by nothingspecial on 2011-01-21
There should be a README text file included in the download. 

I haven`t done this for over a year. What does it say?

---

### Post by alaukikyo on 2011-01-21
you just have to Right Click -> Properties -> Permissions(Tab) and select Allow Executing.
no you can just double click the file and run it.

---

### Post by casbahdk on 2011-01-21
Yeah you would think that it would be that easy wouldn't you? However, it isn't. No ReadMe file is provided. The file is already set to executable, but I get the following error message: ```
Failed to execute child process "/home/user/downloads/smartboard" (No such file or directory)
```

---

### Post by nothingspecial on 2011-01-21
Is the autopackage script in the same directory as the smartbook source?

---

### Post by casbahdk on 2011-01-21
OK, I changed the file name and ran bash from the command line: ```
$ bash notebook_software_copy.package
``` The script presents the user with two possibilities, to use an existing .tar file that wasn't included, or to download autopackage from the Internet. I chose the latter. The download completed fine. Then I got my first error: ```
/usr/bin/xauth:  creating new authority file /root/.Xauthority
Refreshing linker cache, please wait ... done
Your system is missing v5 of the C++ support library, putting a copy in /usr/lib
Refreshing linker cache again, please wait ... done
``` autopackage started the install and then I ran into the following error, sixty eight times: ```
QGtkStyle was unable to detect the current GTK+ theme.

(process:20265): Gtk-CRITICAL **: IA__gtk_widget_style_get: assertion `GTK_IS_WIDGET (widget)' failed
```

I am of course assuming that this is because I don't have either GNOME or KDE on my system - but is this a problem?

Then comes some more errors ```
Creating symlink, libtiff.so.4 -> libtiff.so.3
/usr/bin/chcon: can't apply partial context to unlabeled file `/opt/SMART Technologies/common/lib/libxerces-c.so.28'
QGtkStyle was unable to detect the current GTK+ theme.

QGtkStyle was unable to detect the current GTK+ theme.
Failed to load definitions
HashVerifier: message hash not valid
/usr/bin/chcon: can't apply partial context to unlabeled file `/opt/SMART Technologies/Notebook Software/bin/Notebook/supportlibs/libruby.so.1.8'
QGtkStyle was unable to detect the current GTK+ theme.
tar: This does not look like a tar archive
tar: Exiting with failure status due to previous errors
QGtkStyle was unable to detect the current GTK+ theme.
Checking connection to: http://downloads01.smarttech.com/software/efe
Check succeeded.
Done.

Executing post install script for: SMARTBoardDrivers
Executing post install script for: SMARTBoardDrivers
```

Are any of these errors fatal and what do I do about it?

Then comes the following, but I assume it is looking for a smartboard that I am not connected to at this time? ```
$ retry 1, found num_rsp=-1
retry 2, found num_rsp=-1
retry 3, found num_rsp=-1
retry 4, found num_rsp=-1
retry 5, found num_rsp=-1
retry 6, found num_rsp=-1
retry 7, found num_rsp=-1
retry 8, found num_rsp=-1
retry 9, found num_rsp=-1
retry 10, found num_rsp=-1
sh: /opt/SMART Technologies/SMART Product Drivers/bin/aware/Aware: not found
```

If either of you could make heads or tails of this, I would really appreciate it.

---

### Post by nothingspecial on 2011-01-21
It looks like you need gnome or kde or atleast some gtk libraries.

---

### Post by casbahdk on 2011-01-21
> **nothingspecial said:**
> It looks like you need gnome or kde or atleast some gtk libraries.

The question is which libraries? I am running the program from the console as a test and get the following error messages: ```
test
HashVerifier: message hash not valid
HashVerifier: message hash not valid
HashVerifier: message hash not valid
HashVerifier: message hash not valid
libpng warning: Incomplete compressed datastream in iCCP chunk
libpng warning: Profile size field missing from iCCP chunk
libpng warning: Incomplete compressed datastream in iCCP chunk
libpng warning: Profile size field missing from iCCP chunk
libpng warning: Incomplete compressed datastream in iCCP chunk
libpng warning: Profile size field missing from iCCP chunk
libpng warning: Incomplete compressed datastream in iCCP chunk
libpng warning: Profile size field missing from iCCP chunk
libpng warning: Incomplete compressed datastream in iCCP chunk
libpng warning: Profile size field missing from iCCP chunk
/opt/SMART Technologies/Notebook Software/bin/Notebook/resources/ruby_support/notebook_animation.rb:1041: warning: parenthesize argument(s) for future version
/opt/SMART Technologies/Notebook Software/bin/Notebook/resources/ruby_support/notebook_animation.rb:1615: warning: parenthesize argument(s) for future version
libpng warning: Incomplete compressed datastream in iCCP chunk
libpng warning: Profile size field missing from iCCP chunk
libpng warning: Incomplete compressed datastream in iCCP chunk
libpng warning: Profile size field missing from iCCP chunk
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 3 (X_GetWindowAttributes)
  Resource id:  0x3200390
xscreensaver-command: not active: idle timer reset.

xscreensaver-command: not active: idle timer reset.

xscreensaver-command: not active: idle timer reset.

xscreensaver-command: not active: idle timer reset.

xscreensaver-command: not active: idle timer reset.

xscreensaver-command: not active: idle timer reset.

xscreensaver-command: not active: idle timer reset.

```

---

### Post by marenkar on 2011-06-23
Has anyone solved this yet?

---

### Post by casbahdk on 2011-06-30
> **marenkar said:**
> Has anyone solved this yet?

Nope

---

