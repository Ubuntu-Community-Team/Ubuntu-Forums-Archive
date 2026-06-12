---
title: "Xsane crash"
date: 2011-04-15
forum: General Help
---

### Post by MarkBM on 2011-04-15
Hello forum members, My problem is that Xsane crashes immediately after it opens. It has only done this after installing the proprietary graphics driver via the hardware drivers options under system/administration, ie not from ATI/AMD website. I would like to keep this driver after the recent changes that inhibit compiz for certain ATI hardware (Radeon HD3650 AGP) It allows me to use Google Earth and other apps requiring acceleration. Xsane worked fine with the shipped open source driver.
I have tried opening Xsane from a terminal with the following resultmark@mark-desktop:~$ xsane
Xlib:  extension "RANDR" missing on display ":0.0".

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
The program 'xsane' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 20465 error_code 8 request_code 153 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
mark@mark-desktop:~$ 


I don't want compiz activated as it severely affects video using the proprietary driver. I am also running a second monitor (analog) in xinerama.
Any help greatly appreciated. Ubuntu 10.04 Lucid Lynx

---

### Post by col48 on 2011-04-15
This is a comment, not a solution.

I also see the Warning message (but with xsane:1866 not 3709) when I start xsane from a Terminal.  I counted just now and there were 29 copies of it.

But xsane works normally, so I have ignored it.

I don't get the other messages.

---

### Post by MarkBM on 2011-04-17
Thanks for your comment Col48. Also forgot to mention Simple Scan opens okay.

---

### Post by MarkBM on 2011-05-06
> **MarkBM said:**
> Hello forum members, My problem is that Xsane crashes immediately after it opens. It has only done this after installing the proprietary graphics driver via the hardware drivers options under system/administration, ie not from ATI/AMD website. I would like to keep this driver after the recent changes that inhibit compiz for certain ATI hardware (Radeon HD3650 AGP) It allows me to use Google Earth and other apps requiring acceleration. Xsane worked fine with the shipped open source driver.
I have tried opening Xsane from a terminal with the following resultmark@mark-desktop:~$ xsane
Xlib:  extension "RANDR" missing on display ":0.0".

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3709): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
The program 'xsane' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 20465 error_code 8 request_code 153 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
mark@mark-desktop:~$ 


I don't want compiz activated as it severely affects video using the proprietary driver. I am also running a second monitor (analog) in xinerama.
Any help greatly appreciated. Ubuntu 10.04 Lucid Lynx


Problem solved by disabling xinerama. This is a known bug listed in Launchpad Bug #425506

---

