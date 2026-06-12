---
title: "Terminal file browser that allows multiple selections"
date: 2009-11-22
forum: General Help
---

### Post by Intrepid Ibex on 2009-11-22
Hi,

I'd like to know if there's any terminal file browsers that allow multiple selections (I mean hold Ctrl and click files and/or folders or hold shift and click/press up and down), as mc (midnight commander) won't allow this (at least I haven't found a way with it to do that).

For those not understanding what an earth am I asking about, here's a clarification of selecting multiple files/folders: [http://www.codeproject.com/KB/files/BrowseForFiles/BroswForFiles_1.JPG](http://www.codeproject.com/KB/files/BrowseForFiles/BroswForFiles_1.JPG)

---

### Post by prshah on 2009-11-22
> **Intrepid Ibex said:**
> 
I'd like to know if there's any terminal file browsers that allow multiple selections , as mc (midnight commander) won't allow this (at least I haven't found a way with it to do that).

MC will not work with Ctrl-Click, but you can use Alt_+ to select multiple files, and Alt_- to deselect.

When you press Alt+ you will get an option to enter a filename and/or wildcards. Each time you use Alt+ you can enter more filenames and/or wildcards, the previously selected (tagged) files will not be deselected.

You can also use Alt+ to select all files, then Alt- to deselect the specific files that you want.

Yes, it is inconvenient, but it is a terminal browser after all. Very useful on servers (which are usually without a GUI).

I don't know about any other alternatives, so they might exist; just pointing out that MC has a facility to select (tag) multiple files, though it may not be very convenient.

---

### Post by Intrepid Ibex on 2009-11-27
Ok, well thanks for the info(rmation).

---

