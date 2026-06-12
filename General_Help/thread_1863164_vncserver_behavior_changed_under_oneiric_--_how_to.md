---
title: "vncserver behavior changed under oneiric -- how to recover?"
date: 2011-10-17
forum: General Help
---

### Post by mathuin on 2011-10-17
I upgraded to oneiric and now vncserver does not do what I need it to do.

I have a headless system that needs to run an X11 program.  What I did under lucid, maverick, and natty was ssh into that system, start up vncserver, exit out, and then connect back to it with vncviewer.  Once vncviewer started up, I was able to use the GUI to select my application and run it.

When I attempt to do this after upgrading to oneiric, instead of seeing a familiar GUI, I see something that looks as if I opened a file manager like Nautilus.  The background looks good, but the top bar is grey with black writing:  File Edit View Go Bookmarks Help.  Deleting my entire ~/.vnc directory and starting over does not help.

What I need is either Gnome or Unity back.  How do I do this?  Thanks!

Jack.

---

### Post by spiky001 on 2011-10-17
Have you had a look at Remmina for remote desktop it works with ssh as well, it is in the repos

---

### Post by mathuin on 2011-10-17
> **spiky001 said:**
> Have you had a look at Remmina for remote desktop it works with ssh as well, it is in the repos
I looked over the web page for remmina and installed it, but it can't be run from the command line when I log in remotely via ssh, so it's not going to solve my problem.

Any other suggestions?

Jack.

---

### Post by areeda on 2011-10-19
I have the same issue using remmina or remote desktop.

I think you're right what we need is a Window Manager on the server that can work without hardware OpenGL.

Has anyone got this to work?

I think I'll try Unity 2D and see what happens.  Fortunately I do have a monitor on that system and use vncserver mostly from my bedroom when I want to watch TV and need more than my laptop.

I'll report back if that works.

Joe

---

### Post by areeda on 2011-10-19
Well, I think it's the desktop manage we need not window manager and I'm not sure how to start one.

I can put icons on the desktop and open multiple windows but I really want gnome or unity working and i can't figure out how to start them.

---

### Post by mlzarathustra on 2011-10-22
I had the same problem.  

