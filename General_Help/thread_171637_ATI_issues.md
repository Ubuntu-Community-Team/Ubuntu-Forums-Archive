---
title: "ATI issues"
date: 2006-05-07
forum: General Help
---

### Post by admrly06 on 2006-05-07
I installed the ATI drivers with no problems. Under Applications there's the ATI panel but when I open it it says " Fire GL x11 extensions not found " ( or something to that effect " and when it opens it only has the info tab. Whats am I doing wrong?

---

### Post by chicken101 on 2006-05-07
[QUOTE=admrly06]I installed the ATI drivers with no problems. Under Applications there's the ATI panel but when I open it it says " Fire GL x11 extensions not found " ( or something to that effect " and when it opens it only has the info tab. Whats am I doing wrong?[/QUOTE]


Yeah, you just need to configure the drivers (add it to the xorg.conf file).  Go into the terminal and type "aticonfig".  

> Usage: aticonfig [OPTION] ...
Parses an existing X-Server configuration file and modifies it to operate with
ATI products.

The following command-line options can be invoked as parameters:

ATI Initial Configuration:
  --initial
        Generate a default ATI device section in the configuration file which
        is capable of loading the fglrx driver.
  --initial=dual-head
        Same as '--initial' but generate a basic dual head configuration file.

TV Options:
  --tvf, --tv-format-type=STRING
        Change the TV signal format.  STRING can be one of:
            NTSC-M
            NTSC-JPN
            PAL-B
            PAL-D
            PAL-G
            PAL-H
            PAL-I
            PAL-K
            PAL-K1
            PAL-L
            PAL-M
            PAL-N
            PAL-CN
            PAL-SCART
  --tvs, --tv-standard-type=STRING
        Change the TV standard for TV output.  STRING can be one of:
            VIDEO
            SCART
            YUV

FireGL Workstation Board Features:
  --app, --use-app-profile=STRING
        Change the application profile for a FireGL workstation board.
        STRING can be one of:
            default
            maya
            softimage-xsi
            softimage-3d
            houdini4.0
            houdini5.0
            houdini5.5
FSAA Options:
  --fsaa={on|off}
        Enable/disable full scene anti-aliasing.  Enable this option to enhance
        photo-realism in 3D rendering.  Disable it to get the most accurate 3D
        image.
  --fs, --fsaa-samples={off,0,2,4,6}
        Set the number of FSAA samples per pixel or 2, 4, 6.  off is the same
        as setting 0 samples.
  --fsg, --fsaa-gamma={on|off}
        Enable/disable FSAA gamma.
  --fmsp, --fsaa-ms-positions=x0,y0,x1,y1,x2,y2,x3,y3,x4,y4,x5,y5
        Change the FSAA Multi-Sample Positions for x0,y0 to x5,y5.  You must
        specify exactly 12 real number values separated by commas.

Screen-Related Options:
  --ovt, --overlay-type=STRING
        Change the overlay for the X server.  STRING can be one of:
            opengl
            Xv
            disable
  --ovon, --overlay-on={0|1}
        Choose which head the hardware overlay should be visible on.  The
        hardware overlay can be used for either OpenGL, video, pseudo-color
        or stereo.
  --lcd, --lcd-mode=STRING
        Change the LCD mode.  STRING can be one of:
            center
            full
  --dtop, --desktop-setup=STRING
        Change the desktop setup for multiple display adapters.
        STRING can be one of:
            single              1 screen, second dark
            mirror              2 screens - same content, identical
                                refresh rate/resolution
            clone               2 screens - same content, allows for
                                different refresh rates/resolutions
            horizontal          2 screens - one framebuffer,
                                screen 1 right of screen 0
            horizontal,reverse  2 screens - one framebuffer,
                                screen 1 left of screen 0
            vertical            2 screens - one framebuffer,
                                screen 1 above of screen 0
            vertical,reverse    2 screens - one framebuffer,
                                screen 1 below of screen 0
        Note:  This option is not valid if '--initial=dual-head' is specified.
  --vs, --sync-vsync={on|off}
        Enable/disable sync buffer swaps with vsync.  Enable this option to
        prevent tearing during 3D rendering.
  --psc, --pseudo-color={on|off}
        Enable/disable pseudo-color visuals.  Enable this option to get 16-bit
        color support.
  --stereo={on|off}
        Enable/disable quad-buffer stereo support.  Enable this option only for
        using applications that support the use of hardware 3D shutter glasses.
  --ss, --stereo-sync={on|off}
        Enable/disable quad-buffer stereo sync.  Enable this option to get 3D
        glasses to synchronize with the infrared transmitter.
  --resolution=W1xH1,W2xH2,W3xH3,...
        Set the modes for the first screen.  You may specify several
        resolutions separated by commas.
  --hsync=LOW-HIGH
        Change the horizontal sync range of the first monitor.  Make sure you
        know the capabilities of your monitor before changing this option.
  --vrefresh=LOW-HIGH
        Change the vertical refresh range of the first monitor.  Make sure you
        know the capabilities of your monitor before changing this option.
  --resolution2=W1xH1,W2xH2,W3xH3,...
        Change the modes for the second screen for dual head.  You may specify
        several resolutions separated by commas.
        Note:  The secondary screen must exist.
  --hsync2=LOW-HIGH
        Change the horizontal sync range of the second display.  Make sure you
        know the capabilities of your monitor before changing this option.
  --vrefresh2=LOW-HIGH
        Change the vertical refresh range of the second display.  Make sure you
        know the capabilities of your monitor before changing this option.
  --mode2=W1xH1,W2XH2,W3xH3,...
        Change the modes for the second display.  You may specify several
        resolutions separated by commas.  Only valid for clone and big desktop
        settings.
  --screen-layout={left|right|above|below}
        Set the secondary screen position for dual head.
  --screen-overlap=NUM
        Set the screen overlap region in big desktop mode to be NUM pixels.
  --force-monitor=STRING[,STRING...]
        Describe all displays that are to be enabled and/or disabled regardless
        of physical connection.  STRING can be one or more of the following
        set, separated by commas:
            crt1
            crt2
            lvds
            tv
            tmds1
            tmds2
            tmds2i
            nocrt1
            nocrt2
            nolvds
            notv
            notmds1
            notmds2
            notmds2i

