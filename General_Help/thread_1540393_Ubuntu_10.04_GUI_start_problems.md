---
title: "Ubuntu 10.04 GUI start problems"
date: 2010-07-27
forum: General Help
---

### Post by forume on 2010-07-27
Hi, 
I've just started using linux after so many ears of windows and think its great. The first few times I booted it was all well and good. It would load normally and allow me to login with my credentials. 

The only problem I have with it now is that it doesn't start, or I should say it doesn't load my user account, eg username: Joe. 

Each time I boot linux it doesn't load the GUI and login screen, as per usual, instead I get this:

"Ubuntu 10.04.1 LTS ubuntu tty1

ubuntu login:"

I log in with my credentials --- it accepts, fine.

next I get this:
* Documentation: [https://help.ubuntu.com](https://help.ubuntu.com)
j@ubuntu:~$

At this point (after careful reading on this forum) I've tried sudo startx, which logs me into the GUI not my own account, but as the root user. 

I'm not sure how but while logged in as the root user, I managed to set it so that it would automatically log into my user account on start up. This worked for a while. 

It has reverted to that wierd text base screen: 

"Ubuntu 10.04.1 LTS ubuntu tty1

ubuntu login:"

and not the GUI login screen I miss so much. I've forgotten how I managed to log back into my account and I'm sure there must be an easier way. Because my way required switching the system on and off several times.

Is there away I can jump directly to my account on start up? Or at least log in with my account? 

I don't mind logging in as root, but I understand its not the done thing on linux.

Please help!

---

### Post by robsoles on 2010-07-28
Hi, firstly let me apologise for the community that it is me answering instead of one of the others that could (perhaps) serve you better with this problem!!!

What is happening is that you are being dumped in terminal shy of gnome which runs in x - the mere fact that you mention 'startx' indicates that you are aware of this so I apologise I need to state some obvious things on my way to an attempt at helping.

'sudo startx' is a good reason to land in a desktop as root - did you try 'startx' without the sudo bit?

After x starts and you land in a pretty pretty GUI, do you have a top and bottom panel? In the top panel (if you got one) does it have an icon like a power button and if so then did you find 'Log Out' under it? if you click 'Log Out' under that menu do you land up in ugly ugly terminal or do you get a user login screen as if supported by pretty GUI?

I'll pursue this as far as it takes to get you to mark your thread as 'solved' or to tell me to go away - amongst other things it is at least possible I will learn something!!!!

---

### Post by forume on 2010-07-28
Hi, thanks for replying. 

Its just so wierd. I booted the computer as normal today and what do you know its auto logged me into my own user account in the pretty GUI. I've not touched it since posting this thread. So I suspect it has a mind of its own. Is Linux Ubuntu an AI OS? 

Regarding startx, yes I've tried it without the sudo bit. I don't remember what it returned, but it didn't work. 

Whilst being logged in the GUI as the root, I did have a top and bottom panel, also, tried to log out, thinking I could log back in again with my own user account, but I got an error message instead of that ugly terminal or the pretty GUI. I don't recall what the message read and there is no way of testing it now that I'm not in as the root. Or is there?

---

### Post by forume on 2010-07-28
Ok, so I've rebooted again and it brings up the terminal screen again. 

I type startx without sudo, the screen goes blank for a while then lists the following:

Code
==============
..
No protocal specified
..
No protocal specified 
..
No protocal specified etc.....
.. 
giving up.
xinit: recourse temporarily unavailable (errno 11): unable to connect to X server
waiting for X server to shut down . ddxSigGiveUp: Closing log

xinit: Server error.
xauth: /home/j/.Xauthority not writable, changes will be ignored
j@ubuntu:~$

=============

I then type sudo startx and I now get the same as above!!

It seems I can't even log into the root.

---

### Post by robsoles on 2010-07-28
try
```
sudo service gdm restart
```

and if that fails with errors try 'start' on the end instead of 'restart' and if that fails please post back the error message(s).

I am less sure of this one doing too much for you but if you are already trapped in terminal then trying it over from 'restart' after replacing 'gdm' with 'x11-common'

---

### Post by motonnerd on 2010-08-02
I have a very similar problem.  After selecting the current linux image in GRUB I would see the beginnings of the normal Ubuntu startup splash, but then I am kicked down to terminal.  Similarly, login credentials are taken just fine, and startx kicks me into the GUI.  I have had this happen previously, then it went away, and now it's back.  And whenever I log out, it does kick me back to terminal.
Anyway, something which hasn't been previously mentioned in forume's description:  with me, I have to unlock my login keyring, because I'm told it wasn't unlocked when I logged in.  Previously, I had never noticed anything else wrong.  Now, though, I see something different..
Sudo's working fine, but something else isn't.  I tried to change my login screen settings (hoping to regenerate/repair some missing/corrupted file) when I found I was unable to unlock it.  Upon issuing 'gnome-control-center' at terminal, I get a slew of errors, the highlights I will describe here (bits and pieces of errors):
error getting /desktop/gnome/applications/main-menu/lock-down/user_modifiable_apps
load_xbel_store:  couldn't load bookmark file [NULL]
couldn't load gtk-theme-selector.desktop or gnome-cups-manager.desktop
and a whole lot about missing .service files sprinkled throughout.
there's some interesting output here:  ** (gdmsetup:2410): DEBUG: Found two sessions for user <the user I logged in as>
Failed to unlock:  The name org.gnome.DisplayManager was not provided by any .service files.

So there you go.  I logged out, then sudo gdm start brought up the login screen like you had suggested.  No keyring unlocking needed, and the login preferences utility works just fine.  Gonna restart, I'll let you know if it persists!

Possible connection to this? (I haven't researched it in-depth, just a quick Google search to try to learn about gdm)
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/432492](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/432492)

---

### Post by motonnerd on 2010-08-02
Didn't change anything on reboot, but I put in the same sudo service gdm start command and it worked fine. Booting as normally. I hadn't, though, made any changes to the login preferences. Something I found interesting, too, was that the 'play login sound' service was disabled under 'startup applications', but that preference was on in the login preferences window. Didn't change anything. No errors I can see in the terminal, I guess it's going by too fast for me to pick it out.

On a side note, that was an outdated sig.  My problem is on a 64-bit AMD computer with NVidia graphics, which have been working without a hitch (except for this).  Also have Compiz running, I don't know if that messes with anything...

---

### Post by robsoles on 2010-08-02
Compiz hasn't stuffed up several desktops and a couple of laptops in my life, they are all on 10.04 LTS.

Please post back contents of /etc/init/rc-sysinit.conf obtainable in terminal:
```
sudo cat /etc/init/rc-sysinit.conf
```

EDIT: Also, if a file /etc/inittab exists then it's contents as well please.

---

### Post by forume on 2010-08-04
For the past few days my system didn't even allow me to log in via the terminal. I kept getting this:
Checking battery      [ok]

and nothing would happen. 


Today I booted and logged from the terminal screen. I entered as you said:
sudo service gdm start 

It logged me into my account - great! 

I too am getting an "unlock login keyring"  - what exactly is this?

I think my version of Ubuntu has a mind of it's own, its so temperamental!! ](*,)

---

### Post by robsoles on 2010-08-04
> **forume said:**
> ... 

I too am getting an "unlock login keyring"  - what exactly is this?

...

The 'keyring' refers to the preferred place for programs to keep your passwords to stuff like mail, smb shares and whatever has a password really.

In a 'normal' desktop session of Ubuntu it is unlocked for you as part of your regular login process.


> **forume said:**
> ...

I think my version of Ubuntu has a mind of it's own, its so temperamental!! ](*,)

Something has to have caused it. Taking downloads from websites other than Ubuntu.com and executing them, installing crazy themes that the Ubuntu developers/community haven't checked out etc etc would be my first suspects.

---