The basic instructions I found here:
[http://faq.gotomyvnc.com/fom-serve/cache/56.html](http://faq.gotomyvnc.com/fom-serve/cache/56.html)

say to edit $HOME/.vnc/xstartup, adding the line 

exec gnome-session &

at the end.  Google turns up several sets of instructions that say basically the same thing.  Some leave out the exec, but I'm not sure it matters.


That did not work in "oneiric."  I believe that would start gnome, but not Unity had it worked.  With 11.0 I'm pretty sure it worked without any modification to xstartup.

---

### Post by areeda on 2011-10-22
I've also tried that and it doesn't work for me either.  I believe what's going on is we're still trying to run Unity.

My ~/.vnc/xstartup file looks like:

```
#!/bin/sh
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
vncconfig -iconic &
exec gnome-session &

```
When I open use remmina to open a vnc session I get an empty desktop with a menu from the standard file browser (I forgot what it's called) and I can go to /usr/bin and open an xterm.

The environment variables that seem to be relevant are:

```
XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/etc/xdg/xdg-ubuntu:/etc/xdg
XDG_CURRENT_DESKTOP=Unity
XDG_DATA_DIRS=/usr/share/ubuntu:/usr/share/gnome:/usr/share/ubuntu:/usr/share/gnome:/usr/local/share/:/usr/share/
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0

```
Notice the current desktop is Unity.
On an 11.04 system where vncserver works the way I want the only XDG environment variable is
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/

I'm not sure how to specify a non-unity desktop but I think that's what we need.  I may try a KDE session if I can figure out what that is.

I'm still hoping someone has already figured this out and will share the magic incantation that makes it work.

Joe

---

### Post by areeda on 2011-10-25
Well, I got something I can almost use.  It's very kludgey and I describe it here not to recommend it but as more information on what our problem is hoping someone can help clean it up.

I'm convinced the underlying problem is that xstartup is trying to start unity (3D) and the X-server  does not have OpenGL available.

So here's the kludge (remember I'm showing the problem not recommending a solution)

~/.vnc/startup:
```
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
x-session-manager&
```
Start up the vnc server with:

vncserver :1 -geometry 1920x1080 -localhost -fp /usr/share/fonts

My choice of command line options is a topic for another thread, they are not relevant to this discussion.

This gives me an empty desktop with a Nautilus (Places menu) type toolbar but no (working) window manager.  By adding a desktop icon for terminal to my regular desktop, I get that here also.

In a terminal on that (non functional) desktop type:
```
fvwm&
cairo-dock -c &
```
Neither of those programs are part of the installed default packages but both are in the Software Center.

This does give me a desktop, with an application launcher but 

[LIST]
[*]I think I'm running 2 windows managers (gnome from the x-session-manager in xstartup and fvwm)
[*]FVWM is the 1990's Motif wm or at least it looks like it.
[/LIST]
I'm still working on a real solution.  Anyone have a clue how to proceed?

Joe

---

### Post by mathuin on 2011-10-25
Before I moved back to Linux, I used vnc and fvwm on FreeBSD for years.  I would much rather use Gnome, but I'm glad you got this far.

I was able to get that far by erasing .vnc/xstartup, running vncserver to recreate it, then add in a line to start an xterm.

I am convinced that you are right, that there's an assumption that every X display has 3D or something, and that virtual displays are suffering.  I really hope someone comes up with a better answer.  Thank you for the work you did so far!

Jack.

---

### Post by cryptotheslow on 2011-10-25
Have you tried using xfce or maybe fluxbox for the VNC'd X session?

Just an idea as they are both light on effects etc.

I'll have a mess around later on if I get the time.

---

### Post by areeda on 2011-10-25
> **cryptotheslow said:**
> Have you tried using xfce or maybe fluxbox for the VNC'd X session?

Just an idea as they are both light on effects etc.

I'll have a mess around later on if I get the time.I have not begun to search for good 2D window managers.  I'm stuck on getting anything to work well.  

Like Jack, I too have plenty of past experience with fvwm and it's sort of like the old van I keep around.  Very functional but not something I use to impress people.

I don't like the feeling I have 2 window managers running in a session.  I know it's going to bite me, I'm just not sure when or where.

I believe once we figure out how to not start Unity 3D, we can use Unity 2D or gnome like we do in 11.04.

Joe

---

### Post by Toz on 2011-10-25
This worked for me: [http://askubuntu.com/questions/10232/currently-vnc-doesnt-work-with-compiz-will-you-fix-this-before-unity-is-relea]("http://askubuntu.com/questions/10232/currently-vnc-doesnt-work-with-compiz-will-you-fix-this-before-unity-is-relea").

---

### Post by cryptotheslow on 2011-10-25
OK... this is probably no help at all......

Just fired up 11.10 Desktop in a Vbox, installed and ran X11VNC server then connected to it with xtightvncviewer from my desktop and it perfectly happily grabbed my full fat Unity desktop (not Unity 2D).

Maybe I'm just confusing things here (myself mostly) by using a Vbox and grabbing an active session :confused:

---

### Post by emk2203 on 2011-10-26
If somebody else just wants to have a working vnc server, have a look at [this blog (via Ubuntu forums).]("http://mlepicki.com/?p=10")

After being stuck here, I googled again, and finally found [the answer in another thread in the Ubuntu forums.]("http://ubuntuforums.org/showpost.php?p=11379631&postcount=20")

---

### Post by albundy79 on 2011-10-26
I have put many hours, trying different solutions suggested by different forums with no result.

After this huge bug in Ubuntu 11.1 I consider to abandon Ubuntu completely for Windows Server. I will happily pay some cash to save time, headache and frustration over this buggy system.

---

### Post by Toz on 2011-10-26
> **albundy79 said:**
> I have put many hours, trying different solutions suggested by different forums with no result.

After this huge bug in Ubuntu 11.1 I consider to abandon Ubuntu completely for Windows Server. I will happily pay some cash to save time, headache and frustration over this buggy system.

I'm not so sure its a bug. I'm typing this via a vnc session from a Windows XP desktop connected to Xubuntu 11.10. I'm following these instructions: [http://askubuntu.com/questions/10232/currently-vnc-doesnt-work-with-compiz-will-you-fix-this-before-unity-is-relea]("http://askubuntu.com/questions/10232/currently-vnc-doesnt-work-with-compiz-will-you-fix-this-before-unity-is-relea").

In a nutshell:
1. Install x11vnc:
```
sudo apt-get install x11vnc
```

2. Make sure the firewall, if active, has port 5900 open:
```
sudo ufw allow 5900
```

3. Run the vnc server:
```
x11vnc -usepw -forever -noxdamage -geometry 1280x1024 -avahi -nolookup -q
```
...you will be asked for a connection password - enter one. The parameters passed to the x11vnc command are configurable. See here: [http://manpages.ubuntu.com/manpages/oneiric/man1/x11vnc.1.html]("http://manpages.ubuntu.com/manpages/oneiric/man1/x11vnc.1.html").

4. Connect from Windows XP using a vnc client.

***Security note: vnc is an insecure protocol. If you are using this in an unsecured environment, consider tunneling vnc through ssh.

---

### Post by gilesknap on 2011-10-27
The above solutions using x11vnc do work for me, however they do not solve the issue of screen resolution.

I would like to be able to run at the native resolution of my client machine (which has a much larger screen that my server). With x11vnc it only seems possible to scale the native size of the server and this results in a very unsatisfactory experience.

In the past I used to use freenx and this worked perfectly. I have yet to find an equivalent solution that works for Oneiric.

vncserver has the capability to run additional sessions at any resolution but I have not managed to run Unity or gnome over it (same issue as the original post).

---

### Post by albundy79 on 2011-10-27
> **Toz said:**
> I'm not so sure its a bug. I'm typing this via a vnc session from a Windows XP desktop connected to Xubuntu 11.10. I'm following these instructions: [http://askubuntu.com/questions/10232/currently-vnc-doesnt-work-with-compiz-will-you-fix-this-before-unity-is-relea]("http://askubuntu.com/questions/10232/currently-vnc-doesnt-work-with-compiz-will-you-fix-this-before-unity-is-relea").

In a nutshell:
1. Install x11vnc:
```
sudo apt-get install x11vnc
```

2. Make sure the firewall, if active, has port 5900 open:
```
sudo ufw allow 5900
```

3. Run the vnc server:
```
x11vnc -usepw -forever -noxdamage -geometry 1280x1024 -avahi -nolookup -q
```
...you will be asked for a connection password - enter one. The parameters passed to the x11vnc command are configurable. See here: [http://manpages.ubuntu.com/manpages/oneiric/man1/x11vnc.1.html]("http://manpages.ubuntu.com/manpages/oneiric/man1/x11vnc.1.html").

4. Connect from Windows XP using a vnc client.

***Security note: vnc is an insecure protocol. If you are using this in an unsecured environment, consider tunneling vnc through ssh.

[I]
user@ubuntu:~$ x11vnc -usepw -forever -noxdamage -geometry 1280x1024 -avahi -                                                                                                                     nolookup -q
27/10/2011 09:58:23
27/10/2011 09:58:23 *** XOpenDisplay failed. No -display or DISPLAY.
27/10/2011 09:58:23 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
27/10/2011 09:58:23 *** 1 2 3 4
No protocol specified
**27/10/2011 09:58:27 XOpenDisplay(":0") failed.**
27/10/2011 09:58:27 Trying again with XAUTHLOCALHOSTNAME=localhost ...
No protocol specified
27/10/2011 09:58:27 XOpenDisplay(":0") failed.
27/10/2011 09:58:27 Trying again with unset XAUTHLOCALHOSTNAME ...
No protocol specified
27/10/2011 09:58:27

27/10/2011 09:58:27 ***************************************
[B]27/10/2011 09:58:27 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.[/B]
*** There may be "Xlib:" error messages above with details about the failure.

Some tips and guidelines:

** An X server (the one you wish to view) must be running before x11vnc is
   started: x11vnc does not start the X server.  (however, see the -create
   option if that is what you really want).

** You must use -display <disp>, -OR- set and export your $DISPLAY
   environment variable to refer to the display of the desired X server.
 - Usually the display is simply ":0" (in fact x11vnc uses this if you forget
   to specify it), but in some multi-user situations it could be ":1", ":2",
   or even ":137".  Ask your administrator or a guru if you are having
   difficulty determining what your X DISPLAY is.

** Next, you need to have sufficient permissions (Xauthority)
   to connect to the X DISPLAY.   Here are some Tips:

 - Often, you just need to run x11vnc as the user logged into the X session.
   So make sure to be that user when you type x11vnc.
 - Being root is usually not enough because the incorrect MIT-MAGIC-COOKIE
   file may be accessed.  The cookie file contains the secret key that
   allows x11vnc to connect to the desired X DISPLAY.
 - You can explicitly indicate which MIT-MAGIC-COOKIE file should be used
   by the -auth option, e.g.:
       x11vnc -auth /home/someuser/.Xauthority -display :0
       x11vnc -auth /tmp/.gdmzndVlR -display :0
   you must have read permission for the auth file.
   See also '-auth guess' and '-findauth' discussed below.

** If NO ONE is logged into an X session yet, but there is a greeter login
   program like "gdm", "kdm", "xdm", or "dtlogin" running, you will need
   to find and use the raw display manager MIT-MAGIC-COOKIE file.
   Some examples for various display managers:

     gdm:     -auth /var/gdm/:0.Xauth
              -auth /var/lib/gdm/:0.Xauth
     kdm:     -auth /var/lib/kdm/A:0-crWk72
              -auth /var/run/xauth/A:0-crWk72
     xdm:     -auth /var/lib/xdm/authdir/authfiles/A:0-XQvaJk
     dtlogin: -auth /var/dt/A:0-UgaaXa

   Sometimes the command "ps wwwwaux | grep auth" can reveal the file location.

   Starting with x11vnc 0.9.9 you can have it try to guess by using:

              -auth guess

   (see also the x11vnc -findauth option.)

   Only root will have read permission for the file, and so x11vnc must be run
   as root (or copy it).  The random characters in the filenames will of course
   change and the directory the cookie file resides in is system dependent.

See also: [http://www.karlrunge.com/x11vnc/faq.html](http://www.karlrunge.com/x11vnc/faq.html)[/I]

I still get error... The display cannot be found although the physical display works perfectly.

---

### Post by Toz on 2011-10-27
Try running it like this:
```
x11vnc -usepw -forever -noxdamage -geometry 1280x1024 -avahi -nolookup -auth /var/run/lightdm/root/:0.Xauth -q
```
...(change the -geometry as required)

If that doesn't work, post back the results of:
```
ps wwwaux | grep auth
```

---

### Post by albundy79 on 2011-10-27
It seems xauthority is the problem.. I uninstalled compiz unity to get rid off Unity and use the other windowmanagers instead but with no result.

My plan is to backup important files, format the computer and install debian instead of ubuntu.

---

### Post by mathuin on 2011-10-27
> **Toz said:**
> I'm not so sure its a bug.

Here's how to tell if it's a bug.  If something works before an upgrade but not after an upgrade, and there is no documentation or explanation for the change in behavior, it's a bug.

The x11vnc hack does not work for me.  I get spammed with error messages.  It doesn't matter what command line options I try.

tightvncserver worked just fine.  Now none of them work.  It appears that nobody bothered to test for this use case, or if they did, they didn't care that it was broken.  I'd love to know why.

Combining this with the arbitrary disablement of /dev/dsp, I am losing my enchantment with Ubuntu and starting to doubt their commitment to user-friendliness and quality software.

Jack.

---

### Post by mathuin on 2011-10-27
> **emk2203 said:**
> If somebody else just wants to have a working vnc server, have a look at [this blog (via Ubuntu forums).]("http://mlepicki.com/?p=10")

After being stuck here, I googled again, and finally found [the answer in another thread in the Ubuntu forums.]("http://ubuntuforums.org/showpost.php?p=11379631&postcount=20")

This does not work for my use case.

Try this:  Put two systems on a network.  System A is running Ubuntu 11.10 with no monitor or keyboard or mouse, System B is running anything that can run vncviewer.  With nobody logged into System A via the console (X11 or text), can you start up a VNC server (tightvnc, x11vnc, I don't care) running *any* window manager (ideally Gnome, but I'm flexible here) that you can access from System B?  Solve that problem, document that process, and you will make many many friends.  Heck, I'm getting close to sponsoring a small bounty, which is pretty shameful.

Jack.

---

### Post by mathuin on 2011-10-27
Here is a workaround which at least gets me back up and running in a degraded mode, and may help others:  install fvwm and use that.

[LIST=1]
[*]Install fvwm.
```
$ apt-get install fvwm
```
[*]Comment out everything in your .vnc/xstartup and add the following line at the bottom:
```
fvwm &
```
[*]Kill any existing vncserver sessions and start on one your preferred display number.
```
$ vncserver :1
```
[*]Connect to your server from your client.
```
$ vncviewer server:1
```
Enter your password, and prepare to go back in time.
[/LIST]

If you've never used fvwm before, you will be in for an experience.  The bottom right corner has some interesting artifacts:  a grid of nine virtual screens (the V in fvwm stands for virtual), a mailbox (watch what happens when you get mail), an analog clock, and a load meter.  To open an xterm, click the left button on the background, select Terminals, then Xterm.

As I said, this is a degraded mode and the average Ubuntu user will probably be lost without Gnome or Unity, but if you can tough it out old-school, you can still get some things done.

Joe, by replacing the session line you avoid running multiple sessions or window managers, so you should be good to go.  Hopefully sometime soon someone will fix Unity or Gnome, but until then, at least we've got this.

Jack.

---

### Post by albundy79 on 2011-10-27
> **mathuin said:**
> This does not work for my use case.

Try this:  Put two systems on a network.  System A is running Ubuntu 11.10 with no monitor or keyboard or mouse, System B is running anything that can run vncviewer.  With nobody logged into System A via the console (X11 or text), can you start up a VNC server (tightvnc, x11vnc, I don't care) running *any* window manager (ideally Gnome, but I'm flexible here) that you can access from System B?  Solve that problem, document that process, and you will make many many friends.  Heck, I'm getting close to sponsoring a small bounty, which is pretty shameful.

Jack.

Step 1) Backup your files
Step 2) Download any linux distro (debian or fedora) that is not ubuntu
Step 3) Format harddrive
Step 4) Install the new linux distro
Step 5) Setup a VNC-server
Step 6) Login from a VNC client and enjoy!

