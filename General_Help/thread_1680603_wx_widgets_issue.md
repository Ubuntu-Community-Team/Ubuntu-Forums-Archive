---
title: "wx widgets issue"
date: 2011-02-02
forum: General Help
---

### Post by mr.thraz on 2011-02-02
For years I had a piece of midi equipment that didn't work in Gnu\Linux

[the Creative Prodikeys P.C.-Midi.]("http://www.prodikeys.com/products/Prodikeys_PC-MIDI/")


Now its midi function has been restored by a very  helpful guy  who created a Linux driver for it.

[Here.]("http://sourceforge.net/projects/pc-midi-linux/")

Unfortunately its needs a program to emulate many of its functions “like octave shift”.

The prog. needs wx widgets to make and it refuses to.

I keep getting:


> 
mrthraz@Sol:~$ cd /home/mrthraz/Downloads/pcmidi-linux-driver/pcmidi-controller mrthraz@Sol:~/Downloads/pcmidi-linux-driver/pcmidi-controller$ make cc -c pcmidi_controllerApp.cpp -o obj/Release/pcmidi_controllerApp.o -Wall -DLINUX -O2 `wx-config --cxxflags` pcmidi_controllerApp.cpp: In member function ‘virtual bool pcmidi_controllerApp::OnInit()’: pcmidi_controllerApp.cpp:54: error: conversion from ‘const char [49]’ to ‘wxString’ is ambiguous /usr/include/wx-2.8/wx/string.h:692: note: candidates are: wxString::wxString(wxChar, size_t) <near match> /usr/include/wx-2.8/wx/string.h:682: note: wxString::wxString(int) <near match> pcmidi_controllerApp.cpp:55: error: ambiguous overload for ‘operator+=’ in ‘msg += "Copyright Don Prince (c) 2009\012\012"’ /usr/include/wx-2.8/wx/string.h:1012: note: candidates are: void wxString::operator+=(const wxWCharBuffer&) <near match> /usr/include/wx-2.8/wx/string.h:1407: note: wxString& wxString::operator+=(const wxString&) <near match> /usr/include/wx-2.8/wx/string.h:1413: note: wxString& wxString::operator+=(wxChar) <near match> pcmidi_controllerApp.cpp:56: error: ambiguous overload for ‘operator+=’ in ‘msg += "License: GNU General Public License (version 2 or later)\012\012\012"’ /usr/include/wx-2.8/wx/string.h:1012: note: candidates are: void wxString::operator+=(const wxWCharBuffer&) <near match> /usr/include/wx-2.8/wx/string.h:1407: note: wxString& wxString::operator+=(const wxString&) <near match> /usr/include/wx-2.8/wx/string.h:1413: note: wxString& wxString::operator+=(wxChar) <near match> make: *** [obj/Release/pcmidi_controllerApp.o] Error 1 mrthraz@Sol:~/Downloads/pcmidi-linux-driver/pcmidi-controller$ 


he has told me that:

You need to install wxWidgets 2.8 development libraries and runtime libraries, and also the same for libsysfs .

I tried doing so but I still get the same output. any ideas.

---

### Post by Sazhen86 on 2011-02-02
Hi

It looks like the libraries you are using are compiled with Unicode support which is causing problems with string literals in the source code.

Try surrounding the string literals with _T() or wxT() and see if that helps.

Cheers

---

### Post by mr.thraz on 2011-02-02
whats a string literal?

---

### Post by Sazhen86 on 2011-02-02
A string literal in the code is text that is enclosed in quotes like in the following line:

msg += "Copyright Don Prince (c) 2009\012\012"

To work with a Unicode build, that would need changing to:

msg += wxT("Copyright Don Prince (c) 2009\012\012")

---

### Post by mr.thraz on 2011-02-03
i see.

I'll try it out.

---

### Post by mr.thraz on 2011-02-03
wait a min. what file am i gonna do that with the folder to make  has a ton of files.

---

### Post by mr.thraz on 2011-02-03
still getting:

