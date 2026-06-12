---
title: "BadWindow errors following updates"
date: 2011-01-22
forum: General Help
---

### Post by mediax on 2011-01-22
Until some point in the last week, I have been quite happily running Neverwinter Nights and GNU Backgammon. However, both now refuse to run.  

I haven't been tinkering with my system and I haven't installed any new software apart from routine updates - which makes me suspect my problems are related to the updates (hence my posting here, rather than in the Games Forum).

Neverwinter Nights gives me the following messages when run from a terminal:

```

  X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  137 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x440000f
  Serial number of failed request:  32
  Current serial number in output stream:  32

```

and running gnubg in a terminal gives:

```

GNU Backgammon 0.9.0

Copyright, 1999-2004 by Gary Wong, 2004-2008 GNU Backgammon is the legal
property of its authors.

GNU Backgammon is free software, covered by the GNU General Public License
version 3 or later, and you are welcome to change it and/or distribute
copies of it under certain conditions.  Type "show copying" to see the
conditions. There is absolutely no warranty for GNU Backgammon. Type 
"show warranty" for details.

Python supported.
SQLite database supported.
Window system supported.
External players supported.
XML match equity files supported.
Long RNG seeds supported.
3d Boards supported.
External commands supported.
ESD sound system supported.

(gnubg:3616): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gnubg:3616): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gnubg:3616): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

***WARNING***

Note that gnubg does not use the gnubg.bd file.
You should obtain the file gnubg_ts0.bd or generate
it yourself using the program 'makebearoff'.
You can generate the file with the command:
makebearoff -t 6x6 -f gnubg_ts0.bd
You can also generate other bearoff databases; see
README for more details

set gui showids on
(No game) (No game) The program 'gnubg' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 665 error_code 3 request_code 137 minor_code 4)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I'm guessing this is something to do with the X Window settings, but I'd appreciate any help.

I'm running Ubuntu 10.04, AMD 64 bit Desktop with an NVidia 8500GT graphics card, using version 260.19.29 of the NVidia proprietory drivers.

TIA,

Ian

---

### Post by godbhaal on 2011-01-23
Try to reinstall lastest video drivers. It works for me. 

(I installed lastest wine thinking this is a wine problem and nothing)

---

### Post by mediax on 2011-01-23
Thanks for the suggestion - I'll give it a go.

Getting the NVidia drivers working originally was a bit of a nightmare, so I can't say I'm looking forward to it!

---

### Post by mediax on 2011-01-23
Thanks godbhaal - reinstalling the drivers seems to have fixed things.

And the reinstallation went a lot smoother than the original one, as well!

Thanks again!

---

