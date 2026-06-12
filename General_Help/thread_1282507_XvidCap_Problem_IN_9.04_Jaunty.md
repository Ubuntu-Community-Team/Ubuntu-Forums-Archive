---
title: "XvidCap Problem IN 9.04 Jaunty"
date: 2009-10-04
forum: General Help
---

### Post by BAMF1501 on 2009-10-04
OK so i installed xvidcap but when i go to record in jaunty i press the record button and it just closes out of xvidcap :(

---

### Post by BAMF1501 on 2009-10-04
BUmp??? PLease help

---

### Post by StuartN on 2009-10-04
> **BAMF1501 said:**
> BUmp??? PLease help

Start it from a terminal, and add the verbose option, to capture any warning or error messages it is emitting i.e. "vxidcap --verbose".

"Xvidcap --help" will give you more options.

---

### Post by BAMF1501 on 2009-10-04
How do i start via terminial ??

---

### Post by BAMF1501 on 2009-10-04
i was able to get to record but it looks crazy wierd :9 

[http://www.youtube.com/watch?v=O0NX-ZvT5zM](http://www.youtube.com/watch?v=O0NX-ZvT5zM)

---

### Post by StuartN on 2009-10-04
Try opening a terminal and type **xvidcap --sf** to see if single-frame capture mode works.

---

### Post by BAMF1501 on 2009-10-04
yes and looks clear to this is what it say in terminial

> epic1501@ubuntu:~$ xvidcap --sf 

(xvidcap:32225): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(xvidcap:32225): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xvidcap:32225): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xvidcap:32225): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xvidcap:32225): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(xvidcap:32225): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xvidcap:32225): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(xvidcap:32225): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed



---

### Post by StuartN on 2009-10-04
Well those errors are beyond me, but two things you could try are 1) Open the preferences in xvidcap (right-click on the GUI) and disable audio capture; 2) Disable Compiz.

---

### Post by BAMF1501 on 2009-10-04
i dont see gui ?? anywhere what u talkin bout

---

### Post by StuartN on 2009-10-04
> **BAMF1501 said:**
> i dont see gui ?? anywhere what u talkin bout

If I start xvidcap from the menu or from the commandline I get its graphical user interface (GUI). Right-clicking on the frame-number panel opens the menu, where you can change preferences.

Single-frame mode (xvidcap --sf) saves individual frames with no audio, while audio can be disabled in the multiframe preferences.

---

### Post by BAMF1501 on 2009-10-04
I opened preferences an di dont se no ******* gui sorry for lanquage its jsut agervatting caus ei been trying for 2 days now trying to get this to work

---

### Post by StuartN on 2009-10-04
> **BAMF1501 said:**
> I opened preferences an di dont se no ******* gui sorry for lanquage its jsut agervatting caus ei been trying for 2 days now trying to get this to work

Sorry, my language is confusing - the thing you see the preferences is what I am calling a GUI, you have it. Try disabling audio in the third (Multi-frame) tab by unchecking the tick box.

---

### Post by ApEkV2 on 2009-10-04
As i've been trying to get it to work for the past year?
So you admit you opened the preferences and can't find the gui? plz I think it found you.
Have you tried finding any other threads on this (they do exist).

---

### Post by BAMF1501 on 2009-10-04
> **StuartN said:**
> Sorry, my language is confusing - the thing you see the preferences is what I am calling a GUI, you have it. Try disabling audio in the third (Multi-frame) tab by unchecking the tick box.

i do not see any audio check box in the multi frame tab

---

### Post by StuartN on 2009-10-04
> **BAMF1501 said:**
> i do not see any audio check box in the multi frame tab

Mine looks like this, with "Enable audio" unticked. Version 1.1.6 from the repositories.

---

### Post by BAMF1501 on 2009-10-04
This is how mine looks see told you no tick for chek box 

[IMG]http://i37.tinypic.com/2cr1qb8.png[/IMG]

---

### Post by StuartN on 2009-10-04
You could try starting it with **xvidcap --audio no**

Which version do you have? "About" or Synaptic or xvidcap --help will tell you.

---

### Post by BAMF1501 on 2009-10-04
i have like 1.1.7 or 1.1.17

---

### Post by BAMF1501 on 2009-10-04
Audio support not present in this binary.
Usage: xvidcap, ver 1.1.7, (c) rasca, berlin 1997,98,99, khb (c) 2003 - 07
[--fps #.#]      frames per second (float) or a fraction string like "30000/1001"
[--verbose #]    verbose level, '-v' is --verbose 1
[--time #.#]     time to record in seconds (float)
[--frames #]     frames to record, don't use it with --time
[--continue [yes|no]] autocontinue after maximum frames/time
[--cap_geometry #x#[+#+#]] size of the capture window (WIDTHxHEIGHT+X+Y)
[--window <hex-window-id>] a hexadecimal window id (ref. xwininfo)
[--rescale #]    relative output size in percent compared to input (1-100)
[--quality #]    recording quality (1-100)
[--start_no #]   start number for the file names
[--source <src>] select input source: x11, shm
[--file <file>]  file pattern, e.g. out%03d.xwd
[--gui [yes|no]] turn on/off gui
[--sf|--mf]      request single-frame or multi-frame capture mode
[--auto]         cause auto-detection of output format, video-, and audio codec
[--codec <codec>] specify codec to use for multi-frame capture
[--codec-help]   list available codecs for multi-frame capture
[--format <format>] specify file format to override the extension in the filename
[--format-help]  list available file formats
Supported output formats:
 X11 Window Dump                         (.xwd)
 Portable Graymap File                   (.pgm)
 Portable Anymap File                    (.ppm)
 Portable Network Graphics File          (.png)
 Joint Picture Expert Group              (.jpg, .jpeg)
 Microsoft Audio Video Interleaved File  (.avi)
 General AVI file (DIVX default)         (.mpeg, .mpg)
 Microsoft Advanced Streaming Format     (.asf)
 Macromedia Flash Video Stream           (.flv, .flv1)
 Macromedia Shockwave Flash File         (.swf)
 DV Video Format                         (.dv)
 MPEG1 System Format (VCD)               (.m1v, .vcd)
 MPEG2 PS Format (SVCD)                  (.m2v, .svcd)
 MPEG2 PS Format (DVD VOB)               (.vob, .dvd)
 Quicktime Format                        (.mov, .qt)

---

### Post by StuartN on 2009-10-04
I have version 1.1.6 working fine without any setup, other than disabling audio. Version 1.1.7 is the latest and I think it is the version in Jaunty.

You could try uninstalling 1.1.7 and installing 1.1.6 from [http://sourceforge.net/projects/xvidcap/files/](http://sourceforge.net/projects/xvidcap/files/) or you could try Wink or recordMyDesktop.

To be honest, if single-frame mode is not working then xvidcap has no obvious settings to modify.

---

