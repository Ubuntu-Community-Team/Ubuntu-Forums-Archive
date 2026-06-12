---
title: "vibrance,sharpening. nvidia crash."
date: 2011-01-21
forum: General Help
---

### Post by soryu on 2011-01-21
when i adjust the digital vibrance or image sharpening nvidia crashes.everything else works.
i get this error when running it from a term.

mint01@mint01-desktop ~ $ nvidia-settings
The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 220 error_code 2 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
mint01@mint01-desktop ~ $ 

tried a reinstall of drivers same thing.
thanks.:KS

---

### Post by no2498 on 2011-01-21
will this help you i hope it does


&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.

---

### Post by soryu on 2011-01-22
processing......

---

### Post by soryu on 2011-01-22
mint01@mint01-desktop ~ $ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
?????????


i switched it to  x.
samething.
back to auto detect.

---

### Post by no2498 on 2011-01-22
we all get these

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'


it should not change on its own
did you set it back to auto

---

### Post by efflandt on 2011-01-22
Which nvidia card and nvidia drivers?  And is it Ubuntu nvidia-current package or something you manually installed from nvidia?  Or maybe you have wrong nvida-settings package for your nvidia drivers.  We cannot even tell which mint version you are running.

I am currently using nvidia-current 260.19.29 in Natty (or same version from x-swat ppa in Maverick, which is also available for Lucid).

---

### Post by soryu on 2011-01-22
yea, i set it back it auto detect .


here goes some info:
driver version 173.14.22
mint 9
nvidia geforce fx 5700le
how do i check if  i have the correct nvidia  package?

---

### Post by soryu on 2011-01-22
i've had this card for a while works ok on mint 8 i was unable to use the
x server color correction and digital vibrance and image sharpeniing did work.

now on mint 9 i can use the color correction. not digital vibrance and image sharpening.

---

