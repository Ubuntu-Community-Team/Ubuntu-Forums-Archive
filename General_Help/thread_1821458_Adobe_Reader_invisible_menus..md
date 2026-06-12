---
title: "Adobe Reader invisible menus."
date: 2011-08-09
forum: General Help
---

### Post by sbutton on 2011-08-09
Hi,

I've just scrubbed Windows 7 starter edition and installed Ubuntu 10.10 (netbook?) on an Asus EEE PC 1008HA. When I installed Adobe Reader(9.4.1-1_i486), I do not see any of the menus. It seems to work fine apart from that, but the main reason I want to use it is the "read aloud" functionality. 

(I'm hoping to get it to read some of my course work for my OU degree while I'm commuting in the car)

The menus are visible at the top of the screen, "File Edit View Document Window Help" but as soon as I click any of these I just get a grey drop down, with grey writing, so I obviously can't read any of the menus. Been googling around for this, but can't find anything helpful. 

I'm happy to use something other than Adobe Reader, but I've tried xpdf (very old) and kpdf (not maintained) and ePDFViewer, but none of these seem to have the "read aloud" functionality. 

As it happens, currently the read aloud doesn't even work with Adobe Reader, because when I right click and choose Page Display Preferences, all the options for read aloud are greyed out... but I'll probably be able to figure that one out myself if I can get the menus to appear.

---

### Post by sbutton on 2011-08-10
Anyone? Am I in the wrong forum? Should I go back and re-install Windows 7, which gives me what I need?

---

### Post by aloksethi on 2011-11-08
[http://ubuntuforums.org/showthread.php?t=1724528](http://ubuntuforums.org/showthread.php?t=1724528)

for me this worked
open a terminal ctr+alt+t
export UBUNTU_MENUPROXY=

acroread

this should open acrobat reader with visible menues

u can add "export UBUNTU_MENUPROXY=" to your .bashrc also

---

### Post by sbutton on 2011-11-08
In the end I re-installed with the desktop edition 10.10 Maverick and the problem went away. HTH

---

### Post by mech-e on 2011-12-25
> **aloksethi said:**
> [http://ubuntuforums.org/showthread.php?t=1724528](http://ubuntuforums.org/showthread.php?t=1724528)

for me this worked
open a terminal ctr+alt+t
export UBUNTU_MENUPROXY=

acroread

this should open acrobat reader with visible menues

u can add "export UBUNTU_MENUPROXY=" to your .bashrc also

Thanks! Had same problem and this is really helpful. To get this to work when launching the program from Gnome, though, I needed to create an Xsession.d file because the variable got set there in a fairly brittle fashion in my Ubuntu 11.10 install.

I created a file that I named 98menuproxy (in /etc/X11/Xsession.d/98menuproxy ) with the line:
```
export UBUNTU_MENUPROXY="acroread":$UBUNTU_MENUPROXY
```

and that works great now :)

---

### Post by akabdul on 2012-02-12
Thanks for the fix. It works perfectly after logging out and logging in again.

---

### Post by Doggo#86 on 2012-03-01
Thanks that work perfectly

//from terminal
cd /etc/X11/Xsession.d
sudo gedit 98menuproxy
//open gedit
//paste
export UBUNTU_MENUPROXY="acroread":$UBUNTU_MENUPROXY
//save file
//log off and log on

Quick simple fix, I love it :)

---

### Post by themirror178 on 2012-04-25
> **Doggo#86 said:**
> Thanks that work perfectly

//from terminal
cd /etc/X11/Xsession.d
sudo gedit 98menuproxy
//open gedit
//paste
export UBUNTU_MENUPROXY="acroread":$UBUNTU_MENUPROXY
//save file
//log off and log on

Quick simple fix, I love it :)

Hi when I did this it worked but the menu on google chrome disappeared!and also the menu on adobe reader and the 'close/minimize/maximize' options were on two different lines (if that makes sense)

Anyone know how to fix my google chrome problem? :(

---

### Post by Redcougar27 on 2013-04-15
Hello, 
I have the same problem with Adobe Reader and Ubuntu 12.10: all the menus are black.

The solution UBUNTU_MENUPROXY= acroread works but one time only.

When opening again Adobe Reader, the menus are black again.

What I have to do to make that permanent? 

PS: I don't understand the solutions mentionned above (export UBUNTU_MENUPROXY=" to your .bashr; ...).

Thanks
Best regards.

---

### Post by Redcougar27 on 2013-04-17
Hello,
 
Sorry to disappoint you, but the tip mentionned is NOT working:

 
The command env UBUNTU_MUNUPROXY ... works for one time only; ok with that. 
 
BUT the command QUOTE Paste this "cd/etc/X11/Xsession ... UNQUOTE doesn't work.
 
I run Ubuntu 12.10 and Adobe Reader 9.5.4
 
Thanks & best regards.

---

### Post by dipankara on 2013-08-12
sudo gedit /usr/local/share/applications/AdobeReader.desktop
 change ”Exec=acroread“ to ”Exec=env UBUNTU_MENUPROXY= acroread“ 
notice the space

---

### Post by Sulpicia3 on 2014-04-09
Found the answer, at least for my system (this is the answer: [http://askubuntu.com/questions/73272...adobe-reader-9]("http://askubuntu.com/questions/73272/how-do-i-disable-the-global-application-menu-in-adobe-reader-9")).

Here's what I did (slightly modified version that seemed to work-- bear with me, I just started using linux this morning)

Make sure adobe is closed. Open your terminal (to open: CRTL + ALT + t)
[FONT=courier new]sudo gedit /opt/Adobe/Reader9/bin/acroread[/FONT][FONT=arial]
Then a window should appear with a bunch of coding in it. There is a section at the top with some copyright information. You will notice that each of those lines starts with a # (they are commented out so the computer doesn't read them) and that there is one empty line with a # at end. After the final # in the top section,in the next line down (not next to a #-- if you begin the line with a # the computer won't read it) add this:
[FONT=courier new]export UBUNTU_MENUPROXY=acroread[/FONT]
Press save. Close the window. Close the terminal.
Reopen Acrobat. It worked for me. 
[/FONT]

---