> mrthraz@D:~/Desktop/pcmidi-linux-driver/pcmidi-controller$ make
cc -c pcmidi_controllerApp.cpp -o obj/Release/pcmidi_controllerApp.o -Wall -DLINUX -O2 `wx-config --cxxflags`
pcmidi_controllerApp.cpp: In member function ‘virtual bool pcmidi_controllerApp::OnInit()’:
pcmidi_controllerApp.cpp:54: error: conversion from ‘const char [49]’ to ‘wxString’ is ambiguous
/usr/include/wx-2.8/wx/string.h:692: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
pcmidi_controllerApp.cpp:55: error: ambiguous overload for ‘operator+=’ in ‘msg += "Copyright Don Prince (c) 2009\012\012"’
/usr/include/wx-2.8/wx/string.h:1012: note: candidates are: void wxString::operator+=(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:1407: note:                 wxString& wxString::operator+=(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:1413: note:                 wxString& wxString::operator+=(wxChar) <near match>
pcmidi_controllerApp.cpp:56: error: ambiguous overload for ‘operator+=’ in ‘msg += "License: GNU General Public License (version 2 or later)\012\012\012"’
/usr/include/wx-2.8/wx/string.h:1012: note: candidates are: void wxString::operator+=(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:1407: note:                 wxString& wxString::operator+=(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:1413: note:                 wxString& wxString::operator+=(wxChar) <near match>
make: *** [obj/Release/pcmidi_controllerApp.o] Error 1
mrthraz@D:~/Desktop/pcmidi-linux-driver/pcmidi-controller$ 


---

### Post by mr.thraz on 2011-02-03
and this one when i try wxT:
> 
mrthraz@D:~/Desktop/pcmidi-linux-driver/pcmidi-controller$ make
cc -c GUIDialog.cpp -o obj/Release/GUIDialog.o -Wall -DLINUX -O2 `wx-config --cxxflags`
cc -c pcmidi_controllerApp.cpp -o obj/Release/pcmidi_controllerApp.o -Wall -DLINUX -O2 `wx-config --cxxflags`
pcmidi_controllerApp.cpp: In member function ‘virtual bool pcmidi_controllerApp::OnInit()’:
pcmidi_controllerApp.cpp:54: error: conversion from ‘const char [49]’ to ‘wxString’ is ambiguous
/usr/include/wx-2.8/wx/string.h:692: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
pcmidi_controllerApp.cpp:55: error: ambiguous overload for ‘operator+=’ in ‘msg += "Copyright Don Prince (c) 2009\012\012"’
/usr/include/wx-2.8/wx/string.h:1012: note: candidates are: void wxString::operator+=(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:1407: note:                 wxString& wxString::operator+=(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:1413: note:                 wxString& wxString::operator+=(wxChar) <near match>
pcmidi_controllerApp.cpp:56: error: ambiguous overload for ‘operator+=’ in ‘msg += "License: GNU General Public License (version 2 or later)\012\012\012"’
/usr/include/wx-2.8/wx/string.h:1012: note: candidates are: void wxString::operator+=(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:1407: note:                 wxString& wxString::operator+=(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:1413: note:                 wxString& wxString::operator+=(wxChar) <near match>
make: *** [obj/Release/pcmidi_controllerApp.o] Error 1


---

### Post by Sazhen86 on 2011-02-03
Hi

Try changing 

msg += "Copyright Don Prince (c) 2009\012\012" 

in file pcmidi_controllerApp.cpp at line 55 to

msg += wxT("Copyright Don Prince (c) 2009\012\012")

and 

msg += "License: GNU General Public License (version 2 or later)\012\012\012"

in the same file at line 56 to

msg += wxT("License: GNU General Public License (version 2 or later)\012\012\012")

Save the file and try running make again to see if those errors go away.  There may of course be many such string literals in many files that need changing.  If that's the case, it might be easier to build a non-unicode version of wx.

---

### Post by mr.thraz on 2011-02-04
ok looks alittle different now, still an error.

but I'll fix this one as well.

> mrthraz@D:~/Desktop/pcmidi-linux-driver/pcmidi-controller$ make
cc -c GUIDialog.cpp -o obj/Release/GUIDialog.o -Wall -DLINUX -O2 `wx-config --cxxflags`
cc -c pcmidi_controllerApp.cpp -o obj/Release/pcmidi_controllerApp.o -Wall -DLINUX -O2 `wx-config --cxxflags`
pcmidi_controllerApp.cpp: In member function &#8216;virtual bool pcmidi_controllerApp::OnInit()&#8217;:
pcmidi_controllerApp.cpp:54: error: conversion from &#8216;const char [49]&#8217; to &#8216;wxString&#8217; is ambiguous
/usr/include/wx-2.8/wx/string.h:692: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
make: *** [obj/Release/pcmidi_controllerApp.o] Error 1
mrthraz@D:~/Desktop/pcmidi-linux-driver/pcmidi-controller$ 

---

### Post by mr.thraz on 2011-02-04
OK, new gobbledygook.


> 
mrthraz@D:~/Desktop/pcmidi-linux-driver/pcmidi-controller$ make
cc -c pcmidi_controllerMain.cpp -o obj/Release/pcmidi_controllerMain.o -Wall -DLINUX -O2 `wx-config --cxxflags`
cc -c pcmidi-sysfs.cpp -o obj/Release/pcmidi-sysfs.o -Wall -DLINUX -O2 `wx-config --cxxflags`
pcmidi-sysfs.cpp:34:28: error: sysfs/libsysfs.h: No such file or directory
pcmidi-sysfs.cpp:39: error: &#8216;SYSFS_PATH_MAX&#8217; was not declared in this scope
pcmidi-sysfs.cpp: In function &#8216;int pcmidi_init_sysfs()&#8217;:
pcmidi-sysfs.cpp:45: error: &#8216;SYSFS_PATH_MAX&#8217; was not declared in this scope
pcmidi-sysfs.cpp:50: error: &#8216;sysfs_mount&#8217; was not declared in this scope
pcmidi-sysfs.cpp:50: error: &#8216;sysfs_get_mnt_path&#8217; was not declared in this scope
pcmidi-sysfs.cpp: In function &#8216;int pcmidi_read_one_sysfs_device(sysfs_device*)&#8217;:
pcmidi-sysfs.cpp:63: error: invalid use of incomplete type &#8216;struct sysfs_device&#8217;
pcmidi-sysfs.cpp:59: error: forward declaration of &#8216;struct sysfs_device&#8217;
pcmidi-sysfs.cpp:65: error: &#8216;sysfs_get_device_attr&#8217; was not declared in this scope
pcmidi-sysfs.cpp:67: error: &#8216;sysfs_get_device_attr&#8217; was not declared in this scope
pcmidi-sysfs.cpp:69: error: &#8216;sysfs_get_device_attr&#8217; was not declared in this scope
pcmidi-sysfs.cpp:72: error: invalid use of incomplete type &#8216;struct sysfs_device&#8217;
pcmidi-sysfs.cpp:59: error: forward declaration of &#8216;struct sysfs_device&#8217;
pcmidi-sysfs.cpp:72: error: &#8216;SYSFS_PATH_MAX&#8217; was not declared in this scope
pcmidi-sysfs.cpp: In function &#8216;int pcmidi_read_sysfs_hid_bus()&#8217;:
pcmidi-sysfs.cpp:85: error: &#8216;sysfs_open_bus&#8217; was not declared in this scope
pcmidi-sysfs.cpp:91: error: &#8216;sysfs_get_bus_devices&#8217; was not declared in this scope
pcmidi-sysfs.cpp:97: error: expected primary-expression before &#8216;struct&#8217;
pcmidi-sysfs.cpp:97: error: &#8216;dlist_for_each_data&#8217; was not declared in this scope
pcmidi-sysfs.cpp:98: error: expected &#8216;;&#8217; before &#8216;if&#8217;
pcmidi-sysfs.cpp:103: error: &#8216;sysfs_close_bus&#8217; was not declared in this scope
pcmidi-sysfs.cpp: In function &#8216;int pcmidi_read_channel()&#8217;:
pcmidi-sysfs.cpp:112: error: &#8216;SYSFS_PATH_MAX&#8217; was not declared in this scope
pcmidi-sysfs.cpp:115: error: &#8216;buf&#8217; was not declared in this scope
pcmidi-sysfs.cpp:118: error: &#8216;sysfs_open_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp:121: error: &#8216;sysfs_read_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp:123: error: invalid use of incomplete type &#8216;struct sysfs_attribute&#8217;
pcmidi-sysfs.cpp:111: error: forward declaration of &#8216;struct sysfs_attribute&#8217;
pcmidi-sysfs.cpp:125: error: &#8216;sysfs_close_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp: In function &#8216;void pcmidi_write_channel(int)&#8217;:
pcmidi-sysfs.cpp:133: error: &#8216;SYSFS_PATH_MAX&#8217; was not declared in this scope
pcmidi-sysfs.cpp:135: error: &#8216;buf&#8217; was not declared in this scope
pcmidi-sysfs.cpp:138: error: &#8216;sysfs_open_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp:143: error: &#8216;sysfs_write_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp:145: error: &#8216;sysfs_close_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp: In function &#8216;int pcmidi_read_octave()&#8217;:
pcmidi-sysfs.cpp:151: error: &#8216;SYSFS_PATH_MAX&#8217; was not declared in this scope
pcmidi-sysfs.cpp:154: error: &#8216;buf&#8217; was not declared in this scope
pcmidi-sysfs.cpp:157: error: &#8216;sysfs_open_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp:160: error: &#8216;sysfs_read_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp:162: error: invalid use of incomplete type &#8216;struct sysfs_attribute&#8217;
pcmidi-sysfs.cpp:150: error: forward declaration of &#8216;struct sysfs_attribute&#8217;
pcmidi-sysfs.cpp:164: error: &#8216;sysfs_close_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp: In function &#8216;void pcmidi_write_octave(int)&#8217;:
pcmidi-sysfs.cpp:172: error: &#8216;SYSFS_PATH_MAX&#8217; was not declared in this scope
pcmidi-sysfs.cpp:174: error: &#8216;buf&#8217; was not declared in this scope
pcmidi-sysfs.cpp:177: error: &#8216;sysfs_open_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp:182: error: &#8216;sysfs_write_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp:184: error: &#8216;sysfs_close_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp: In function &#8216;int pcmidi_read_sustain()&#8217;:
pcmidi-sysfs.cpp:190: error: &#8216;SYSFS_PATH_MAX&#8217; was not declared in this scope
pcmidi-sysfs.cpp:193: error: &#8216;buf&#8217; was not declared in this scope
pcmidi-sysfs.cpp:196: error: &#8216;sysfs_open_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp:199: error: &#8216;sysfs_read_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp:201: error: invalid use of incomplete type &#8216;struct sysfs_attribute&#8217;
pcmidi-sysfs.cpp:189: error: forward declaration of &#8216;struct sysfs_attribute&#8217;
pcmidi-sysfs.cpp:203: error: &#8216;sysfs_close_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp: In function &#8216;void pcmidi_write_sustain(int)&#8217;:
pcmidi-sysfs.cpp:211: error: &#8216;SYSFS_PATH_MAX&#8217; was not declared in this scope
pcmidi-sysfs.cpp:213: error: &#8216;buf&#8217; was not declared in this scope
pcmidi-sysfs.cpp:216: error: &#8216;sysfs_open_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp:221: error: &#8216;sysfs_write_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp:223: error: &#8216;sysfs_close_attribute&#8217; was not declared in this scope
pcmidi-sysfs.cpp: At global scope:
pcmidi-sysfs.cpp:59: warning: &#8216;int pcmidi_read_one_sysfs_device(sysfs_device*)&#8217; defined but not used
make: *** [obj/Release/pcmidi-sysfs.o] Error 1


it seems to be saying im missing "sysfs/libsysfs.h"

am i correct in thinking this?

---

### Post by mr.thraz on 2011-02-04
OK, i installed libsysfs and got this:

> mrthraz@D:~/Desktop/pcmidi-linux-driver/pcmidi-controller$ make
cc -c pcmidi-sysfs.cpp -o obj/Release/pcmidi-sysfs.o -Wall -DLINUX -O2 `wx-config --cxxflags`
cc -o bin/Release/pcmidi-controller obj/Release/GUIDialog.o obj/Release/pcmidi_controllerApp.o obj/Release/pcmidi_controllerMain.o obj/Release/pcmidi-sysfs.o -s `wx-config --libs` -lsysfs


but when i try to make install i get this:

> mrthraz@D:~/Desktop/pcmidi-linux-driver/pcmidi-controller$ make install
cc -o bin/Release/pcmidi-controller obj/Release/GUIDialog.o obj/Release/pcmidi_controllerApp.o obj/Release/pcmidi_controllerMain.o obj/Release/pcmidi-sysfs.o -s `wx-config --libs` -lsysfs
/usr/local/bin/install -c bin/Release/pcmidi-controller /usrlocal/bin
/bin/bash: /usr/local/bin/install: No such file or directory
make: *** [install] Error 127

---

### Post by mr.thraz on 2011-02-04
ok, it see now that it made the app it just didn't install it in its proper place.

but it doesn't need to. 

i can put it my home folder if need be and launch it from there with a custom icon.

thank you so much for helping me. i was so lost with out you.

can i submit this to him as a fix?

---

### Post by Sazhen86 on 2011-02-04
Hi

It's good to hear that you got it sorted out and I'm happy to have helped.

If you really want it installed in /usr/local you could either edit the makefile to use /usr/bin/install instead of /usr/local/bin/install.  Or, you could try make -n install which will show what make would have done and then do it manually.  If you need help, post the output from 'make -n install' and we'll see what it was trying to do.

Feel free to submit it to him as a fix.  The wxT() macro will work in both unicode and non-unicode builds so it would be a worthwhile addition to the code.

Cheers

---

### Post by fpohlmann2 on 2011-03-13
[QUOTE=Sazhen86;10423572]Hi

Try changing 

msg += "Copyright Don Prince (c) 2009\012\012" 

in file pcmidi_controllerApp.cpp at line 55 to

msg += wxT("Copyright Don Prince (c) 2009\012\012")

and 

msg += "License: GNU General Public License (version 2 or later)\012\012\012"

in the same file at line 56 to

msg += wxT("License: GNU General Public License (version 2 or later)\012\012\012")

Mine looks like this.

 wxString msg = "\nProdikeys PC-MIDI Keyboard helper application\n\n";
    msg += "Copyright Don Prince (c) 2009\n\n";
    msg += "License: GNU General Public License (version 2 or later)\n\n\n";
    msg += wxbuildinfo(long_f);
    wxMessageBox(msg, _("Device not found...Aborting"),wxICON_ERROR | wxCENTRE);

Instead of dates I have \n\n

I've tried to change from \n\n to the suggested line above with ; and without it and I'm still getting errors.
Take a look.

fpohlmann@ubuntu:~/Desktop/pcmidi-controller$ make
cc -c pcmidi_controllerApp.cpp -o obj/Release/pcmidi_controllerApp.o -Wall -DLINUX -O2 `wx-config --cxxflags`
pcmidi_controllerApp.cpp: In member function ‘virtual bool pcmidi_controllerApp::OnInit()’:
pcmidi_controllerApp.cpp:54: error: conversion from ‘const char [49]’ to ‘wxString’ is ambiguous
/usr/include/wx-2.8/wx/string.h:692: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
pcmidi_controllerApp.cpp:55: error: ambiguous overload for ‘operator+=’ in ‘msg += "Copyright Don Prince (c) 2009\012\012"’
/usr/include/wx-2.8/wx/string.h:1012: note: candidates are: void wxString::operator+=(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:1407: note:                 wxString& wxString::operator+=(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:1413: note:                 wxString& wxString::operator+=(wxChar) <near match>
pcmidi_controllerApp.cpp:56: error: ambiguous overload for ‘operator+=’ in ‘msg += "License: GNU General Public License (version 2 or later)\012\012\012"’
/usr/include/wx-2.8/wx/string.h:1012: note: candidates are: void wxString::operator+=(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:1407: note:                 wxString& wxString::operator+=(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:1413: note:                 wxString& wxString::operator+=(wxChar) <near match>
make: *** [obj/Release/pcmidi_controllerApp.o] Error 1

What I'm doing wrong?

Thank's

---

