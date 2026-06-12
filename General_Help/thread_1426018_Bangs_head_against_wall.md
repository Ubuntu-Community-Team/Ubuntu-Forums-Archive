---
title: "*Bangs head against wall*"
date: 2010-03-09
forum: General Help
---

### Post by Autumn Night on 2010-03-09
Good evening everyone.

I finally got my nVIDIA graphics card to work, though I am using version 96 as I couldn't get 175 and 183 to work. Now I have a new problem.

When ever I log out or restart my computer, my display settings reset from 1240x1060 to 800x600. My graphics card stays selected, rather it's the settings in my nVIDIA X server settings that get erased. I've tried saving my settings, and I get the following error:

Failed to parse existing X config file '/etc/X11/xorg.conf'

Now, while I was trying to fix the old '800x600' problem, I tried to go in through the terminal and 'fix' my X-Server settings. I am not sure if this has anything to do with my new problem, and I have found what I think is the new file I made, and deleted it. Still I have this problem, and still I get this error message.

Help!

---

### Post by wojox on 2010-03-09
Open your terminal and:

```
sudo nvidia-xconfig
```

Then:

```
gksudo nvidia-settings
```

It should stick now.

---

### Post by Autumn Night on 2010-03-09
I did that, and here is what happened:

```
autum@autum-desktop:~$ sudo nvidia-xconfig
[sudo] password for autum: 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

autum@autum-desktop:~$ gksudo nvidia-settings
/home/autum/.themes/c2/gtk-2.0/gtkrc:54: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
autum@autum-desktop:~$ 

```It let me save afterwards, so I logged out then back in, and the same thing happened. I tried saving again, and:

Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'

I'm really not sure what I did to mess this all up lol.

---

### Post by Autumn Night on 2010-03-09
And, now my window taskbars and buttons (close, minimize, etc) are gone. :(

---

### Post by lakersforce on 2010-03-09
> **Autumn Night said:**
> And, now my window taskbars and buttons (close, minimize, etc) are gone. :(

Try to turn off visual effects. system > settings > looks (sorry, not using english version). Go to visual effects tab and turn everything off.

---

### Post by Autumn Night on 2010-03-09
Well, this helped with the no tool bar thing, but how do I get them back under the 'Extra' setting?

---

### Post by lidex on 2010-03-10
Do you have ccsm (CompizConfig Settings Manager) installed? Look in your applications menu: "System>Preferences>CompizConfig Settings Manager"
If it's there, open and under "Effects" click "Window Decoration". In the command field enter:
```
/usr/bin/compiz-decorator
```
Logout/reboot. If not installed you can do so with this command in a terminal:
```
sudo apt-get install compizconfig-settings-manager
```
"Applications>Accessories>Terminal"

---

### Post by Autumn Night on 2010-03-10
Yes, I do have it installed, and this is another thing that resets when I relog/boot. My windows were fine until I tried the code from above, though I don't know why that would harm anything.

---

### Post by shockandawe on 2010-03-10
For the visual effects reseting problem. Check my post on this thread. I made a step-by-step.

[http://ubuntuforums.org/showthread.php?p=8938181#post8938181](http://ubuntuforums.org/showthread.php?p=8938181#post8938181)

---

