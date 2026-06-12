---
title: "Ubuntu 9.10 Can't Login"
date: 2010-02-15
forum: General Help
---

### Post by wolf_3d on 2010-02-15
Hello,

Lately I've become very addicted to Ubuntu so I've been using it more recently than in the last 2 years or so. I also made several changes to the Ubuntu partition and swap partition to bring my Ubuntu partition up to 27 GB from 19GB. I logged into it this morning and spent a few hours tweaking my cairo-dock, installing thunderbird and a few other tweaks but when I restarted it, I could no longer login even though I'm using the right password.

It gets to the login screen as usual and I click on my name and insert my password but then the screen flickers, goes black and then takes me back to the login screen :frown:.

So i've got back into my Windows XP account without any problems
and I've looked around this forum to see if there is anything similar and I've found these threads which sound similar but I'm not sure if they are relevant to me;

[http://ubuntuforums.org/showthread.php?t=1316229&highlight=can%27t+login](http://ubuntuforums.org/showthread.php?t=1316229&highlight=can%27t+login)
[http://ubuntuforums.org/showthread.php?t=1342147&highlight=can%27t+login](http://ubuntuforums.org/showthread.php?t=1342147&highlight=can%27t+login)

---

### Post by flippo on 2010-02-15
Your problem seems fairly common, something is causing your login to crash, then gdm is restarting your login screen.  Can you post the output of ~/.xsession-errors?

---

### Post by wolf_3d on 2010-02-15
Thanks for the quick reply, I'm not sure how (or where?) I would use the ~/.xsession-errors command.

A couple of other things I've tried is to click on the "Other" button and try logging in that way but it comes up with an authentication failure. And using another kernel doesn't work either.

---

### Post by flippo on 2010-02-15
I'm sorry, I wasn't very clear.

.xsession-errors is a file in your home directory.  At the login screen push (ctrl+alt+f1) to drop to tty1 then login and open .xsession-errors (using something like nano or less).  Then tell me what it says (it may be long).

---

### Post by wolf_3d on 2010-02-15
Ok, I've managed to work out how to do this using nano. The following is the complete output that it gave me;

/etc/gdm/Xsession: Beginning session startup...
/etc/profile: 29: [[: not found
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinpu$
Unable to create /home/john/.dbus/session-bus
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 29: [[: not found
.: 34: Can't open /home/john/.profile

(8 Lines)

I've also tried;

stop gdm
startx&

which gave me a black screen with my cursor in the middle of it.

---

### Post by wolf_3d on 2010-02-16
UPDATE - I've been trying some of my own problem solving today and here's where i'm up to.

Using this thread: [http://ubuntuforums.org/showthread.php?t=1338879](http://ubuntuforums.org/showthread.php?t=1338879)

I've used some of the ideas from here to see if it helps me.

I've opened my xorg.conf file in nano and checked that the configuration for my monitor is correct.

I then noticed this section:

```
SubSection "Display"
           Depth   24
           Virtual 1440    900
           Modes           "1024x768@75"  "1024x768@70"
EndSubSection
```

So I thought that the value of virtual was wrong and changed it to 1024 768 using nano. This didn't fix it.

I then decided to change it to "1440 900" as this would be the same resolution as my desktop. However I'm still not having any luck no matter how many times I try to log in.

Using the older kernels (I have 3) doesn't work as they are all variants of the 2.6.31.x kernel.

I've tried going into recovery but there is no option for failsafe gnome and I can't start x using the command startx as it just gives my a black screen with the cursor and no hdd activity.

---

### Post by wolf_3d on 2010-02-17
UPDATE #2 - I have tried using the following...

```
sudo dpkg-reconfigure xserver-xorg
```

...to try and see if I can reconfigure the xserver but it is not showing the setup screens and instead after typing the above it returns to prompt.

I'm starting to run out of options here - I know I'm not the only one to embrace this problem so please somebody has to be able to suggest something.

---

### Post by wolf_3d on 2010-02-17
Update #3 - I have now tried uninstalling gdm and then installing kdm, but when I rebooted and kdm loaded - it changed behaviour.

It no longer flickered or looped but once I entered my username and password the login screen disappeared to leave the background where it appears to do nothing. I assume it hangs at this point.

I decided to uninstall kdm and then reinstall gdm. But now the behaviour has changed with this too. Once i've entered my password the ubuntu logo and horizontal scrolling bar appears and scrolls from side to side for a while before a terminal with a white background appears in the top left hand corner and it just does...nothing.

There seems to be a real problem loading the desktop.

---

### Post by stoneage on 2010-02-17
I take it you undid those xorg.conf edits?

---

### Post by wolf_3d on 2010-02-17
UPDATE 4 - YESSSS!!!! I'M BACK IN MY UBUNTU ACCOUNT!!!!!

I went into the recovery option for my most recent kernel and then chose the option for dpkg - fix broken packages (or along those lines) and it seems have installed various packages such as cupsd and more strangely evolution which I deleted on monday in favour of thunderbird. It then reconfigure the ubuntu desktop and when it had finished I rebooted and...here I am back in my ubuntu account :D.

This is my first successful login so I won't get too happy just yet. I'm going to make some backups, check a few settings and then try rebooting and logging back in a few times.

I'll report back if I experience any more problems over the next week or two and then mark this as solved.

---

### Post by wolf_3d on 2010-02-24
It's been about a week now, and I've had no problems since so I'm now marking this as solved. I think the problem was to do with closing Ubuntu down using the cairo-dock so I wont do that again.

---

### Post by colsinc on 2010-12-11
Just adding a note to this, I had a problem that seemed very similar.  When logging in, the screen flickered (some text, too fast to read) and then returned to the login screen.

I went to tty1 and looked in ~/.xsession-errors and saw that it could not read the file ~/.ICEauthority

Then I changed this file to world writeable (temporarily lol) 
sudo chmod 777 /ICEauthority

Returned to the login screen, and was able to login.
--
The problem developed after I did an upgrade (but didn't restart as instructed) and then did another update a few days later, and then restarted

---