---

### Post by gilesknap on 2011-10-28
> **Toz said:**
> Try running it like this:
```
x11vnc -usepw -forever -noxdamage -geometry 1280x1024 -avahi -nolookup -auth /var/run/lightdm/root/:0.Xauth -q
```
...(change the -geometry as required)

If that doesn't work, post back the results of:
```
ps wwwaux | grep auth
```

If I start an ssh terminal session to my server and execute the above command, it gives me the same error "XOpenDisplay failed. No -display or DISPLAY." as experienced by albundy79. It Does however work if executed from within the already active GUI session on the server (Useless for those with headless servers).

The following does work for me from an ssh terminal (I ran as root for access to the log file):-

```
x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log -geometry 1920x1200
```

HOWEVER: it is still scaling the screen for a nasty blurry effect. I want a separate session with its own X config - not just a scaled mirror of the physical screen. Freenx used to be the solution for this but I understand it is no longer supported.

---

### Post by gilesknap on 2011-10-28
> **mathuin said:**
> This does not work for my use case.

Try this:  Put two systems on a network.  System A is running Ubuntu 11.10 with no monitor or keyboard or mouse, System B is running anything that can run vncviewer.  With nobody logged into System A via the console (X11 or text), can you start up a VNC server (tightvnc, x11vnc, I don't care) running *any* window manager (ideally Gnome, but I'm flexible here) that you can access from System B?  Solve that problem, document that process, and you will make many many friends.  Heck, I'm getting close to sponsoring a small bounty, which is pretty shameful.

