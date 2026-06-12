---
title: "how do i install or run vnc viewer"
date: 2011-01-22
forum: General Help
---

### Post by bluenose1982 on 2011-01-22
Hi,  I'm trying to install my first program and need a bit of guidance please.

 I've downloaded Real VNC but i have no idea how to install it, or maybe it stands alone and runs??

it came as a tar.gz file which i've managed to extract in gui but then i tried to double click the vncinstall or vncviewer.exe and nothing seems to happen

the files are
license.txt
readme (readme document)
vnc.so
vncconfig (executable)
vncconfig.man (troff document)
vncinstall (shell script)
vncpasswd (executable)
vncpasswd.man (troff document)
vncserver (perl script)
vncserver.man (troff document)
vncviewer (executable)
vncviewer.man (troff document)
x0vncserver (executable)
x0vncserver.man (troff document)
Xvnc (executable)
Xvnc.man (troff document)

some info from readme;

 vncviewer - this is the VNC viewer, or client, program for X. (its this i want to use, what is X)

and some more;


In addition to these standalone programs, on Linux platforms this distribution
can also be used to turn a native XFree86 version 4 X server into a VNC server.
This is done using a module loaded at run-time.  On other platforms, VNC
support can only be added by replacing the native X server binary - you must
build from the source distribution if this is what you want.

