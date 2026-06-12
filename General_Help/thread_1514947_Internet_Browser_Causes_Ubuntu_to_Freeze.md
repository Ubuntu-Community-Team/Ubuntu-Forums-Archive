---
title: "Internet Browser Causes Ubuntu to Freeze"
date: 2010-06-21
forum: General Help
---

### Post by Sugi on 2010-06-21
I am having a huge issues with Opera, Japanese (Anthy), and Ubuntu 10.04.  The reason, I know it's directly related to Opera and Japanese, because this has happen on two machines now, one being 10.04 & 9.10.  The freezes themselves are weird as well.  

 - The first kind of freezes completely lockup the screen and keyboard, I can't click on the GUI, I can't use any keyboard shortcuts, and my power button doesn't even work.
 - The next kind of freezes disables clicking of the GUI, but I can use the keyboard to control the computer.  At which point, I completely close out of Opera and everything is back to working order. 
 - The next kind of freeze disables all type in Opera and only in opera, but I can click on the GUI, use keyboard shortcuts and even control other programs.  I close down opera and restart it, opera + everything is working again.
 - And the last kind of freeze disables clicking of the GUI, keyboard shortcuts, and all programs, but I can sometimes click on the power button and it will bring up this system menu entitled "Shut Down the Computer".  This will give me options of shut down, restart, suspend, and hibernate.  At this point, I can now click on the GUI of this system menu and use my keyboard to operate the computer.  I close out of this menu and everything is back to working order.

Which is weird because this will only happen when Opera is open.  Also, all of my System Monitors work and I get updates from Pidgin that someone signed online even during these "kind" of freezes.

Machine one: 10.04
86x bit
Opera 10.10 build 4742
Japanese Anthy

Machine Two: 9.04
86x Bit
Opera
Japanese Anthy

Machine two worked fine with opera and without Japanese on it for a long time, but after installing Japanese on it, it started these weird kind of freezes.

Any idea on how to fix this?

Thanks for reading,
Sugi

---

### Post by dnguyen1963 on 2010-06-21
> **Sugi said:**
> I am having a huge issues with Opera, Japanese (Anthy), and Ubuntu 10.04.  The reason, I know it's directly related to Opera and Japanese, because this has happen on two machines now, one being 10.04 & 9.10.  The freezes themselves are weird as well.  

 - The first kind of freezes completely lockup the screen and keyboard, I can't click on the GUI, I can't use any keyboard shortcuts, and my power button doesn't even work.
 - The next kind of freezes disables clicking of the GUI, but I can use the keyboard to control the computer.  At which point, I completely close out of Opera and everything is back to working order. 
 - The next kind of freeze disables all type in Opera and only in opera, but I can click on the GUI, use keyboard shortcuts and even control other programs.  I close down opera and restart it, opera + everything is working again.
 - And the last kind of freeze disables clicking of the GUI, keyboard shortcuts, and all programs, but I can sometimes click on the power button and it will bring up this system menu entitled "Shut Down the Computer".  This will give me options of shut down, restart, suspend, and hibernate.  At this point, I can now click on the GUI of this system menu and use my keyboard to operate the computer.  I close out of this menu and everything is back to working order.

Which is weird because this will only happen when Opera is open.  Also, all of my System Monitors work and I get updates from Pidgin that someone signed online even during these "kind" of freezes.

Machine one: 10.04
86x bit
Opera 10.10 build 4742
Japanese Anthy

Machine Two: 9.04
86x Bit
Opera
Japanese Anthy

Machine two worked fine with opera and without Japanese on it for a long time, but after installing Japanese on it, it started these weird kind of freezes.

Any idea on how to fix this?

Thanks for reading,
Sugi

Roll your kernel back to 2.6.32-21-generic.  It has been working well for me.  Also look at other posts in this forum about freezes.

---

### Post by radddi on 2010-06-21
Well, to my mind Opera version 10.10 has already passed its shelf life. I don't know if this will cure your strange freeze problems, but try updating to the new Opera 10.60 Beta to see how it goes :D . Also, there are tons of new features, bug fixes and optimisations. And it's so stable that for the first time in my life I actually migrated to an Alpha release. The new beta is worth considering.

[http://www.opera.com/browser/next/](http://www.opera.com/browser/next/)

.:CheerS:. and hope I could help you.

---

### Post by Sugi on 2010-06-21
radddi,
I'll try it on Machine one, and see one how it works.  Thanks.

dnguyen1963,
Machine One:
2.6.32-22-generic
Machine Two:
2.6.31.17-generic

I'll look into it on Machine one.  Thanks for the tip.

Sugi

---

### Post by XSAlliN on 2010-06-21
Asian characters seem really heavy for most systems... :)

---

### Post by Sugi on 2010-06-21
They are not too heavy. :)

dnguyen1963,
I have two different kernel version, but the same problem between them.

Sugi

---

### Post by James Keating on 2010-06-22
I never had Opera problems like this -- Japanese input either works well or not at all.

Are you using Anthy with SCIM or IBus? For me, IBus doesn't work with Opera or other Qt programs. Ubuntu is pushing IBus and dropped SCIM, but IBus doesn't fully work yet. If you are using IBus, try switching to SCIM. If you are using SCIM, try switching to IBus. 

