---
title: "gthumb import gtk error"
date: 2009-12-24
forum: General Help
---

### Post by MundoMuerto on 2009-12-24
I'm currently using gThumb to import pictures from a finepix e550 digital camera via usb. Recently, and since my upgrade to Karmic, I've been unable to import my pictures with the gThumb photo import tool. When I connect my camera it is detected as a generic mass storage device and the gThumb import tool is launched automatically. I can browse the photos stored on the camera but when I click the import button an empty gray progress bar appears at the bottom of the dialog box and nothing happens.

When I run gThumb from a terminal I get an error message after clicking the import button which seems to point towards some sort of gtk conflict:

```
(gthumb:4964): Gtk-CRITICAL **: gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed

```

Doesn't immediately mean anything to me but I'm guessing it has something to do with rendering the progress bar.

Running as root makes no difference and I can manually pull images from the camera through nautilus. If this is a bug, I couldn't find any obvious duplicates on the gnome.org bugzilla list. Any ideas on how I should proceed from here would be appreciated, even tips on how (and when) to report an issue like this to the project page.

Thanks in advance.

---

### Post by lidex on 2009-12-24
Try running it (gthumb) with this command in an Alt+F2 run box:
```
gthumb --import-photos
```

---

### Post by MundoMuerto on 2009-12-25
Doesn't seem to behave any differently than when I run it normally. If I opt to 'run in terminal' I still get the gtk error message I posted above.

As far as I know the run application dialog is basically shorthand for running things from a terminal. Thanks for the response though.

---

### Post by MundoMuerto on 2009-12-25
I believe I've isolated the issue somewhat. I had two video files (.avi) on the camera of approximately 75 MBs each. After manually moving the videos to the desktop gThumb properly imported and deleted the remaining pictures.

It looks like the import tool is choking on the video files somehow. I still find this strange since I'm sure I was able to import video files with gThumb previously. Then again, I haven't tried to import both videos and pictures simultaneously before. I'm glad to see that I can import images again but I'm still open to any ideas on what's going on here.

---

### Post by davidecapod on 2009-12-25
I am having the same problem, having an AVI file on my SD card causes thumb not to import my photos.

I built gthumb from source to check where is the problem, and it seems that gp_camera_file_get() call fails when trying to open the AVI.

As I reported some time ago ([https://bugs.launchpad.net/gthumb/+bug/202318](https://bugs.launchpad.net/gthumb/+bug/202318)), when gthumb fails to import just ONE file causes to fail the whole process!
BUT, if you jump over in dlg-photo-importer.c, line 1053 (where it sets the global error flag) and you go on with the import, the AVI file gets imported successfully!!
So it seems that only the thumbnailing operation is failing!!

---

### Post by troywhite on 2010-01-02
I am experiencing exactly the same issue as the OP.
Same symptoms and same error on the command line.

Has anyone managed to fix this?

---

### Post by draco31.fr on 2010-01-09
I've got the same issue. Don't try without video.
I never got this problem on Jaunty or Intrepid.

---

### Post by draco31.fr on 2010-03-01
Does anyone got more info for this bug ?
How can we bypass this bug and still import photo and video ?
(I could import video with f-spot)

---

