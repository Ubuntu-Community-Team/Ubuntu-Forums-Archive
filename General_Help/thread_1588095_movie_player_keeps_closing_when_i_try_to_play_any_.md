---
title: "movie player keeps closing when i try to play any file"
date: 2010-10-04
forum: General Help
---

### Post by fuzzylogic25 on 2010-10-04
I dont know why this happened. I restarted my computer and now I cant play any movies. I can open up Movie Player but when I try to drag a file into it or open a file, it closes. Anyone know whats up?

---

### Post by andrewthomas on 2010-10-04
Open totem from the terminal and post any error messages

```
totem
```

---

### Post by fuzzylogic25 on 2010-10-04
This is what it says:
==========================================================
john@cmp:/media/DATA-2TB/ totem test.avi 
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 58 error_code 11 request_code 133 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
============================================================

---

### Post by andrewthomas on 2010-10-04
try ```
sudo aptitude purge totem
```followed by 

```
sudo aptitude update && sudo aptitude install totem
```

then try again.

---

### Post by fuzzylogic25 on 2010-10-04
yep it works now. thanks for that. do you know what caused it though? or what could have caused it?

---

### Post by mailhauler on 2011-03-25
Didn't for me, I afraid.

  Dell Dimension 2400
  video - Intel 82845G/GL/GE/PE/GV
  ubuntu 10.10 (new install - dual boot)
              booted to root shell and ran;
                   Xorg -configure
                   cp /root/xorg.conf.new /etc/X11/xorg.conf (advice from this board)

Totem run from terminal yields this error;

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 127 error_code 11 request_code 134 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Totem WILL play audio files (without visualisation, with visualisation totem crashes). Have tried VLC and gnome-mplayer, none has successfully played any video.

      Thank you in advance for any help.

---