I've put most of what I know about Anthy and SCIM in the post [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=27811](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=27811)

1. installation: 

To use Anthy with SCIM, you should have the packages 
scim-bridge-agent
scim-bridge-client-gtk
scim-bridge-client-qt
scim-gtk2-immodule
scim-modules-socket
scim-qtimm

I also suggest 
edict, enamdict, gjiten, kanjidic, kasumi, poppler-data, gs-cjk-resource, cmap-adobe-japan1, cmap-adobe-japan2, xpdf-japanese for full PDF ability, a dictionary (gjiten) and a utility to add kanji combinations to the word lookup list (kasumi)

2. xinput.d:

Check your hidden home directory file ~/.xinput.d/en_US, which links to /etc/X11/xinit/xinput.d/scim-bridge. It must be edited as root. Mine was choosing xim first. I had to change it to prefer scim-bridge, then scim:

XIM=SCIM
if [ -e /usr/bin/skim ]; then
XIM_PROGRAM=" "
else
XIM_PROGRAM=/usr/bin/scim-bridge
fi
XIM_ARGS="-d"
if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
GTK_IM_MODULE=scim-bridge
else
GTK_IM_MODULE=scim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ]; then
QT_IM_MODULE=scim-bridge
else
QT_IM_MODULE=scim
fi
DEPENDS="scim | skim, scim-bridge-agent, scim-bridge-client-gtk | scim-bridge-client-qt"

3. Opera command:

You should be able to start Opera from the command line with 
scim -d & XMODIFIERS="@im=SCIM" QT_IM_MODULE="scim" opera

To start it from the regular menu, I made a file called ~/.bin/opera-scim:

#!/bin/sh
QT_IM_MODULE="scim"; export QT_IM_MODULE
XIM_PROGRAM="scim -d"; export XIM_PROGRAM
opera

then made it executable, and edited the Applications menu to change the Opera properties to run:
~/.bin/opera-scim %u

Possibly your locale is a problem, though I haven't had locale trouble in years. Adding these to the startup script might help:

LANGUAGE=en_US.UTF-8; export LANGUAGE
LINGUAS=en_US.UTF-8; export LINGUAS
LANG=en_US.UTF-8; export LANG
LC_CTYPE=en_US.UTF-8; export LC_CTYPE
LC_MESSAGES=en_US.UTF-8; export LC_MESSAGES
SUPPORTED=en_US:C:en_US:ISO-8859-15:ja_JP.eucJP:ja_JP.UTF-8:ja_JP:ja:ja_JP.JIS7:ja_JP.SJIS; export SUPPORTED

After that, I suggest looking at the log files. Something there may indicate your specific problem. 

You can also try newer or older versions of Opera. It's the only program I ever have trouble with, but I like it too much to switch.

---

### Post by Sugi on 2010-06-22
I haven't gotten any good results from the suggestions in this thread.  Bummer, has anyone come across this problem and figured how to fix it?

Edit:
Reading Material that's kinda related:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=27811&page=4](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=27811&page=4)

Sugi

---

### Post by XSAlliN on 2010-06-22
Well, this is the general Ubuntu forum... So finding a Japanese guy that happens to find a fix for your problem here - are pretty low... Even if there is 1 or 2 here with a solution, maybe they'll miss topic. That being said, I believe you'll have better luck on a a local forum:

[http://www.ubuntulinux.jp/](http://www.ubuntulinux.jp/)

English is not my native language, I'm actually from Romania, and obviously - solution specific to my language are more easy to find on local forum. Yet I use English version, don't like the translated terms... :)

---

### Post by Sugi on 2010-06-23
Thanks for the tip, but I think it's more linked to Opera issues and maybe just having a second language on the system as well.  Probably any second language infact.  The fix could just be an easy one that might not even be linked to Japanese.

Sugi

---

### Post by James Keating on 2010-06-23
You seem to have an uncommon problem with no clear cause and no specific error messages from any log files. It's not surprising no one knows the solution yet. Also, you made a new thread, so not many people will notice it. If you post to an existing thread, everyone else who ever posted to it will be notified, and you should get more responses. You may want to search for related threads, or try a Google search for something line ubuntu opera freeze crash

One more possibility: sometimes I have trouble with Opera when it looks for plugins in several places, and tries to run two at once for the same plugin. This is especially bad with Flash. Try going to Preferences, Content, Plug-in Options and changing the path to /usr/lib/mozilla/plugins.

---

### Post by omac on 2010-06-24
I'm using Opera 10.10 on Ubuntu 8.04, and this version of Opera freezes whenever I minimize(through double clicking) it to the Information(?) panel/bay ... the same bay that shows the status of the network configuration, the day, date, and time.

If I don't double click to minimize Opera to that panel, it doesn't hang.

By hang, I mean the whole computer just freezes.  I can't try to toggle to another application; I can't click anything.  The mouse moves, but that's it.  Everything else hangs.

I just remind myself to not double click to minimize into that tray/panel. :D

---

### Post by James Keating on 2010-06-24
This may be a bug in Opera:
[https://bugs.launchpad.net/ubuntu/+bug/489863](https://bugs.launchpad.net/ubuntu/+bug/489863)

and no solution is posted there.

---

### Post by Sugi on 2010-07-06
I was afraid that might be true. :S  Thanks for the link though.

Sugi

---

