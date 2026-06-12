---
title: "xubuntu-desktop installed, but..."
date: 2006-03-19
forum: General Help
---

### Post by m.musashi on 2006-03-19
Okay, I thought I'd try the xubuntu desktop for fun. I did ```
sudo apt-get install xubuntu-desktop
``` and it seems to have installed fine. At the login screen I choose session and then xfce. It loads and I get a green desktop with a mouse and XFCE under it - nothing else. Right or left clicking the desktop gives me nothing. It does nothing. If their goal was a minimalist experience then they have succeeded. I would like a bit more functionality personally.

Any idea? I am using dapper flight 4 on a dell 600m laptop.

Thanks.

---

### Post by taurus on 2006-03-19
Look in "ps -A" to see if you have xfdesktop running!  If not, run it from a terminal "xfdesktop &" and save the session.  Log back in and see if your right mouse button working!

---

### Post by 5-HT on 2006-03-19
Hey, while XFCE is a minimalists desktop (sorta, comes with lots of nice utilities though), it's definitely not that minimalistic!

Looks like there may be an issue with Dapper's xubuntu-desktop.
I'm not running Dapper but did come across this recent thread in a search which seems to describe you problem.

Maybe this will be of help?
[http://ubuntuforums.org/showthread.php?t=140914]("http://ubuntuforums.org/showthread.php?t=140914")

Some highlights from that thread (and some from the top of my head) that may help...

Try running (if they aren't already, as taurus pointed out a 'ps aux' or similar will let you know): 
```

xfce4-panel & 
xftaskbar4 &
xfdesktop & 
``` 
For the panel, taskbar, and desktop drawing (incl. middle/right click menus), respectively.

It would probably be best to follow any of this up in the Dapper forum.

HTH

---

### Post by m.musashi on 2006-03-19
Thanks for the feedback. I'll check the other thread. However, when you mention running something, where do I run it. xfce doesn't load so I do I do it gnome or drop to terminal level?

Taurus: I'm not sure I get the ps -A bit. Again, do it from the terminal or gnome? If at terminal level then xfdesktop wouldn't be running would it?

---

### Post by 5-HT on 2006-03-19
[quote=m.musashi]Thanks for the feedback. I'll check the other thread. However, when you mention running something, where do I run it. xfce doesn't load so I do I do it gnome or drop to terminal level?

Taurus: I'm not sure I get the ps -A bit. Again, do it from the terminal or gnome? If at terminal level then xfdesktop wouldn't be running would it?[/quote] 

Ouch, my bad.

Can you bring up a run dialogue (alt + F2) to enter the commands?

If not, there are a couple things to try (doing the previous from GNOME wouldn't affect XFCE).

1)
First off all why don't you try shutting down GDM
```
sudo /etc/init.d/gdm stop 
``` 
And try running XFCE using
```
startxfce4 
``` 

2)
If that doesn't work, what you could try to do is create your own custom .xinitrc script for starting an X session with 'startx'.
You'll need to do this from a virtual terminal or from GNOME (to get GDM runing again to do it from GNOME: sudo /etc/init.d/gdm start).

Here is a great guide for that:
[https://wiki.ubuntu.com/CustomXSession]("https://wiki.ubuntu.com/CustomXSession")

In brief, something like this may work:

```
#!/usr/bin/env bash
xfce4-panel &
xftaskbar4 &
xfdesktop &
exec startxfce4
``` 
Save this file as 
```
~/.xinitrc 
``` and make it executable with
```
chmod +x ~/.xinitrc 
``` 
To run it, type:
```
 startx 
``` 
Hopefully, XFCE will boot along with its panel, takbar, and desktop drawing.

If the above works, simply save your session on logout.
You can then delete the ~/.xinitrc file you just created and start GDM with: 
```
 sudo /etc/init.d/gdm start 
``` 
Once you log in, hopefully you'll be greeted with the proper functionality.

This is a really long way to get around the problem and the only reason I've given it is so that you can boot into a functional XFCE session. 
That guide also  talks about creating a custom X session script that will work for GDM as well, if you want to just keep using it and not the default XFCE one (that was beyond the scope of this blurb).


Again, the Dapper forum may be a better avenue for help on this issue as I'm not up to date at all on what's going on in Dapper. It is still in development though, so if this is a bug it should get ironed out (as long as a bug report is sent or a dev is aware of the issue).

HTH

---

### Post by Chozabu on 2006-03-19
logging in without X, then
sudo startxfce4
(someone alredy mentioned, i know)
works - but it logs in as root, and seemed to bork the .ICEauthority in my home dir
sudo chmod 777 .ICEauthority
fixed it (yeah, shouldnt be 777, but i cant remember the nums :P 755 perhaps?)

---

### Post by Chozabu on 2006-03-19
hmm, trying to install the xfce taskbar, i get this message

```
xfce4-taskbar-plugin:
 Depends: libxfce4util-1 (>=4.2.1-1) but it is not installable
 Depends: libxfcegui4-3 (>=4.2.1-1) but it is not installable
```

though those exact packages arnt there, there are two newer ones that say they replace the "not installabale" ones..

---

### Post by m.musashi on 2006-03-19
Thanks 5-HT. The script worked. However, I have a very gnome looking desktop (top and bottom panels, workspace switcher, etc). It's not exactly the same but I thought xfce had a mini panel on the bottom by default. Is the xubuntu version different?

Anyway, it's working. Now something new to learn. Thanks.

EDIT: well, it's not exactly working after all. I was able to run one app (a game) and then nothing else worked. Firefox wouldn't load nor would any other app I selected including the terminal. I'd right click, choose something, the mouse pointer would show busy for a moment and then nothing. I couldn't even log out. I did a restart and back to the same problem - no panels, no right or left click, no nothing. I booted to a terminal and did "startx" again but now it just brings up the same useless desktop.

---

