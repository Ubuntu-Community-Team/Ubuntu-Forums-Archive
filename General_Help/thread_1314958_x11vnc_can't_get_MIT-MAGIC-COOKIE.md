---
title: "x11vnc can't get MIT-MAGIC-COOKIE"
date: 2009-11-04
forum: General Help
---

### Post by (-NINJ4-) on 2009-11-04
I'm attempting to start x11vnc server on my 9.10 desktop, but it won't work.  I started with just "sudo apt-get install x11vnc" and then when I use this command:
```
/usr/bin/x11vnc -rfbauth ~/.vnc/x11vnc.pass -o ~/.vnc/x11vnc.log -display :0

```All I get is the following:
```
04/11/2009 21:43:12 passing arg to libvncserver: -rfbauth
04/11/2009 21:43:12 passing arg to libvncserver: /home/mflame/.vnc/x11vnc.pass
04/11/2009 21:43:12 x11vnc version: 0.9.3 lastmod: 2007-09-30
No protocol specified

04/11/2009 21:43:12 ***************************************
04/11/2009 21:43:12 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

Some tips and guidelines:

 * An X server (the one you wish to view) must be running before x11vnc is
   started: x11vnc does not start the X server.  (however, see the
   recent -create option if that is what you really want).

 * You must use -display <disp>, -OR- set and export your $DISPLAY
   environment variable to refer to the display of the desired X server.
 - Usually the display is simply ":0" (in fact x11vnc uses this if you forget
   to specify it), but in some multi-user situations it could be ":1", ":2",
   or even ":137".  Ask your administrator or a guru if you are having
   difficulty determining what your X DISPLAY is.

 * Next, you need to have sufficient permissions (Xauthority) 
   to connect to the X DISPLAY.   Here are some Tips:

 - Often, you just need to run x11vnc as the user logged into the X session.
   So make sure to be that user when you type x11vnc.
 - Being root is usually not enough because the incorrect MIT-MAGIC-COOKIE
   file will be accessed.  The cookie file contains the secret key that
   allows x11vnc to connect to the desired X DISPLAY.
 - You can explicity indicate which MIT-MAGIC-COOKIE file should be used
   by the -auth option, e.g.:
       x11vnc -auth /home/someuser/.Xauthority -display :0
       x11vnc -auth /tmp/.gdmzndVlR -display :0
   you must have read permission for the auth file.

 - If NO ONE is logged into an X session yet, but there is a greeter login
   program like "gdm", "kdm", "xdm", or "dtlogin" running, you will need
   to find and use the raw display manager MIT-MAGIC-COOKIE file.
   Some examples for various display managers:

     gdm:     -auth /var/gdm/:0.Xauth
     kdm:     -auth /var/lib/kdm/A:0-crWk72
     xdm:     -auth /var/lib/xdm/authdir/authfiles/A:0-XQvaJk
     dtlogin: -auth /var/dt/A:0-UgaaXa

   Only root will have read permission for the file, and so x11vnc must be run
   as root.  The random characters in the filenames will of course change,
   and the directory the cookie file resides in may also be system dependent.
   Sometimes the command "ps wwwaux | grep auth" can reveal the file location.

See also: [http://www.karlrunge.com/x11vnc/#faq](http://www.karlrunge.com/x11vnc/#faq)
```Even though my .Xauthority does exist, has the proper permissions, is correct, and an X session is running.

When I replace "-display :0" with "-find" I get the following output:
```
04/11/2009 19:25:58 passing arg to libvncserver: -rfbauth
04/11/2009 19:25:58 passing arg to libvncserver: /home/mflame/.vnc/x11vnc.pass
04/11/2009 19:25:58 x11vnc version: 0.9.3 lastmod: 2007-09-30
04/11/2009 19:25:58 wait_for_client: WAIT:cmd=FINDDISPLAY
04/11/2009 19:25:58 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
04/11/2009 19:25:58 
04/11/2009 19:25:58 Autoprobing TCP port 
04/11/2009 19:25:58 Autoprobing selected port 5900

The VNC desktop is:      NINJ4:0
04/11/2009 19:26:02 Got connection from client 127.0.0.1
04/11/2009 19:26:02   other clients:
04/11/2009 19:26:02 wait_for_client: got client
04/11/2009 19:26:02 wait_for_client: running: env X11VNC_SKIP_DISPLAY='' /bin/sh /tmp/x11vnc-find_display.z2aTpT
04/11/2009 19:26:02 wait_for_client: find display cmd failed
04/11/2009 19:26:02 wait_for_client: bad reply '
```I used the same method for setting up x11vnc in 9.04 and everything went swimmingly.
Can anyone suggest how I might fix x11vnc please? 

