---
title: "keymapping for joystick"
date: 2012-06-08
forum: General Help
---

### Post by Kymus on 2012-06-08
I'm looking for a program that will keymap my Logitech Cordless Rumblepad 2. I know about QJoyPad, but that is unresponsive on my system (it'll open and close and that's it. All other commands are ignored it seems). 

I've tried rejoystick, but long story short, that was unsuccessful as well.

I was able to install jscalibrator, but when I run it, all I see is a screen to calibrate the analog control sticks. I can't seem to figure out how to assign a key for specific buttons.

Lastly I know there's jstest-gtk, but I can't figure out how to even download it ](*,)

I also have a Gravis Gamepad Pro, if that is going to make my life any bit easier.

---

### Post by archeryguru2000 on 2012-06-08
It has been a while (at least 3 years ago) since I've last used this, but I had good results from [[COLOR="Blue"]_joy2key_[/COLOR]]("http://www-en.jtksoft.net/").  I have a Pelican AfterGlo Pro Controller (for PS3), and it worked just fine.  I simply mapped the keys I needed for the 'keyboard' game and went on from there.

I've never used QJoyPad, or the others that you've mentioned, but try joy2key and let us know if you have any success (or problems).

EDIT======================
Arrgg! I just checked their web-site.  They do not have a *nix version to download.  I must have used wine (or something) to utilize this application.  However, here's a couple of links that have some helpful information.
Link 1: [_[COLOR="Blue"]Ubuntuforums[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=903858")

Link 2: [[COLOR="blue"]_Techzoku_[/COLOR]]("http://techzoku.blogspot.com/2009/06/gamepads-in-ubuntu-linux.html") (which gives a bit of info for Qjoypad)

~~archery~~

---

### Post by Kymus on 2012-06-08
Hey Archery, thanks for the reply.

I tried joy2key shortly after posting this. It will run on my PC but after assigning keys, it doesn't seem to do anything (unless I need to *save* something?). On my HTPC (which is the bigger issue here), it won't run at all. I executed the file and I'll get the busy icon for a bit and then... nothing. To the best of my knowledge, wine is up to date and I made sure that it was trying to execute the file with wine and that the permission was set to run it as a program. 

In regards to link #1, It's rather intimidating for me, since that's beyond my expertise. >_<

Link #2 may be helpful. I've already followed those directions for jscalibrator (I followed [this guide here]("http://askubuntu.com/questions/32031/how-do-i-configure-a-joystick-or-gamepad"), which seems to be a copy and paste of the same directions you will find everywhere). 

The input on QJoypad may be helpful.. Unfortunately, the link provided for the deb file is no good, but I may be able to try installing it a different way and following the rest of the instructions. I will report back

Thanks :)

---

### Post by Kymus on 2012-06-08
I uninstalled qjoypad, then installed it via the terminal. It said I was missing a dependency and I needed QT4. 

[This]("http://install-climber.blogspot.com/2011/06/installing-complete-qt-4-environment-on.html") page said to do this:

> sudo apt-get install libqt4-assistant libqt4-core \
libqt4-dbg libqt4-dbus libqt4-designer libqt4-dev libqt4-gui \
libqt4-help libqt4-network libqt4-opengl libqt4-sql \
libqt4-sql-mysql libqt4-sql-odbc libqt4-sql-psql \
libqt4-sql-sqlite2 libqt4-svg libqt4-test libqt4-sql-sqlite \
libqt4-webkit libqt4-webkit-dbg libqt4-xml libqt4-xmlpatterns\
libqt4-xmlpatterns-dbg libqtcore4 libqtgui4 \
qt4-demos qt4-designer qt4-dev-tools qt4-doc qt4-doc-html \
qt4-qtconfig qtcreator


But then I got this error:

> E: Unable to locate package libqt4-sql-sqlite2
E: Unable to locate package libqt4-xmlpatternslibqt4-xmlpatterns-dbg


So, I just left those two out..... and ran along with things.

It's installed and everything, but I still have the same odd problem as before: it doesn't respond to my commands. It will detect the presence of a joystick and it will open the menu, but the only button that seems to respond, is quit.

---

### Post by Kymus on 2012-06-10
Bump

---

### Post by archeryguru2000 on 2012-06-11
As for the errors:

```

E: Unable to locate package libqt4-sql-sqlite2
E: Unable to locate package libqt4-xmlpatternslibqt4-xmlpatterns-dbg

```

You instead need;

```

#: apt-get install libqt4-xmlpatterns libqt4-xmlpatterns-dbg

```

Notice the space between the two libraries.  These are two separate items.  However, I'm not sure why libqt4-sql-sqlite2 is _*not found*_.  On my machine (Ub 11.04) I get the following:

```

$: apt-cache search libqt4-sql-sqlite2
libqt4-sql-sqlite2 - Qt 4 SQLite 2 database driver

```

Maybe try installing that library through synaptic instead?

~~archery~~

---

### Post by archeryguru2000 on 2012-06-11
By the way, I seem to remember having some issues with getting some wine utilities to grab the usb properly.  I assume you have your joystick connected by usb?  I wonder if you need to change some permissions to/from su/you?

I'll do a bit more digging around and see what I come up with.

~~archery~~

---

### Post by Kymus on 2012-06-11
Thanks for the tip, Archery!

As far as I know (and I could be completely wrong or mistaken), the joystick is being recognized, it's just an issue of either (A) these programs deciding not to run (either at all, or just properly), or (B) no response after keys are programmed (though so far this is much less the issue).

Right now, I'm fiddling with Wine (just updated to 1.5, though I am missing PPA's for 1.3 and winetricks, which keeps me from updating them in the update manager) and I also found out that the version of Key2Joy I downloaded and tried previously was outdated version (3.X, current version is 5.X). I realized that I wasn't at the official site, so I decided to google and figured out that I was using an outdated version.

