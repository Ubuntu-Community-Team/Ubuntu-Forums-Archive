---
title: "gnome hang? unsure what this is"
date: 2009-08-06
forum: General Help
---

### Post by Fatman_UK on 2009-08-06
I was dragging launchers between nautilus-desktop, gnome-panel and gnome-do (Docky mode) when I got the error "Drag and drop is not supported. An invalid drag type was used."

I can still move the mouse pointer so it doesn't seem to be a kernel panic. I can press "caps lock" and see the "caps lock" light come on, so basic I/O is still there.

The system isn't hung exactly, but nautilus-desktop and gnome-panel are not responding at all to left, right and middle clicks. Neither is gnome-do responding to clicks but it still does the "dock zoom" whenever I mouse over it. Guake is not responding to the "drop down" key (which I have set as F1).

The error dialog is still on the screen. I can't get rid of it. I can't click the "&OK" button, pressing Alt-O doesn't work either. The mouse pointer is stuck in "drag" mode.

I'm left with my usual trick of Ctrl-Alt-F1 and log into the console. It takes forever but eventually logs in. I see nothing unusual in "top" or "ps".

I would like to recover the session and continue working. I suspect either "shutdown -r now" or failing that the magic SysRq sequence will work for rebooting. Suggestions anyone?

---

### Post by depaulmatthew on 2009-08-30
I got the same problem. No idea how to fix it. please help.

---

### Post by bedhead75 on 2009-09-21
I've experienced the same problem many times, and it's reproducible...exactly what you said.  Does anyone know how to fix this without having to alt-Ctrl-backspace to restart X?

---

### Post by AsoSako on 2009-09-23
I too have this problem.  I would love a solution please!

---

### Post by bertmanphx on 2009-09-23
Interesting.  I've just had this happen too.  I managed to Alt-F2 and get gnome-system-monitor running.  Then I killed gnome-settings-daemon and everything started working again.  But of course, my theme was incorrect....

bertmanphx

---

### Post by bedhead75 on 2009-09-23
Could you be a bit more specific in exactly how you got gnome-system-monitor running?  Pressing alt-F2 on my system doesn't do anything, but ctrl-alt-F2 exits to the terminal.  I'd like to be able to get out of this problem without having to restart X and risk losing unsaved data.

---

### Post by AsoSako on 2009-09-24
> **bertmanphx said:**
> Interesting.  I've just had this happen too.  I managed to Alt-F2 and get gnome-system-monitor running.  Then I killed gnome-settings-daemon and everything started working again.  But of course, my theme was incorrect....
bertmanphx
That is very interesting bertmanpx so maybe it's the gnome-settings-daemon that does the problem...

> **bedhead75 said:**
> Could you be a bit more specific in exactly how you got gnome-system-monitor running? Pressing alt-F2 on my system doesn't do anything, but ctrl-alt-F2 exits to the terminal. I'd like to be able to get out of this problem without having to restart X and risk losing unsaved data.
I too can barely every if not at all get alt-F2 to work when gnome hangs.  I think it worked like once...  Anyways I set up a hotkey for the gnome-system-monitor and it seems to work.... but this is only a temporary solution

Well definitely need a more permanent solution to this issue...
When it happens to me both bottom and top panel seem to freeze, as well as my desktop like the original poster said...  It seems somewhat random, but it has happened more often right after logon, and it seems to occur when I open a random application...  Nothing set that I have noticed.  The only thing that seems to still work is the place on the top right on the bar where I see my name and I get the options to shutdown/restart and all of those things...
As I said before I would love a solution to all of this.

---

### Post by AsoSako on 2009-09-24
killall gnome-panel also seems to work as a temporary solution.  I have it set up on a hotkey.

---

### Post by bertmanphx on 2009-09-24
Hello,
Well, I have also done a crl-alt-F2, dropped to terminal, then hit ctrl-alt-F7 and all was ok.

also I turned off all effects (compiz), and didn't have the problem.

bertmanphx

---

### Post by AsoSako on 2009-09-25
Alright.  I got the hang again and I tryed killing gnome-settings-daemon however that did not fix it for me.  It seems that only killall gnome-panel works.  Or restarting the X server with ctrl-alt-backspace

---

### Post by bedhead75 on 2009-09-25
Yea...I just tested it again by reproducing the bug.  I have my gnome-do docky set to autohide, and when this error happens, the gnome-do dock hides itself even though the mouse pointer and dragged icon aren't even near the dock.  Opening a terminal and then "killall gnome-panel" functions to close the dialog box and returns functionality of the mouse pointer.  At least there's a way to recover without restarting X and potentially losing data.
     I've filed a bug on Launchpad with gnome-do the other day, but I'm thinking maybe it has nothing to do with that?  Any other suggestions?  With gnome perhaps or compiz?

---

### Post by AsoSako on 2009-09-25
Let me know if you discover something else.  As far as I have noticed it seems to happen at times when I open files with a text editor...  It is kind of odd, and I may be wrong.

---

### Post by bedhead75 on 2009-09-25
Reproducing this bug actually begins with an apparent bug in gnome-do when removing launchers from docky.

1. I notice that sometimes dragging a launcher off of docky and releasing it onto the desktop in order to remove it from docky, doesn't work the first time around. The icon reappears in docky, and the animation in which the icon vanishes in a "puff of smoke" doesn't happen. Sometimes I have to add and re-add different icons a few times in order to get this bug to happen, but it happens soon enough.

2. When step 1 does happen, it takes a second drag of the same launcher onto the desktop in order to remove it from docky in a "puff of smoke".

3 Regardless of whether you did step 2 or not, as long as step 1 has occurred, dragging any icon from the gnome menu (doesn't have to be the icon from step 1) causes this error window to appear.

For me, I can only return functionality with "killall gnome-panel". Running "killall nautilus" in a terminal doesn't work. This error still happens when I turn Intellihide off. After recovering from this error using "killall gnome-panel", after a few minutes gnome-do crashes and closes unexpectedly with the following message in the terminal, when gnome-do was run from the terminal.

The program 'Do' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 12909 error_code 9 request_code 14 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


I've filed this bug in launchpad with gnome-do.

---

### Post by AsoSako on 2009-09-27
Alright.  I have a potential fix.  At least this did it for me and it seems to work for now at least...  
I had some bookmarks in gnome which led me to some private VPN servers.  I removed them and the gnome-panel and everything else seems to work pretty fast and smooth now without hanging.  If you have any such bookmarks you may want to remove them.  I will post again if the bug occurs again, but it seems fixed and stable for now.

---

### Post by johnbrondum on 2009-11-21
I've had the same problem - I did a fresh install of Ubuntu 9.10 and noted that the problem didn't seem to appear, until this morning after I installed the Global Menu program [http://code.google.com/p/gnome2-globalmenu/](http://code.google.com/p/gnome2-globalmenu/)

I removed it again and haven't had a problem with Gnome-do since.... but no idea why or if it is just coincidence.... 

:-/

---

### Post by johnbrondum on 2009-11-21
btw - I also removed the program compile dependencies as well...

---

### Post by mayankbhagya on 2010-04-15
Isn't the actual cause/solution for the problem known yet...
I am facing the same problem.
But it started only after I installed gnome-do.

---