Thanks in advance!

---

### Post by krunge on 2009-11-05
I have a test machine running ubuntu 9.10 and I think I see what is the problem.

Using a vanilla test user 'fred' from a terminal **inside** his desktop session I see:
```

fred@testbox:~$ echo $XAUTHORITY
/var/run/gdm/auth-for-fred-s0G6r1/database
fred@testbox:~$ xauth list
testbox/unix:0  MIT-MAGIC-COOKIE-1  646e3cc6fef51b9fad5a1c3f427aae5a

```
and starting x11vnc (or of course any other X client) works fine in there.

Note that the XAUTHORITY cookie file is over in /var/run/gdm/auth-for-fred...

However if I ssh in I get this instead:
```

fred@testbox:~$ echo $XAUTHORITY

fred@testbox:~$ xauth list
testbox/unix:10  MIT-MAGIC-COOKIE-1  e070f5c02f5d540b159e4b612ef2faf3

```
The unset XAUTHORITY means ~/.Xauthority will be used by default, and the xauth list for it only gives a ssh X11 forwarding, not the display :0 one. Trying to start x11vnc in the ssh shell fails.

Does your environment look more or less like this?

It's not clear what to do inside the ssh shell besides digging out the path to the xauthority file and using it explicitly:
```

x11vnc -display :0 -auth /var/run/gdm/auth-for-fred-s0G6r1/database ...

```
Later I will check if GDM can be configured to use ~/.Xauthority

---

### Post by (-NINJ4-) on 2009-11-05
The following is all from a local terminal:
```
mflame@NINJ4:~$ sudo echo $DISPLAY
:0.0
mflame@NINJ4:~$ echo $XAUTHORITY
/var/run/gdm/auth-for-mflame-6ZNfae/database
mflame@NINJ4:~$ xauth list
NINJ4/unix:0  MIT-MAGIC-COOKIE-1  f6f4ebcced89a960c522686758b3ce7e
mflame@NINJ4:~$ 
mflame@NINJ4:~$ x11vnc -rfbauth ~/.vnc/x11vnc.pass -display localhost:0.0
05/11/2009 11:23:22 passing arg to libvncserver: -rfbauth
05/11/2009 11:23:22 passing arg to libvncserver: /home/mflame/.vnc/x11vnc.pass
05/11/2009 11:23:22 x11vnc version: 0.9.3 lastmod: 2007-09-30

05/11/2009 11:23:22 ***************************************
05/11/2009 11:23:22 *** XOpenDisplay failed (localhost:0.0)

*** x11vnc was unable to open the X DISPLAY: "localhost:0.0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

Some tips and guidelines:

 * An X server (the one you wish to view) must be running before x11vnc is
   started: x11vnc does not start the X server.  (however, see the
   recent -create option if that is what you really want).

 * You must use -display <disp>, -OR- set and export your $DISPLAY
   environment variable to refer to the display of the desired X server.
 - Usually the display is simply ":0" (in fact x11vnc uses this if you forget
   to specify it), but in some multi-user situations it could be ":1", ":2",
   or even ":137".  Ask your administrator or a guru if you are having
   difficulty determining what your X DISPLAY is.

 * Next, you need to have sufficient permissions (Xauthority) 
   to connect to the X DISPLAY.   Here are some Tips:

 - Often, you just need to run x11vnc as the user logged into the X session.
   So make sure to be that user when you type x11vnc.
 - Being root is usually not enough because the incorrect MIT-MAGIC-COOKIE
   file will be accessed.  The cookie file contains the secret key that
   allows x11vnc to connect to the desired X DISPLAY.
 - You can explicity indicate which MIT-MAGIC-COOKIE file should be used
   by the -auth option, e.g.:
       x11vnc -auth /home/someuser/.Xauthority -display :0
       x11vnc -auth /tmp/.gdmzndVlR -display :0
   you must have read permission for the auth file.

 - If NO ONE is logged into an X session yet, but there is a greeter login
   program like "gdm", "kdm", "xdm", or "dtlogin" running, you will need
   to find and use the raw display manager MIT-MAGIC-COOKIE file.
   Some examples for various display managers:

     gdm:     -auth /var/gdm/:0.Xauth
     kdm:     -auth /var/lib/kdm/A:0-crWk72
     xdm:     -auth /var/lib/xdm/authdir/authfiles/A:0-XQvaJk
     dtlogin: -auth /var/dt/A:0-UgaaXa

   Only root will have read permission for the file, and so x11vnc must be run
   as root.  The random characters in the filenames will of course change,
   and the directory the cookie file resides in may also be system dependent.
   Sometimes the command "ps wwwaux | grep auth" can reveal the file location.

See also: [http://www.karlrunge.com/x11vnc/#faq](http://www.karlrunge.com/x11vnc/#faq)
mflame@NINJ4:~$ x11vnc -auth /var/run/gdm/auth-for-mflame-6ZNfae/database -rfbauth ~/.vnc/x11vnc.pass -display localhost:0.0
05/11/2009 11:25:52 passing arg to libvncserver: -rfbauth
05/11/2009 11:25:52 passing arg to libvncserver: /home/mflame/.vnc/x11vnc.pass
05/11/2009 11:25:52 x11vnc version: 0.9.3 lastmod: 2007-09-30

05/11/2009 11:25:52 ***************************************
05/11/2009 11:25:52 *** XOpenDisplay failed (localhost:0.0)

*** x11vnc was unable to open the X DISPLAY: "localhost:0.0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

Some tips and guidelines:

<SNIP, same thing as above>

See also: [http://www.karlrunge.com/x11vnc/#faq](http://www.karlrunge.com/x11vnc/#faq)

```I get the same error when I just use "-display :0" for the two commands above, as well.