I'm gonna try Key2Joy first on my PC (much easier to fiddle with) then my HTPC (main target here). I'll try it with my Gravis Gamepad Pro first, since it should ideally be plug-and-play (though technically, the Logitech controller should be too, but I figure that there's always the possibility of some sort of hiccup since it's wireless).

ADDENDUM: My PC is running 11.10 and the HTPC is running 12.04, FWIW. I'm just too lazy to update on the PC for now :P

---

### Post by archeryguru2000 on 2012-06-11
You mentioned in your original post jstest-gtk.  The base package jstest is in the ub-repos (under: joystick).  If you install joystick, you can run jstest (from cli) and see if your gamepad is operating as it should.  This may also give us some help (running cli) in deciphering any errors that you may encounter.

Here's a [[COLOR="Blue"]_man page for joystick_[/COLOR]]("http://www.x.org/archive/X11R7.5/doc/man/man4/joystick.4.html").

~~archery~~

---

### Post by Grumbel on 2012-06-13
First of, make sure that your joystick is detected properly and working. You can do so from command line with:

 jstest /dev/input/js0

If that responds properly, you should be able to use QJoypad or rejoypad. As QJoypad or rejoypad does exactly what you want, you should further investigate why they don't work. 

As for QJoypad, I can confirm that it doesn't seem to work properly. It gets put into the systray, but none of the menu commands do anything. Running it with:

$ qjoypad --notray

however seems to work.


rejoystick brings up a window for me, but once I hit "Ok" it kills itself with error message:


$ rejoystick 
No file to load, creating
XIO:  fatal IO error 0 (Success) on X server "&#65533;Wt	"
      after 94 requests (94 known processed) with 0 events remaining.

$ sudo /usr/games/rejoystick 
** (rejoystick:19509): WARNING **: Could not connect: Connection refused

Further notes:

joy2key will not work for Linux applications, it's a Windows tool and thus will only work within the Wine sandbox, if at all.

Neither jstest-gtk or jscalibrator allow you to remap buttons, so you can forget those tools.

Ignore the manpage that archeryguru2000 posted, that's just for obscure Xorg joystick handling that nobody uses.

---

### Post by Kymus on 2012-06-14
Thanks for the help, Grumbel.

Running** $*** qjoypad --notray* works for me as well, but it seems like the D-pad and the analog controls don't respond. It's fine with key presses for all the other buttons though, and running jstest, it recognizes my controller by name just fine.

**update:** So far so good with the Gravis Gamepad Pro (well, the d-pad works, but there are no analog controls). I'll try again later with the Logitech controller

**update2:** Not sure what I did wrong before, but I've got everything working fine now. Thank you for your help, guys!

---

### Post by archeryguru2000 on 2012-06-18
Glad to see you're up and running now.  I don't believe I've ever used Qjoypad before.  But I will try to remember the '--notray' option for future reference.

Thanks for jumping in and adding some of your expertise Grumbel.

~~archery~~

---

