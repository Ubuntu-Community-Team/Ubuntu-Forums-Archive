---
title: "gdm error after update"
date: 2006-06-15
forum: General Help
---

### Post by pRedat0r on 2006-06-15
Hi,

I just installed todays huge batch of updates (which included gdm), and now I am stuck with gdm yelling at me that something is wrong, but I havent been able to figure out what it is.  Any help would be appreciated.

When it tells me that something is whacked out and I tell it to show me what it gives me the error: "Unrecognized option: vt7" along with a bunch of options..

Here is the :0.log from /var/log/gdm/
```

Unrecognized option: vt7
use: X [:<display>] [option]
-a #                   mouse acceleration (pixels)
-ac                    disable access control restrictions
-audit int             set audit trail level
-auth file             select authorization file
bc                     enable bug compatibility
-br                    create root window with black background
+bs                    enable any backing store support
-bs                    disable any backing store support
-c                     turns off key-click
c #                    key-click volume (0-100)
-cc int                default color visual class
-co file               color database file
-core                  generate core dump on fatal error
-dpi int               screen resolution in dots per inch
dpms                   enables VESA DPMS monitor control
-dpms                  disables VESA DPMS monitor control
-deferglyphs [none|all|16] defer loading of [no|all|16-bit] glyphs
-f #                   bell base (0-100)
-fc string             cursor font
-fn string             default font name
-fp string             default font path
-help                  prints message with these options
-I                     ignore all remaining arguments
-ld int                limit data space to N Kb
-lf int                limit number of open files to N
-ls int                limit stack space to N Kb
-nolock                disable the locking mechanism
-logo                  enable logo in screen saver
nologo                 disable logo in screen saver
-nolisten string       don't listen on protocol
-noreset               don't reset after last client exists
-reset                 reset after last client exists
-p #                   screen-saver pattern duration (minutes)
-pn                    accept failure to listen on all ports
-nopn                  reject failure to listen on all ports
-r                     turns off auto-repeat
r                      turns on auto-repeat 
-render [default|mono|gray|color] set render color alloc policy
-s #                   screen-saver timeout (minutes)
-sp file               security policy file
-su                    disable any save under support
-t #                   mouse threshold (pixels)
-terminate             terminate at server reset
-to #                  connection time out
-tst                   disable testing extensions
ttyxx                  server started from init on /dev/ttyxx
v                      video blanking for screen-saver
-v                     screen-saver without video blanking
-wm                    WhenMapped default backing-store
-x string              loads named extension at init time 
-maxbigreqsize         set maximal bigrequest size 
+xinerama              Enable XINERAMA extension
-xinerama              Disable XINERAMA extension
-dumbSched             Disable smart scheduling, enable old behavior
-schedInterval int     Set scheduler interval in msec
+extension name        Enable extension
-extension name        Disable extension
-query host-name       contact named host for XDMCP
-broadcast             broadcast for XDMCP
-multicast [addr [hops]] IPv6 multicast for XDMCP
-indirect host-name    contact named host for indirect XDMCP
-port port-num         UDP port number to send messages to
-from local-address    specify the local address to connect from
-once                  Terminate server after one session
-class display-class   specify display class to send in manage
-displayID display-id  manufacturer display ID for request
-kb                    disable the X Keyboard Extension
+kb                    enable the X Keyboard Extension
[+-]accessx [ timeout [ timeout_mask [ feedback [ options_mask] ] ] ]
                       enable/disable accessx key sequences
-ardelay               set XKB autorepeat delay
-arinterval            set XKB autorepeat interval
-xkbmap                XKB keyboard description to load on startup

Xgl usage:
-ddx module            specify ddx module
-noglx                 don't load glx extension
-glxlog file           glx extension log file
-vertextype [short|float] set vertex data type
-yinverted             Y is upside-down
-lines                 accelerate lines that are not vertical or horizontal
-noyuv                 turns off hardware color-space conversion of YUV data
-xvfilter [nearest|linear] set xvideo filter
-vbo                   use vertex buffer objects for streaming of vertex data
-pbomask [1|4|8|16|32] set bpp's to use with pixel buffer objects
-accel TYPE[@WIDTH[/MIN]xHEIGHT[/MIN]][:METHOD] offscreen acceleration

Xglx usage:
-screen WIDTH[/WIDTHMM]xHEIGHT[/HEIGHTMM] specify screen characteristics
-fullscreen            run fullscreen
-display string        display name of the real server
-softcursor            force software cursor

Fatal server error:
Unrecognized option: vt7

```

after seeing that error I went on the hunt to fix the issue, I found the following in my gdm.conf:

> # Automatic VT allocation.  Right now only works on Linux.  This way we force
# X to use specific vts.  turn VTAllocation to false if this is causing
# problems.
FirstVT=7
VTAllocation=true


I duped the line and commented out the original, then set the dupe to be false: "VTAllocation=false" and went back to the prompt and restarted gdm and it still failed.

NOTE:  Once I log in on the text login screen, i can do a startx and everything starts up just fine.

Help?  Anyone else have this problem?

Thanks in advance for the help!

---

### Post by mlind on 2006-06-15
I updated too, but didn't get that error. Are you using xgl ?

---

### Post by pRedat0r on 2006-06-15
I installed XGL a few days back, but could never get it to work so I removed all of the edits that I had made to gdm.conf and gdm.conf-custom, which were to switch the display to 1 (1=Standard in gdm.conf), and adding new sections in the gdm.conf-custom file.

After I removed all of that stuff I had rebooted and everything was fine.

Guess I'll try to remove the xgl and compiz stuff and see if that helps.  Hopefully it cant hurt anything!

I'll post back shortly if it solved the issue.

Thanks

---

### Post by pRedat0r on 2006-06-15
well,

I uninstalled compiz-gnome, then compiz, then xgl (cant remember the exact package name), rebooted, and everything seems to be working again.  Must have been a compiz or xgl update that somehow hosed up something.

If any other people had issues with gdm and xgl/compiz, maybe a remove/reinstall of those packages is in order?

Thanks for your help, I thought it had to be something that got updated with gdm, didnt think it could have been the xgl stuff that was sitting around (unused -- although I wish I could have gotten it working!).

---

