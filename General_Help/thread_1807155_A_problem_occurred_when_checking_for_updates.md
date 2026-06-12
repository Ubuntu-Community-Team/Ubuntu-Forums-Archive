---
title: "A problem occurred when checking for updates"
date: 2011-07-18
forum: General Help
---

### Post by jepkratz on 2011-07-18
I'm a total Ubuntu Linux newb, apologies in advance! I'm using 10.04 Lucid LTS.

I boot up this AM, and the normal fast boot is off, and the ubuntu purple screen says there's been an error, and offers to let me manually fix, or for it to fix itself (sorry, not exact wording). I finally get to my desktop, and I see a red ball with a horizontal white line across it in the top menu bar. I hover my pointer over the symbol and it says "A problem occurred when checking for updates".

So I go System - Administration - Update Manager, and the pointer wheel spins, and then nothing, the update window doesn't open. Same thing happens for Ubuntu Software Center, and Software Sources.

It will let me open the Synaptic Package Manager, but I can't seem to get anywhere with that.

Much appreciation for any help.:confused:

---

### Post by garvinrick4 on 2011-07-18
ctrl/alt/F1
login
```
sudo apt-get update
```
If no errors:
```
sudo apt-get upgrade
```
ctrl/alt/F7
above gets back to GUI

---