---

### Post by krunge on 2009-11-05
> **(-NINJ4-) said:**
> The following is all from a local terminal:
```
mflame@NINJ4:~$ sudo echo $DISPLAY
:0.0
mflame@NINJ4:~$ echo $XAUTHORITY
/var/run/gdm/auth-for-mflame-6ZNfae/database
mflame@NINJ4:~$ xauth list
NINJ4/unix:0  MIT-MAGIC-COOKIE-1  f6f4ebcced89a960c522686758b3ce7e

mflame@NINJ4:~$ x11vnc -rfbauth ~/.vnc/x11vnc.pass -display localhost:0.0
05/11/2009 11:23:22 passing arg to libvncserver: -rfbauth
05/11/2009 11:23:22 passing arg to libvncserver: /home/mflame/.vnc/x11vnc.pass


```I get the same error when I just use "-display :0" for the two commands above, as well.

I don't think one should ever use a display "localhost:0.0" because I believe that implies a TCP socket connection which is disabled for Linux X servers these days.

I'm confused why you would run "sudo echo $DISPLAY".  Besides $DISPLAY already being expanded in your non-sudo shell, I can't see any reason for using "sudo" for any of this troubleshooting. We want to do all of this (x11vnc access) as the user mflame. So please don't run any commands as sudo.

I'm also surprised you see this problem using :0.0 as well. I'm going to ask you to do it again just to be sure.  I assume user mflame is logged in to the X desktop.  Please run this as user mflame in a shell outside of the desktop (e.g. ssh login or Ctrl+Alt+F1 console login.)
```

echo $DISPLAY
echo $XAUTHORITY
xauth list $DISPLAY
xdpyinfo -display :0
env XAUTHORITY=/var/run/gdm/auth-for-mflame-6ZNfae/database xdpyinfo -display :0

```
Where the last line you got XAUTHORITY from inside the desktop session (i.e. in a terminal window.)

Well, the above is not really optimal, but please send it when you can.  I realize now I don't understand what you mean by 'local terminal'.  You mean one inside the desktop session or something else??

Thanks

---