POWERplay Options:
  --lsp, --list-powerstates
        Print information about power states and exit.
  --set-powerstate=NUMBER
        Set a power state listed by --list-powerstates.

Advanced Options:
  --tls={on|off}
        Enable/disable fast thread local storage.  Disable this option when
        virtual machines or WineX fail to work properly.
  --sb, --signal-block={on|off}
        Enable/disable signal blocking.  Disable this option when debugging a
        multi-threaded OpenGL application.
  --iagp, --internal-agp={on|off}
        Enable/disable internal AGP gart.  Enable this option to use the ATI
        AGP GART module.  Disable it to use the module included with the Linux
        kernel.  Changing this option may help resolve display-related issues.
  --agpl, --agp-locked-userpages={on|off}
        Enable/disable AGP locked user pages. Disable this option if the system
        hangs when running fgl_glxgears.
  --gcpu, --generic-cpu={on|off}
        Enable/disable generic CPU.  Use this option if the CPU is being
        reported improperly.  For example: If you have an AMD cpu that is
        being reported as Intel.

Miscellaneous Options:
  -v, --verbose
        Show what aticonfig is doing.
  -q, --quiet
        Disable all information output except for errors.
  --effective={now,startup}
        Choose when the requested changes should take effect.
            now:     Immediately.  This change will affect the running X
                     session if applicable.  Only 'set-powerstate' and
                     'overlay-on' are applicable for now.
            startup: On future X server startups.  This change will modify the
                     X server configuration file if applicable.
        The default is 'now,startup', i.e., do both as applicable.
  -i, --input=FILE
        Select a FILE to input as the configuration file. Set FILE to '-' to
        pipe from standard input.  Without this option, aticonfig will search
        /etc/X11 for the default configuration file.
  -o, --output=FILE
        Select a FILE to output the new configuration file to.  Set FILE to '-'
        to print to standard output.  Without this option, aticonfig will
        replace the input file with the newly generated file.
  -h, --help
        Display this help screen.
  -f, --force
        Only valid with 'initial' option.  Force aticonfig to generate default
        Monitor, Device, and Screen sections even if the original configuration
        file has invalid settings in these sections.

Examples:
  1. Setting up fglrx for the first time.
       Single head :    aticonfig --initial --input=/etc/X11/xorg.conf
       Dual head   :    aticonfig --initial=dual-head --screen-layout=above
                        This command will generate a dual head configuration
                        file with the second screen located above the first
                        screen.
  2. Setting up big desktop to horizontal and set overlay on secondary display.
                        aticonfig --dtop=horizontal --overlay-on=1
  3. Setting up modes for primary display.
                        aticonfig --resolution=1600x1200,1280x1024,1024x768
  4. Force primary CRT on and TV-out off.
                        aticonfig --force-monitor=crt1,notv