Jack.

The quoted solution above worked perfectly for me. What errors did you get?

---

### Post by Toz on 2011-10-28
Have a look at: [http://mlepicki.com/?p=10]("http://mlepicki.com/?p=10") for a suggestion on how to start x11vnc on system startup to avoid the X error. Also: [http://ubuntuforums.org/showthread.php?t=1860295&highlight=x11vnc.conf]("http://ubuntuforums.org/showthread.php?t=1860295&highlight=x11vnc.conf").

As for the blurrines, have a look at the -scale parameter: [http://manpages.ubuntu.com/manpages/oneiric/man1/x11vnc.1.html]("http://manpages.ubuntu.com/manpages/oneiric/man1/x11vnc.1.html"). Perhaps a better value specified there can eliminate the blurriness.

---

### Post by mathuin on 2011-10-28
> **gilesknap said:**
> The quoted solution above worked perfectly for me. What errors did you get?

Most of the errors I got were related to :0 and some were related to authority issues.  Running with sudo is not acceptable, so I can't get past the nonsense authority issues, and x11vnc doesn't like localhost:11.0 anyway.

The user-mode workaround I posted doesn't require sudo and works on remote X displays just like vncserver used to work.  If I'm stuck with fvwm instead of gnome, I'll just have to dig out my old-school customized .fvwm2rc and think about "progress".

Jack.

---

### Post by Tristan Schmelcher on 2011-11-13
> **mathuin said:**
> When I attempt to do this after upgrading to oneiric, instead of seeing a familiar GUI, I see something that looks as if I opened a file manager like Nautilus.  The background looks good, but the top bar is grey with black writing:  File Edit View Go Bookmarks Help.  Deleting my entire ~/.vnc directory and starting over does not help.

FYI, I encountered the same thing and opened [https://bugs.launchpad.net/bugs/889996](https://bugs.launchpad.net/bugs/889996) for it. Basically the way that Unity detects 3D support is broken in this situation, so it incorrectly tries to use Unity 3D instead of Unity 2D. I described a work-around in the bug report.

If you still experience the problem, it would be helpful if you could mark the bug as affecting you too so that it gets attention from the developers sooner.

---

### Post by mathuin on 2011-11-14
> **Tristan Schmelcher said:**
> FYI, I encountered the same thing and opened [https://bugs.launchpad.net/bugs/889996](https://bugs.launchpad.net/bugs/889996) for it. Basically the way that Unity detects 3D support is broken in this situation, so it incorrectly tries to use Unity 3D instead of Unity 2D. I described a work-around in the bug report.

If you still experience the problem, it would be helpful if you could mark the bug as affecting you too so that it gets attention from the developers sooner.

Thank you!  I should have done this, but I guess I was too butt-hurt and cranky.  I appreciate your mature response to this horrible situation, and have indeed marked the bug as affecting me as well. :-)

Jack.
(is there any way to include bug numbers in forum title lines?)

---

### Post by Tristan Schmelcher on 2011-11-14
> **mathuin said:**
> (is there any way to include bug numbers in forum title lines?)

So that it creates a link, you mean? Don't think that's possible.

---

### Post by TiberiusT on 2011-12-01
[COLOR=#000000][FONT=Calibri]Well...this is fun (VNC in 11.10)....[/FONT][/COLOR]

[COLOR=#000000][FONT=Calibri]Not really having a clue abt what Tristan is on about I tried:[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]**sudo**[/FONT][/COLOR][COLOR=#000000][FONT=Calibri]***ln -s /usr/lib/nux/unity_support_test  /bin/false***[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]but  it erred with ‘already exists’. There was no change in behaviour - I  still can’t get a working window manager from a vnc client. Did I do it  right?[/FONT][/COLOR]

[COLOR=#000000][FONT=Calibri]I  also marked that bug and kudos to Tristan for such an excellent bug  report - he’s even delved into the code and pinpointed the error. Not  much chance of a fix for 11.10 it seems. I see it’s been assigned for  Precise though. [/FONT][/COLOR]

[COLOR=#000000][FONT=Calibri]I  ended up in Mathuin land with the venerable fvwm - a trip down memory  lane and mildly entertaining. For a bit. I have tried running  Ubuntu Classic/no effects on the server but the result is the same - no problem VNCing  in, but can’t really do anything when I arrive. So, I tried XRDP , but I see now that this uses VNC4server as a  type of slave host (?) so same problem - and I sit there staring at the  blank server’s desktop background. The X11vnc solution does actually  work, but the -noxdamage switch apparently means that it redraws the  entire screen each time and is therefore slow and extremely tedious when  trying to do proper maintenance work on the server and no good for simultaneous users on different Xscreens.[/FONT][/COLOR]

[COLOR=#000000][FONT=Calibri]Enuf verbosity. My question is:[/FONT][/COLOR]

[COLOR=#000000][FONT=Calibri]What  do I need to do to the server to get VNC back again? It’s an HTPC server, I  don’t care what it looks like, but I need a basic window manager. It runs XBMC with VDPAU and it was fine with 10.04. Can I ditch  Unity/LightDM completely in 11.10? Can I sidegrade to Kubuntu or even  xfce ? I really don’t want to re-install but will do so if abs  necessary to get VNC back...

Tks in advance
T

[/FONT][/COLOR]

---

### Post by Tristan Schmelcher on 2011-12-01
The simplest thing to do is to just manually select "Ubuntu 2D" in the session dropdown (the gear on the login screen) when connecting via VNC. That's what I'm doing.

---

### Post by TiberiusT on 2011-12-02
@Tristan

Tks a lot for yr reply and yr efforts to resolve this really annoying glitch. 

So, I just have to use XDMCP which enables a login screen when VNCing in, and then I can choose 2D from the gear box? That will be a good enough solution - I'll get on it this weekend.

BTW, anyone who has got this far in this thread is almost certainly affected by the bug, but I see that only 4 people have marked themselves as being affected. The more that mark it, the more chance of it getting fixed quickly I guess...so get clicking if you're affected.

Cheers
T

---

### Post by TiberiusT on 2011-12-05
[FONT=Verdana]@Tristan. Thanks again - that worked in both LightDM and GDM :D:D . I've fallen back to GDM desktop manager and Gnome Classic window manager since I don't need any fancy interface on an HTPC server.  

Case anyone's interested I did this: [/FONT][FONT=Verdana]

[/FONT] [FONT=Verdana][COLOR=#000000]I created the file "custom.conf" under /etc/gdm/ with the following contents:[/COLOR][/FONT][FONT=Verdana]
 [/FONT]```
[daemon]
RemoteGreeter=/usr/lib/gdm/gdmlogin

[xdmcp]
Enable=true
```[FONT=Verdana]I then created another file called "service" in [/FONT][FONT=Verdana][COLOR=#000000]/etc/xinetd.d:[/COLOR][/FONT]```
[FONT=Verdana][COLOR=#000000]service Xvnc[/COLOR][/FONT][FONT=Verdana]
{
type = UNLISTED
disable = no
socket_type = stream
protocol = tcp
wait = no
user = root
server = /usr/bin/Xvnc
server_args = -inetd -query 127.0.0.1 -once -geometry 1200x800 -depth 16 -securitytypes=none -DisconnectClients=0 -NeverShared
port = 5901
}[/FONT]
```[FONT=Verdana]Reboot and then login using a vncviewer. I use Remmina bcos it has a great sticky scaler that u can use to set window sizes on different clients. I have static IP on the server so for me the host/server address is: 192.168.1.60:5901 and I get the GDM login screen on the server and a fully useable Gnome Classic desktop. I'll start optimising the settings soon but I'm so damn relieved to have it working I'm kinda reticent to tinker with it;) People might wanna check out the security issues with XDMCP as per this [/FONT][https://wiki.ubuntu.com/xdmcp](https://wiki.ubuntu.com/xdmcp)[FONT=Verdana]
[/FONT][FONT=Verdana]
and for ref here's the serve[/FONT][FONT=Verdana]r's  [COLOR=#000000]~/.vnc/xstartup[/COLOR]```
[COLOR=#000000]#!/bin/sh[/COLOR]
[COLOR=#000000]# Uncomment the following two lines for normal desktop:[/COLOR]
[COLOR=#000000]unset SESSION_MANAGER[/COLOR]

[COLOR=#000000]exec /etc/X11/xinit/xinitrc[/COLOR]
[COLOR=#000000]gnome-session[/COLOR]
[COLOR=#000000]#[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup[/COLOR]
[COLOR=#000000]#[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources[/COLOR]
[COLOR=#000000]#xsetroot -solid grey[/COLOR]
[COLOR=#000000]#vncconfig -iconic &[/COLOR]
[COLOR=#000000]#xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &[/COLOR]
[COLOR=#000000]#twm &[/COLOR]
```[/FONT][FONT=Verdana][COLOR=#000000]

sorted....finally.

T

[/COLOR][/FONT]

---

