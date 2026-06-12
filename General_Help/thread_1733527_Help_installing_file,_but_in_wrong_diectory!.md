---
title: "Help installing file, but in wrong diectory!"
date: 2011-04-19
forum: General Help
---

### Post by Advice Pro on 2011-04-19
I have a file in *Downloads* called *qjoypad-4.1.0.tar.gz* and want to install it via the terminal.  This command:
```

tar -xzvf qjoypad-4.1.0.tar.gz
```

gave me this error:
```

tar: qjoypad-4.1.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
```

I think this means that I'm not in the current directory.  How would I change to the current directory and then install.  The path of the file is */home/lapiii/Downloads/qjoypad-4.1.0.tar.gz* and the current directory is */home/lapiii*, obtd. via com. *pwd*

---

### Post by WorMzy on 2011-04-19
```
cd /home/lapiii/Downloads/
```

or, if you're logged in as lapiii

```
cd ~/Downloads/
```

---

### Post by ~Plue on 2011-04-19
maybe it would be a lot easier for the OP to use a debian package?
[http://archive.getdeb.net/getdeb/ubuntu/pool/games/q/qjoypad/](http://archive.getdeb.net/getdeb/ubuntu/pool/games/q/qjoypad/)

---

### Post by Advice Pro on 2011-04-19
> **~Plue said:**
> maybe it would be a lot easier for the OP to use a debian package?
[http://archive.getdeb.net/getdeb/ubuntu/pool/games/q/qjoypad/](http://archive.getdeb.net/getdeb/ubuntu/pool/games/q/qjoypad/)

What's the beneficial difference between these files and *qjoypad-4.1.0.tar.gz*?

I had ran:
```
cd ~/Downloads/
tar -xzvf qjoypad-4.1.0.tar.gz
```

Which output:```
./qjoypad-4.1.0/
./qjoypad-4.1.0/README.txt
./qjoypad-4.1.0/LICENSE.txt
./qjoypad-4.1.0/src/
./qjoypad-4.1.0/src/event.h
./qjoypad-4.1.0/src/keycode.cpp
./qjoypad-4.1.0/src/axis_edit.cpp
./qjoypad-4.1.0/src/layout_edit.cpp
./qjoypad-4.1.0/src/buttonw.cpp
./qjoypad-4.1.0/src/joyslider.h
./qjoypad-4.1.0/src/joypadw.h
./qjoypad-4.1.0/src/button_edit.h
./qjoypad-4.1.0/src/quickset.h
./qjoypad-4.1.0/src/joypad.cpp
./qjoypad-4.1.0/src/axisw.cpp
./qjoypad-4.1.0/src/qjoypad.pro
./qjoypad-4.1.0/src/main.cpp
./qjoypad-4.1.0/src/icon.h
./qjoypad-4.1.0/src/joyslider.cpp
./qjoypad-4.1.0/src/getkey.h
./qjoypad-4.1.0/src/icon.cpp
./qjoypad-4.1.0/src/getkey.cpp
./qjoypad-4.1.0/src/configure
./qjoypad-4.1.0/src/keycode.h
./qjoypad-4.1.0/src/event.cpp
./qjoypad-4.1.0/src/constant.h
./qjoypad-4.1.0/src/quickset.cpp
./qjoypad-4.1.0/src/config
./qjoypad-4.1.0/src/axisw.h
./qjoypad-4.1.0/src/axis.h
./qjoypad-4.1.0/src/button.h
./qjoypad-4.1.0/src/error.h
./qjoypad-4.1.0/src/joypadw.cpp
./qjoypad-4.1.0/src/button.cpp
./qjoypad-4.1.0/src/joypad.h
./qjoypad-4.1.0/src/button_edit.cpp
./qjoypad-4.1.0/src/layout.cpp
./qjoypad-4.1.0/src/device.h
./qjoypad-4.1.0/src/layout_edit.h
./qjoypad-4.1.0/src/axis_edit.h
./qjoypad-4.1.0/src/axis.cpp
./qjoypad-4.1.0/src/buttonw.h
./qjoypad-4.1.0/src/flash.h
./qjoypad-4.1.0/src/layout.h
./qjoypad-4.1.0/src/flash.cpp
./qjoypad-4.1.0/INSTALL.txt
./qjoypad-4.1.0/icons/
./qjoypad-4.1.0/icons/gamepad3-64x64.png
./qjoypad-4.1.0/icons/gamepad2-64x64.png
./qjoypad-4.1.0/icons/gamepad1-24x24.png
./qjoypad-4.1.0/icons/gamepad4-64x64.png
./qjoypad-4.1.0/icons/gamepad1-64x64.png
./qjoypad-4.1.0/icons/gamepad3-24x24.png
./qjoypad-4.1.0/icons/gamepad4-24x24.png
./qjoypad-4.1.0/icons/gamepad2-24x24.png

```

Would you know where the icon is in the *Menu* or how else to start the program?

---

### Post by ~Plue on 2011-04-19
> **Advice Pro said:**
> What's the beneficial difference between these files and *qjoypad-4.1.0.tar.gz*?

ta.gz archives would usually require you to compile the program yourself whereas the .deb packages are ready for a one click install

---

### Post by WorMzy on 2011-04-19
> **Advice Pro said:**
> What's the beneficial difference between these files and *qjoypad-4.1.0.tar.gz*?

I had ran:
```
cd ~/Downloads/
tar -xzvf qjoypad-4.1.0.tar.gz
```

Which output:```
./qjoypad-4.1.0/
./qjoypad-4.1.0/README.txt
./qjoypad-4.1.0/LICENSE.txt
./qjoypad-4.1.0/src/
./qjoypad-4.1.0/src/event.h
./qjoypad-4.1.0/src/keycode.cpp
./qjoypad-4.1.0/src/axis_edit.cpp
./qjoypad-4.1.0/src/layout_edit.cpp
./qjoypad-4.1.0/src/buttonw.cpp
./qjoypad-4.1.0/src/joyslider.h
./qjoypad-4.1.0/src/joypadw.h
./qjoypad-4.1.0/src/button_edit.h
./qjoypad-4.1.0/src/quickset.h
./qjoypad-4.1.0/src/joypad.cpp
./qjoypad-4.1.0/src/axisw.cpp
./qjoypad-4.1.0/src/qjoypad.pro
./qjoypad-4.1.0/src/main.cpp
./qjoypad-4.1.0/src/icon.h
./qjoypad-4.1.0/src/joyslider.cpp
./qjoypad-4.1.0/src/getkey.h
./qjoypad-4.1.0/src/icon.cpp
./qjoypad-4.1.0/src/getkey.cpp
./qjoypad-4.1.0/src/configure
./qjoypad-4.1.0/src/keycode.h
./qjoypad-4.1.0/src/event.cpp
./qjoypad-4.1.0/src/constant.h
./qjoypad-4.1.0/src/quickset.cpp
./qjoypad-4.1.0/src/config
./qjoypad-4.1.0/src/axisw.h
./qjoypad-4.1.0/src/axis.h
./qjoypad-4.1.0/src/button.h
./qjoypad-4.1.0/src/error.h
./qjoypad-4.1.0/src/joypadw.cpp
./qjoypad-4.1.0/src/button.cpp
./qjoypad-4.1.0/src/joypad.h
./qjoypad-4.1.0/src/button_edit.cpp
./qjoypad-4.1.0/src/layout.cpp
./qjoypad-4.1.0/src/device.h
./qjoypad-4.1.0/src/layout_edit.h
./qjoypad-4.1.0/src/axis_edit.h
./qjoypad-4.1.0/src/axis.cpp
./qjoypad-4.1.0/src/buttonw.h
./qjoypad-4.1.0/src/flash.h
./qjoypad-4.1.0/src/layout.h
./qjoypad-4.1.0/src/flash.cpp
./qjoypad-4.1.0/INSTALL.txt
./qjoypad-4.1.0/icons/
./qjoypad-4.1.0/icons/gamepad3-64x64.png
./qjoypad-4.1.0/icons/gamepad2-64x64.png
./qjoypad-4.1.0/icons/gamepad1-24x24.png
./qjoypad-4.1.0/icons/gamepad4-64x64.png
./qjoypad-4.1.0/icons/gamepad1-64x64.png
./qjoypad-4.1.0/icons/gamepad3-24x24.png
./qjoypad-4.1.0/icons/gamepad4-24x24.png
./qjoypad-4.1.0/icons/gamepad2-24x24.png

```

Would you know where the icon is in the *Menu* or how else to start the program?

You haven't installed it yet, you've just extracted the contents of the archive. What you have there is a bunch of source files. You'll need to compile the application first. To do that you'll need to install buildessential and any development libraries this application depends on. Check README.txt and INSTALL.txt for details.

Or, use a deb to install the program, like Plue suggested.

---

### Post by hwttdz on 2011-04-19
Original poster stated they would like to install in terminal (as opposed to using a deb).

To do this first untar (i.e. tar -xf filename), maybe some more flags (you fed -v for verbose, and -z to tell it the archive was gzipped, it should be able to figure it out, but I always do the same).  

Then you should have a new directory.  The first thing I do is go into the directory and poke around, there's generally at least a README file and also frequently an INSTALL file.  Look at both of these, they should give instructions for compiling.  Which generally amounts to changing to the src directory and doing "./configure && make && sudo make install", or maybe replace "sudo make install" with "make install" if you fed something else a --prefix option.

---

### Post by Advice Pro on 2011-04-21
I'm not going to use a deb package for future references since most apps are packaged as binary files. I can't open README.txt, I get the error:

> Could not open the file /home/lapiii/Downloads/qjoypad-4.1.0/README.txt.

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.

Character Encoding:

Current Local (UFE-8)
Western (ISO-8859-15)

---