Please report bugs to [http://support.ati.com](http://support.ati.com)


You'll get something that looks like the quote above.  Do a:> aticonfig --initial --input=/etc/X11/xorg.conf

To set up your drivers for the first time.  If it can't find aticonfig, do:
> sudo dpkg-reconfigure xserver-xorg  
In the wizard, instead of choosing the normal "ati" drivers, choose the frglx drivers from the list, then finish the wizard so it writes those changes to the xserver-xorg.conf file, located in ect/X11/xorg.conf

---

### Post by se7ensamurai on 2006-05-09
hey guys, I'm having a similar problem, but whenever I try to run the aticonfig this is what I get:
> bash: aticonfig: command not found

so I check the install instructions on the ATI site, and it says to run this:
>  /usr/X11R6/bin/aticonfig --initial

but I get this:
> /usr/X11R6/bin/aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory

So, what am I doing wrong here? I've looked in that directory with File Browser, and its there...and I've been searching the forums for days trying to figure this out. I almost just went and edited the xorg.conf, but I'm affraid I'll screw something up.

Really the only articles I can find about setting up TV out are geared towards Nvidia cards (not surprising). What I find strange is that with the SVideo connected to the TV, it looks like theres just something wrong with the refresh rate.

thanks in advance for any help yall can give.

(btw: its a radeon 9600)

*-update-I just noticed that the install GUI says to save the xwindow configuration...*

---

### Post by jclose on 2006-05-10
Did you get your problem figured out se7ensamurai?  I am having the same issue.  I installed the drivers OK, but when I run the "aticonfig" command I get:

[COLOR="MediumTurquoise"]aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory[/COLOR]

Thanks,
J

---

### Post by 04nmr85 on 2006-05-11
I'm having the same exact problems with mine jclose.

---

### Post by chrisHHde on 2006-05-12
I have the same problem..... I notice that the library aticonfig is looking for actually resides in /usr/X11R6/lib, named libfglrx_pp.so.1.0. So I made a symlink pointing at that library, named libfglrx_pp.so.1. But that didn't resolve the problem.

I guess there has something got to be done to make the library known generally, but just running ldconfig doesn't do the trick. I'm not ultimately firm with installations and how to make libraries known in the system.... anyone else?

Looks like a minor bug.

Btw, I have Kubuntu 5.10 on an AMD64 machine. Radeon Mobility 9600.

EDIT: Okay, I guess I know why..... in /etc/ld.so.conf there are only the 32-bit library directories listed.... does anyone know why?? I wonder if I break anything if I add the 64-bit library directories..... then running ldconfig should make the library known to the system (and aticonfig). But I wonder if that's the way it should be..... I can't imagine that ubuntu developers simply forget about something like that... they must have left out the 64-bit libraries on purpose...!?

---

### Post by chicken101 on 2006-05-13
Ok, I used to have this problem (but I forget  what I did).  I think it was something like this..

> sudo apt-get install xorg-driver-fglrx

> sudo apt-get install xserver-xorg-driver-ati

Reboot, and then try..

> aticonfig

If that works, do...

> sudo dpkg-reconfigure xserver-xorg

Choose the fglrx driver instead of the default ati driver.

That should solve the problem guys, cheers, and good luck!

---

### Post by gitargr8 on 2006-05-14
I followed your instructions to the letter and it still doesn't recognize the aticonfig command. I'm using kubuntu, don't know if that makes a difference...

---

### Post by 00Kevin on 2006-05-14
If you installed the fglrx driver. You should be running "fglrxconfig" instead. You might also want to run "fglrxinfo" and "fgl_glxgears" after setting up your /etc/X11/xorg.conf to make sure ever thing is working ok.

---

### Post by morgengenuss on 2006-05-15
i can remember having had this "libfglrx_pp.so.1" issue as well.
i fiddled around a while and found and followed the instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)
now everything works fine (although i couldn't tell the difference between these instructions and what i had tried before).:-D 

actually i seem to have managed to switch on opengl manually in the xorg.conf, but what really annoyes me is the fact that linux doesn't remember the gamma-values i tell aticonfig to use.:confused: 

furthermore: can anyone tell me how do adjust brightness and contrast values in linux for my ati x1400?

---

### Post by ulises on 2006-05-16
I have installed the new ATI driver (for notebooks) and I've done everything; however, when I rebooted, X did not work :( -- it showed a blue scree saying the x server was not ok and it redirected me to command line where I just deleted the new xorg.conf and used the old one.
Firefox Start		Firefox Logo	Firefox Logo
	
	
why it did not work? what else do I need?


PS: my card:
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 01)

thx in advance

EDIT:

I thinks this might be the problem

FATAL: Error inserting fglrx (/lib/modules/2.6.16-ck3/misc/fglrx.ko): Operation not permitted

what to do now?

---

### Post by ysr on 2006-09-13
Hi all, I am having some problems with the ```
aticonfig --set-powerstate=N
```. Sometimes this works absolutely fine, allowing me to switch between the three power states listed for my card, at other times, the screen just goes blank (white or black) and the system has to be hard rebooted.

I have ATI x1300 mobility radeon card with 128 MB hypermemory (i.e. 64MB shared with main memory :-k ), screen resolution 1280x800, latest fglrx drivers.

Anybody else experiencing similar issues. Any ideas what might be causing it and how to work around.

---