### Post by (-NINJ4-) on 2009-11-05
All of the following was run from a remote SSH connection into the computer:
```
mflame@NINJ4:~$ echo $DISPLAY

mflame@NINJ4:~$ echo $XAUTHORITY

mflame@NINJ4:~$ xauth list $DISPLAY
NINJ4/unix:11  MIT-MAGIC-COOKIE-1  337ca3f6d0c5c86517a2278ee4d66a5f
NINJ4/unix:20  MIT-MAGIC-COOKIE-1  98b35db5e229001a3fd75fb5470dc858
NINJ4:20  MIT-MAGIC-COOKIE-1  98b35db5e229001a3fd75fb5470dc858
mflame@NINJ4:~$ xdpyinfo -display :0
No protocol specified
xdpyinfo:  unable to open display ":0".
mflame@NINJ4:~$ env XAUTHORITY=/var/run/gdm/auth-for-mflame-6ZNfae/database xdpyinfo -display :0
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    10604000
X.Org version: 1.6.4
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x3200371, revert to Parent
number of extensions:    29
    BIG-REQUESTS
    Composite
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    DRI2
    GLX
    Generic Event Extension
    MIT-SCREEN-SAVER
    MIT-SHM
    NV-CONTROL
    NV-GLX
    RANDR
    RECORD
    RENDER
    SECURITY
    SHAPE
    SYNC
    X-Resource
    XC-MISC
    XFIXES
    XFree86-DGA
    XFree86-VidModeExtension
    XINERAMA
    XINERAMA
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1280x720 pixels (602x345 millimeters)
  resolution:    54x53 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x13c
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0x7a807f
    KeyPressMask             KeyReleaseMask           ButtonPressMask          
    ButtonReleaseMask        EnterWindowMask          LeaveWindowMask          
    PointerMotionMask        ExposureMask             StructureNotifyMask      
    SubstructureNotifyMask   SubstructureRedirectMask FocusChangeMask          
    PropertyChangeMask       
  number of visuals:    84
  default visual id:  0x21
  visual:
    visual id:    0x21
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x22
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x24
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x25
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x26
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x27
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x28
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x29
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2a
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2b
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2c
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2d
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2e
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2f
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x30
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x31
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x32
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x33
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x34
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x35
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x36
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x37
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x38
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x39
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3a
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3b
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3c
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3d
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3e
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3f
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x40
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x41
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x42
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x43
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x44
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x45
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x46
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x47
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x48
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x49
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4a
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4b
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4c
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4d
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4e
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4f
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x50
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x51
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x52
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x53
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x54
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x55
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x56
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x57
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x58
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x59
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x23
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5a
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5b
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5c
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5d
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5e
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5f
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x60
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x61
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x62
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x63
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x64
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x65
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x66
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x67
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x68
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x69
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x6a
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x6b
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x6c
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x6d
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x6e
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x6f
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x70
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x71
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x72
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x73
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x74
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
```Yes, when I said a local terminal I meant I ran those commands while sitting at the physical computer using gnome-terminal.  Sorry about using a sudo command, I found it while googling for similar problems, and thought it might help.  I had a similar reason behind using :0.0, I was unsure which was the proper way of doing it, so I tried both.  Also, yes user mflame is currently logged into an X session.  Sorry about any confusion I may have caused.

Also, because of the output of xauth list, I decided to try the following to see if they might work, but none of them did, and all created the same error as I have been getting with any x11vnc -display command:

```
  x11vnc -rfbauth ~/.vnc/x11vnc.pass -display NINJ4/unix:11
  x11vnc -rfbauth ~/.vnc/x11vnc.pass -display NINJ4/unix:20
  x11vnc -rfbauth ~/.vnc/x11vnc.pass -display NINJ4:11
  x11vnc -rfbauth ~/.vnc/x11vnc.pass -display :11
  x11vnc -rfbauth ~/.vnc/x11vnc.pass -display :20
  x11vnc -auth /var/run/gdm/auth-for-mflame-6ZNfae/database -rfbauth ~/.vnc/x11vnc.pass -display :11
  x11vnc -auth /var/run/gdm/auth-for-mflame-6ZNfae/database -rfbauth ~/.vnc/x11vnc.pass -display :20

```

---

### Post by krunge on 2009-11-05
In the same shell where you successfully ran:
```

mflame@NINJ4:~$ env XAUTHORITY=/var/run/gdm/auth-for-mflame-6ZNfae/database xdpyinfo -display :0
name of display:    :0.0
version number:    11.0
...

```
then this x11vnc command *must* also succeed:
```

flame@NINJ4:~$ x11vnc -auth /var/run/gdm/auth-for-mflame-6ZNfae/database -display :0

```
I say this because both xdpyinfo and x11vnc are X clients trying to connect to display :0 (and x11vnc's -auth option sets XAUTHORITY to its option value.)

Please try the above x11vnc command in the same shell where xdpyinfo works.  If that doesn't work, paste the output here (you can skip the stuff after 'tips and guidlines'...)

---

### Post by (-NINJ4-) on 2009-11-06
```
06/11/2009 00:05:16 passing arg to libvncserver: -rfbauth
06/11/2009 00:05:16 passing arg to libvncserver: /home/mflame/.vnc/x11vnc.pass
06/11/2009 00:05:16 x11vnc version: 0.9.3 lastmod: 2007-09-30
06/11/2009 00:05:16 Using X display :0
....
```Not sure why it suddenly decided this was okay, could have sworn I already tried this or something similar in one of my numerous earlier attempts, but whatever.  

Thanks a ton for helping me get this working :D!  Problem solved :)

---

