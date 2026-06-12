---
title: "GUI Problems"
date: 2006-04-24
forum: General Help
---

### Post by ahd100 on 2006-04-24
Hi,

I'm currently having problems getting kde to launch as normal.

It all started after some fiddling trying to get openoffice to work properly having switched between a few different versions.

Now when I start the computer I get only a terminal style log-in rather than the graphical one I usually get. Once logged in I have tried to start the X server using 'startx' but I get errors telling me that the 'bitmap' and 'pcidata' modules do not exist and X will not start.

I've tried reconfiguring the server using 'sudo dpkg-reconfigure xserver-xorg' but this did not help.

Please give intimate detail of any suggested solutions as I'm very new to linux, particularly the terminal commands.

Thanks,

Andrew

---

### Post by jazzmuzik on 2006-04-24
(Read the message below before reading this one.)

I do this when things are totally unfixable to restore kde default settings. Note that this is a last resort if you can't fix the problem. It's a way of putting KDE back to its default values.

1. Boot up to the log-in screen. 

2. Press Ctrl-Alt-F1 to get a text mode screen. 

3. Log in

4. Move .kde to dot-kde ('mv .kde dot-kde')
This disables all the kde settings which will be recreated when you go into KDE the next time. Your old KDE settings are in the dot-kde directory and you can merge back the important ones, like config files, etc.

5. Exit the text mode shell: Ctrl-D

6. Return to GUI mode: Alt-F7

Now you should be back at the gui login screen. Now log into KDE the way you normally do. All your KDE setting should be reset to the defaults and your old settings are stored in the dot-kde directory. The last step is merging some of your old settings to the new .kde directory. This is time and thought consuming. I'll leave it to you to figure out how to do that, but you need to use a text editor. You can use gedit for that.

---

### Post by jazzmuzik on 2006-04-24
Oops. Well, I reread your problem and you are in worse shape than I thought. You must have messed around in sudo mode and done more than just user directory damage which the solution above addresses. I'm wondering if there is a dpkg or apt-get command that can reinstall packages that are broken. Hopefully somebody will chime in.

---

### Post by ahd100 on 2006-04-25
It seems my problem is the same as detailed in this thread : [http://ubuntuforums.org/showthread.php?t=8566](http://ubuntuforums.org/showthread.php?t=8566)

The strange thing is that this thread is over a year old and related to an earlier version of Ubuntu.

The error message shown there is exactly the same as I get but I can't revert to an older version of Xorg because I don't have one in the archives.

Upon trying "sudo ln -s /usr/X11R6/lib/modules/extensions/libglx.{so,a}" as suggested by daniels in the aforementioned thread I found that /usr/X11R6/lib/modules/ doesn't appear to be a directory as the above command might suggest, might this be related to the problem?

I haven't a clue what's going on here!

---

### Post by ahd100 on 2006-05-02
This problem's really holding back my degree work for my major project. Any sugestions would be greatly appreciated.

Thanks

---

