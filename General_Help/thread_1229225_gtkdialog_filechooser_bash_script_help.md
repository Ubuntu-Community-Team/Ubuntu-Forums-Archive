---
title: "gtkdialog filechooser bash script help"
date: 2009-08-01
forum: General Help
---

### Post by myk.dinis on 2009-08-01
I wrote a quick dirty mencoder -> ffmpeg script to convert videos for my BB.

I would like to add a gtkdialog filechooser option to it so I can browse to the file I want to convert.

---------------------Script----------------------------
#!/bin/bash

# variables

VIDEO=$1

# per model scaling-------------------- 

PHONE=-10:320,rotate=1	# 82xx aka Pearl Flip
#PHONE=320:-10		# 83xx Curve

# end scaling--------------------------

# video and audio bitrates-------------

ABR=64k                 # audio bitrate
VBR=400                 # video bitrate

# end bitrates--------------------------


mencoder "$VIDEO" \
        -o "${VIDEO%.*}_draft.avi" \
	-of avi \
	-ovc lavc \
        -oac copy \
	-lavcopts vcodec=mpeg4:vbitrate=$VBR \
	-vf scale=$PHONE,harddup && \
ffmpeg -i "${VIDEO%.*}_draft.avi" \
	-vcodec copy \
	-acodec libfaac -ar 22050 -ac 2 -ab $ABR \
	"${VIDEO%.*}_82xx.mp4" && \
rm *draft.*


# Extra Comments
#--------------------------
# harddup - 
# harddup keeps the audio in sync with video by not dumping duplicate video frames.
# I used two separate encoders because I like the way ffmpeg does audio but it lacks the rotate option.
#--------------------------
# scaling - 
# From mencoder man pages--
# -2:   Calculate w/h using the other dimension and the prescaled aspect ratio.)
# -(n+8): Like -n above, but rounding the dimension to the closest multiple of 16.)
# -------------------------
# So, I used -10 because avi needs both dimensions to be multiples of 16
#
-------------------End Script-------------------------------


Would someone be able to help?

Thanks!

---

### Post by Brandon Williams on 2009-08-02
You could throw together a simple python script that will present a graphical file selecter. Using python makes it easy to do without having to install a bunch of extra libraries in order to compile a binary for the purpose. Here's an example of such a script:
```
#!/usr/bin/env python

try:
    import pygtk
    pygtk.require("2.0")
except:
    pass
try:
    import sys
    import os
    import gtk
except ImportError, e:
    print "Import error in helper:", e
    sys.exit(1)


def SelectFile(filters):
    """This function is used to select an existing file """

    dialog_buttons = (gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL,
                      gtk.STOCK_OPEN, gtk.RESPONSE_OK)
    dialog_title = "Select File"
    dialog = gtk.FileChooserDialog(title=dialog_title,
                                   action=gtk.FILE_CHOOSER_ACTION_OPEN,
                                   buttons=dialog_buttons)
    for filter in filters:
        dialog.add_filter(filter)
    allfilter = gtk.FileFilter()
    allfilter.set_name("All files")
    allfilter.add_pattern("*")
    dialog.add_filter(allfilter)

    result = ""
    if(dialog.run() == gtk.RESPONSE_OK):
        result = dialog.get_filename()
    dialog.destroy()

    return result


if __name__ == "__main__":
    filter = gtk.FileFilter()
    filter.set_name("AVI file")
    filter.add_pattern("*.avi")
    filename = SelectFile([filter])
    print filename
    sys.exit(0)
```
With a bit of effort, you could abstract it further to make it a more general purpose utility.

---

### Post by tekknokrat on 2010-10-20
> **Brandon Williams said:**
> 
...
to compile a binary for the purpose. Here's an example of such a script:
[code]#!/usr/bin/env python
...


Thx for the pygtk introduction :-)

---