You need a reasonably recent version of the X window system installed.  This
come as standard with most unix machines.  If you don't have it
installed, see [http://www.xfree86.org](http://www.xfree86.org) or [http://www.x.org](http://www.x.org)

You should copy the programs to some directory which is in your PATH
environment variable, such as /usr/local/bin.  You can use the vncinstall
script to do this for you:

  % ./vncinstall /usr/local/bin

This will also attempt to install the manual pages in an appropriate directory.
You can specify an alternative directory as a second argument to vncinstall:

  % ./vncinstall /usr/local/bin /usr/local/man

It will also try to install the vnc.so XFree86 version 4 module if appropriate.
This will be copied to the /usr/X11R6/lib/modules/extensions directory and can
be enabled like any other module by adding a Load "vnc" line to the Module
section of XF86Config.  The parameters listed in the Xvnc manual page can be
set as options in XF86Config e.g. Option "passwordFile" "/root/.vnc/passwd".
Note that for some reason options cannot be set in the Module section of
XF86Config - try the Screen section.

If you want to use the Java VNC viewer, you should copy the files from
the java directory to some suitable installation directory such as
/usr/local/vnc/classes:

  % mkdir -p /usr/local/vnc/classes
  % cp java/* /usr/local/vnc/classes

We recommend that you use the vncserver script to run Xvnc for you.  You can
edit the script as appropriate for your site.  Things you may need to change
include:

 * The location of Perl - if Perl is not installed in /usr/bin you'll need
   to edit the "#!/usr/bin/perl" first line of vncserver.

 * Xvnc's font path and color database.  If you have an installation of
   X which is not in the standard place you may need to add arguments to the
   Xvnc command line to set these.  These should be appended to the $cmd
   variable at the comment "# Add font path and color database...".

 * $vncJavaFiles - this specifies the location of the files for
   the VNC viewer Java applet.  The default is /usr/local/vnc/classes

---

### Post by Foxheadz on 2011-01-22
well if there is a .exe file then it sounds more for windows... Are you sure you donwloaded then one for ubuntu? I would recommend just using vinagre wich should come by default with ubuntu or if you don't have it just run ```
sudo apt-get install vinagre
```

---

### Post by endotherm on 2011-01-22
vinagre should be installed by default. you can also install tight, real or xvnc4viewer from the repos.

[http://ubuntuforums.org/showthread.php?t=600368](http://ubuntuforums.org/showthread.php?t=600368)
[http://ubuntuforums.org/showthread.php?t=314697](http://ubuntuforums.org/showthread.php?t=314697)
[http://packages.ubuntu.com/search?keywords=xvnc4viewer](http://packages.ubuntu.com/search?keywords=xvnc4viewer)

---

### Post by bluenose1982 on 2011-01-22
I should have explained, i have a computer already running windows and the realvnc server i want to connect to.  This is definitely the version for linux i downloaded.

is vinagre able to connect to realvnc?

Anyhow I typed sudo apt-get vinagre anyway, (can you explain what that means please so i learn as i go) and it just said E: Invalid operation vinagre

---

### Post by howefield on 2011-01-22
> **bluenose1982 said:**
> Anyhow I typed sudo apt-get vinagre anyway, 

It is sudo apt-get install vinagre

You could try opening Applications > Internet > Terminal Server Client, change the Protocol to VNC and connect to your windows box.

---

### Post by bluenose1982 on 2011-01-22
Brilliant it's working! cheers guys.  There's two programs 'Terminal Server Client' which i'm not so keen on and 'Remote Desktop Viewer' which is perfect!

Now in the name of me actually learning something from this;

1.  Was remote desktop viewer there all along? (i only ask because i was messing about in ubuntu software center looking for a vnc viewer and didn't know if i added it.

2. sudo apt-get install vncviewer <-- what did each bit of that command do?? 

3. How from that command did it know to install xtightvncviewer and where did it go? I expected a new option to appear in the menus called tightvnc.... but it was just a protocol in terminal server client???

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xtightvncviewer' instead of 'vncviewer'
Suggested packages:
  tightvncserver ssh
The following NEW packages will be installed
  xtightvncviewer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 89.5kB of archives.
After this operation, 229kB of additional disk space will be used.
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe xtightvncviewer i386 1.3.9-6.1 [89.5kB]
Fetched 89.5kB in 0s (447kB/s)         
Selecting previously deselected package xtightvncviewer.
(Reading database ... 145169 files and directories currently installed.)
Unpacking xtightvncviewer (from .../xtightvncviewer_1.3.9-6.1_i386.deb) ...
Processing triggers for man-db ...
Setting up xtightvncviewer (1.3.9-6.1) ...
update-alternatives: using /usr/bin/xtightvncviewer to provide /usr/bin/vncviewer (vncviewer) in auto mode.

---

### Post by howefield on 2011-01-22
> **bluenose1982 said:**
> Was remote desktop viewer there all along?

Yes, it's part of a default Ubuntu install. 

> sudo apt-get install vncviewer <-- what did each bit of that command do??

sudo give you admin rights needed to carry out the command and apt-get install is the application used to fetch and install the package.

> How from that command did it know to install xtightvncviewer and where did it go?

xtightvncviewer can be driven from the terminal, it doesn't have a GUI by itself. It didn't need to be installed to use Remote Desktop Viewer.

---

### Post by bluenose1982 on 2011-01-22
thanks for all the help.  Very much enjoying this ubuntu experience, having this forum to back it up is quality

---

### Post by DoneRightI.T. on 2011-01-22
1. download the latest version of rvnc to a familiar place(in my case "Downloads"
2. copy the file to a more usable static location ie. Desktop
3. open a terminal [ alt-f2, "gnome-terminal" ]
4. `cd ~/Desktop/`
5. `chmod +x vnc-E4_6_0-x86_linux_viewer`
6. `./vnc-E4_6_0-x86_linux_viewer`

tada....

**** NOTE **** the above are not single quotes, I don't know the name of them... but on my keyboard are to the left of the 1

hope that helps some... to execute it afterwards just double click :)

---

### Post by endotherm on 2011-01-22
> **howefield said:**
> It is sudo apt-get install vinagre

You could try opening Applications > Internet > Terminal Server Client, change the Protocol to VNC and connect to your windows box.

sorry, I should have expounded. vinagre is the utility that the "Remote Desktop Viewer" launcher uses, hence it is usually installed by default. it is paired with the server, vino, that ubuntu uses for it's remote desktop sharing by default.

@op, any vnc viewer should be able to connect to any kind of vnc server. I often use vino on the server and xvnc4viewer on the client. some products may have options that only work with their server, but I haven't seen many of these. 

the remote desktop viewer (rdesktop) is another good option, and it can connect to the windows remote desktop service.

---

### Post by endotherm on 2011-01-23
> **DoneRightI.T. said:**
> 
**** NOTE **** the above are not single quotes, I don't know the name of them... but on my keyboard are to the left of the 1


those are called "Backquotes" in computer parlance, and are more correctly called "[Grave accents]("http://en.wikipedia.org/wiki/Grave_accent")"

---

