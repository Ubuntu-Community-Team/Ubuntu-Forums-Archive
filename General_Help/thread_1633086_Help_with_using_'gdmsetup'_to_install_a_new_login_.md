---
title: "Help with using 'gdmsetup' to install a new login screen."
date: 2010-11-28
forum: General Help
---

### Post by David802 on 2010-11-28
Hey guys, I downloaded the "BlueSwirl" login screen theme from 

[http://art.gnome.org/themes/gdm_greeter](http://art.gnome.org/themes/gdm_greeter)

After extracting the tar ball I read the install and readme files files. The readme was useless but the install file said to use 'gdmsetup' to install. 

so I pulled up a terminal window and ran 'gdmsetup' and this is what came out.

> david@davids-laptop:~/devel/BlueSwirl$ gdmsetup
** (gdmsetup:2747): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): Key not found
** (gdmsetup:2747): WARNING **: Error calling GetValue('daemon/TimedLoginDelay'): Key not found
** (gdmsetup:2747): DEBUG: init delay=30
** (gdmsetup:2747): DEBUG: "/usr/share/xsessions/guest-restricted.desktop" is hidden or contains non-executable TryExec program
** (gdmsetup:2747): DEBUG: "/usr/share/xsessions/une-guest-restricted.desktop" is hidden or contains non-executable TryExec program
** (gdmsetup:2747): DEBUG: "/usr/share/xsessions/une-efl-guest-restricted.desktop" is hidden or contains non-executable TryExec program


** (gdmsetup:2747): WARNING **: Error calling GetValue('daemon/DefaultSession'): Key not found
** (gdmsetup:2747): DEBUG: Init default session found:'(null)'
** (gdmsetup:2747): DEBUG: GdmUserManager: Found current seat: /org/freedesktop/ConsoleKit/Seat1
** (gdmsetup:2747): DEBUG: GdmUserManager: running 'ck-history --frequent --seat='Seat1' --session-type='''
** (gdmsetup:2747): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:2747): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:2747): DEBUG: adding monitor for '/home/david/.face'
** (gdmsetup:2747): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:2747): DEBUG: Found 1 sessions for user david
** (gdmsetup:2747): DEBUG: GdmUser: adding session /org/freedesktop/ConsoleKit/Session2
** (gdmsetup:2747): DEBUG: GdmUserManager: sessions changed user=david num=1
** (gdmsetup:2747): DEBUG: GdmUserManager: added session for user: david
** (gdmsetup:2747): DEBUG: GdmUserManager: history output: david    429
** (gdmsetup:2747): DEBUG: GdmUserManager: history output: gdm      21
** (gdmsetup:2747): DEBUG: GdmUserManager: excluding user 'gdm'
** (gdmsetup:2747): WARNING **: Error calling GetValue('daemon/AutomaticLoginEnable'): Key not found
** (gdmsetup:2747): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): Key not found
** (gdmsetup:2747): WARNING **: Error calling GetValue('daemon/TimedLogin'): Key not found
** (gdmsetup:2747): DEBUG: init user='(null)' auto=False


It stops there and brings up the login screen settings window (which I then unlock instead of using sudo in terminal), but theres no where for me to tell it to install the theme I downloaded nor anyway to even continue...

Below is a list of files that came out of the tarball.

> david@davids-laptop:~/devel/BlueSwirl$ ls
background.jpeg  GdmGreeterTheme.desktop  README          shade-right.png
blueswirl.xml    gnome-linux-desktop.png  screenshot.jpg  small-n.png
dotline.png      INSTALL                  shade-left.png  vline.svg


So my question... Where do I go from there?

Thanks for the help! 

David

---

### Post by David802 on 2010-11-28
This can be deleted I figured it out.

---

### Post by cantru on 2011-04-05
Could you share your knowledge? I'm stuck.

Thanks.

---

### Post by jdgregson on 2011-09-03
Yes, could you share your knowledge? I am also having the same problem with the same theme. When a problem is solved, you don't remove any evidence that you ever had the problem, but rather, you explain the solution, so that others in the future can find it with Google, and also solve their problem, without having to start a whole new thread.

---