### Post by jepkratz on 2011-07-18
Thanks - did the ctrl-alt-F1, started the log-in - it let me type my username (same as for ubuntu boot log-in I'm assuming), I hit enter, and it asks for password, when I start to type, no characters/dots appear. The cursor just keeps blinking. It then times out at sixty seconds and queries for the user id again. 

I entered my password , and pressed enter, but it said login error, and requested my log-in id again on a new line.

ctrl alt F7 did get me back to the GUI.

---

### Post by jepkratz on 2011-07-18
I have gone back several times. The interface is just not recognizing that I am typing my password - the cursor just blinks just past the colon. What's strange is that is lets me type in my log-in i.d, but not my password. :confused:

Am I correct that I should be using the same log-in id and password as when I boot up in th GUI?

---

### Post by garvinrick4 on 2011-07-18
> I have gone back several times. The interface is just not recognizing  that I am typing my password - the cursor just blinks just past the  colon. What's strange is that is lets me type in my log-in i.d, but not  my password. :confused:
It will not move the cursor when typing password. And yes it is the same password you used
when you installed the system.

---

### Post by jepkratz on 2011-07-18
Thanks garvinrick4 - okay, I was finally able to log-in and password in the terminal - I entered sudo apt-get update and it listed out a bunch of stuff, but I didn't see any error codes, and per your instructions then entered sudo apt-get upgrade and it scrolled off a shorter list including "building new tree" , but still no error codes, so I ctrl alt F7 back, and the red dot with white horizontal line is still there up in the menu bar. Still cant open update manager, ubuntu software, or software sources.

I thought maybe it needed a re-boot - so I did, and all the problems mentioned are still here.

Much appreciation for your efforts - any further suggestions?:confused:

---

### Post by cipherboy_loc on 2011-07-18
Red dot with a white line? Could you take a screen shot? Also, what happens with the following command:

```

gksudo gnome-terminal

```

Does it open up the password prompt, or does it just sit and spin?


Cipherboy

---

### Post by garvinrick4 on 2011-07-18
```
sudo dpkg --configure -a
```Above will fix broken packages.
If all is OK you will get no response from code.

Did you have any updates to do when did update and upgrade?

---

### Post by jepkratz on 2011-07-19
> **cipherboy_loc said:**
> Red dot with a white line? Could you take a screen shot? Also, what happens with the following command:

```

gksudo gnome-terminal

```Does it open up the password prompt, or does it just sit and spin?


Cipherboy

I wish I knew how to take a screenshot.

It's a red circle, about the same diameter as the blue ? help button, and it has a white horizontal bar bisecting it. It is located in right middle of the top menu bar next to the up/down arrows for the network connection. 

When I hover the mouse pointer over it a dialog box pops up "A problem occurred when checking for updates" When I right click on it, a pull down sub-menu opens with Show updates, Install updates, Check for updates, Start package manager, Show notifications (which has a "check" in front of it), and Preferences. Only the package manager works (opens the Synaptic Pagage Manager program).

When I click on the "Install all updates" in the pull down sub-menu it does ask for my password, but then nothing happens.

I entered from the terminal ( gksudo gnome-terminal ) and the reply was:
(gksudo:1689) Gtk - WARNING **: cannot open display

Thank you for your help.

---

### Post by jepkratz on 2011-07-19
> **garvinrick4 said:**
> ```
sudo dpkg --configure -a
```Above will fix broken packages.
If all is OK you will get no response from code.

Did you have any updates to do when did update and upgrade?

I entered ( sudo dpkg --configure -a ) into the terminal it asked for my password, then a new query line. I entered the command again, and this time it just started a new query line.

The Synaptic package manager has a selection for "broken" I select it and click reload it has a window pop up, says it has downloaded 50 of 50 files, and then just goes away. Nothing appears in the "programs" window.

Thanks again for your help. Is this completely strange, or something that has been seen before?

edit: there was a big update last week that I installed when prompted by the update manager. I do not know if it was doing the background auto-searching for updates when the problem started today. I do not believe there were any updates pending install.

---

### Post by cipherboy_loc on 2011-07-19
A quick google showed this link ([http://ubuntuforums.org/showthread.php?t=1703705](http://ubuntuforums.org/showthread.php?t=1703705)). Look through your /etc/apt/sources.list and make sure you only have lines like:

```

deb http://example.com distro group
deb-src http://example.com distro group

```That might be the cause of your issues (if you have line that isn't properly formatted). Rather than deleting it, you can just put a # in front of it to comment it out.  

EDIT:

As for the terminal, it doesn't look like thats the issue (now that I know what the red-circle-with-line-through-it icon means).

Cipherboy

---

### Post by jepkratz on 2011-07-19
> **cipherboy_loc said:**
> A quick google showed this link ([http://ubuntuforums.org/showthread.php?t=1703705](http://ubuntuforums.org/showthread.php?t=1703705)). Look through your /etc/apt/sources.list and make sure you only have lines like:

```

deb http://example.com distro group
deb-src http://example.com distro group

```That might be the cause of your issues (if you have line that isn't properly formatted). Rather than deleting it, you can just put a # in front of it to comment it out.  

EDIT:

As for the terminal, it doesn't look like thats the issue (now that I know what the red-circle-with-line-through-it icon means).

Cipherboy

Thanks Cipherboy,
I clicked on the link provided - it does appear to be a similar problem (same icon) - with some differences. Does their Maverick vs my Lucid version make a difference with this problem?

I'm not seeing the exact same error codes - and it appears that other fellow is still able to open the Software Center, I'm not able to open Software Center, Software Sources, or Update Manager, only the Synaptic Pkg Mngr, and the Terminal (and of course my Firefox browser - and my file manager)

In my first post I did apologize, and do so again for being a total ubuntu/linux newb. I went to the terminal and after log-in entered code: " gksu gedit /etc/apt/sources.list " reply was
" (gksu:1973): Gtk-WARNING **: cannot open display:

---

### Post by cipherboy_loc on 2011-07-20
For your last issue of editing the sources, use the following command(s):

```

export DISPLAY=":0.0"
gksu gedit /etc/apt/sources.list

```


What all the programs that **cannot** run, with the exception of Software Sources, have in common is that they use an "internal" root authentication, rather than using gksu and launching the application as root. Do you mind posting the error codes again?



Cipherboy

---

### Post by jepkratz on 2011-07-20
> **cipherboy_loc said:**
> For your last issue of editing the sources, use the following command(s):

```

export DISPLAY=":0.0"
gksu gedit /etc/apt/sources.list

```
What all the programs that **cannot** run, with the exception of Software Sources, have in common is that they use an "internal" root authentication, rather than using gksu and launching the application as root. Do you mind posting the error codes again?



Cipherboy

Okay, I logged into terminal, and a number of messages (?) popped up, it is quite a bit, and some may shed light on the problem. Is there a way to copy and paste from the terminal (just hoping - it's a lot (about one screen's worth) to write, re-type, and get it right)?

On the assumption the export display command is just that, at the prompt I entered;
export DISPLAY=":0.0" (then hit enter for 2nd line)
gksu gedit /etc/apt/sources.list

Response;
Error copying '/home/jepkratz/.Xauthority' to '/tmp/libgksu-PaAwgW'; No such file or directory

On returning to the GUI, a small window popped up with the red dot/white line icon with text: Failed to run gedit '/etc/apt/sources.list' as user root unable to copy the users Xauthorization file.

My previous error codes with the code entered to get them:
gksu gedit /etc/apt/sources.list
(gksu:1973): Gtk-WARNING**: cannot open display:

gksudo gnome-terminal
(gksudo: 1689) Gtk-WARNING**: cannot open display:

Thank you for your patience and efforts. Do you think this problem in the area of bug/corruption, or should I worry about malware/virus?

Oh, I also found that my Ubuntu Software Center downloaded "Pychess" program wont run either - I guess it is linked to the kernel as well. BTW, the only other non software center program downloads I have done are Adobe PDF, and Java (Iced Tea doesn't seem to work on Chessgames.com)

---

### Post by garvinrick4 on 2011-07-20
If you open a terminal and run sudo apt-get update and you
get a merglist /var/lib/apt problem. Then run these one at
a time in a terminal.

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get clean all 
sudo apt-get update

```

---

### Post by jepkratz on 2011-07-21
> **garvinrick4 said:**
> If you open a terminal and run sudo apt-get update and you
get a merglist /var/lib/apt problem. Then run these one at
a time in a terminal.

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get clean all 
sudo apt-get update

```

Okay, after log-in and pword, terminal ran down the long list of traceback (most recent last call).

Interpreting your insturctions, I ran ( sudo apt-get update ) again. It ran through a long list of what look like update repositories - typical being ( Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release & Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main packages ) it then gave a MBs downloaded in X sec (didn't write down) then back to the prompt.

It did not give any merglist /var/lib/apt error or problem that I could see, so I exited terminal - the error icon was still present, so I re-booted. Problem icon reappears after about a minute (I assume while it is checking for updates upon booting/log-in)

Right, back to terminal/log-in, ran ( sudo apt-get update ) with same results, followed with ( sudo rm /war/lib//apt/lists/* -vf ) (my memory is already fuzzy, but I think it ran through some more code) then entered ( sudo apt-get clean all ) I think it just went to next prompt, then entered ( sudo apt-get update ) again and this time it had a much larger download.

Thinking okay, it looks like we've backed out the previous update, and re-installed, I returned to the GUI, problem icon still there, re-booted/log-in and after the 1 minute or so delay, problem icon reappears.

After re-entering terminal/log-in I decided to write down best I could the traceback as follows:
Last Login: Wed Jul 21 0947:50 PDT 2011 on tty1
Traceback (most recent call last):
File "/usr/lib/update-notifier/apt-check"' line 10, in <module>
import gettext
File "/usr/lib/python2.6/gettext.py", line49, in <module>
import locale, copy, os, re, struct, sys
File "/usr/lib/python2.6/locale.py", line14, in <module>
import sys, encodings, encodings.aliases
ImportError: No module named encodings
run-parts: /etc/update-motd.d/90-updates-available exited with return code 1

And then it returns to the prompt.

I hope I have proceeded as intended, and that I have reported the events accurately. Thanks again, etc.

---

### Post by jepkratz on 2011-07-24
To whom it may concern:
Well, whatever was happening, when I booted up this am, ubuntu decided to crash the rest of the way. When I got to the gnome desktop, a series of windows opened with a triangle and exclamation point. The text of each as follows:
"The panel encountered a problem while loading "OAFIID:GNOME_NotificationAreaApplet". Do you want to delete the applet from your configuration? I clicked on the "no" button. The other windows were all the same, except they contained as follows in place of "_NotificationAreaApplet"; _IndicatorApplet, _ClockApplet, -FastUserSwitchApplet, _WorkspaceSwitchApplet, _Panel_TrashApplet, _WindowListApplet, _ShowDesktopApplet.

I was then left with a blank purple screen (ubuntu version of the "blue screen of death?") :(

On reboot the terminal had this message for me
Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filsystem doesn't have /sbin/init
No init found. Try passing hit = bootarg

Having reached an end of my ability to continue trying to work this thing out - I do thank you very much for the help garvinrick4 and cipherboy - I have reformatted my HD, and re-installed ubuntu, and installed the latest updates. :confused:
While discouraging to have an ubuntu linux crash after just 4 weeks of use, I do like the OS, and plan to continue using it. My recommendation to anyone going thru a similar even is of course, back-up, back-up, an back-up.

Best regards ubuntu forums,
jepkratz

---

### Post by garvinrick4 on 2011-07-25
> While discouraging to have an ubuntu linux crash after just 4 weeks of use, I do like the OS, and plan to continue using it. 
I have found through many installs of Linux that any stable version that I install when I do
get a problem it is mostly and highly likely a user error. I believe is part of learning curve 
of the Free and Open Source Operating Systems known as Linux. I would not want it any other way, 
though my many mistakes I learn. 
> My recommendation to anyone going thru a similar even is of course, back-up, back-up, an back-up.
I do not care what O.S. you use if not backed up you deserve the final outcome eventually.

---

