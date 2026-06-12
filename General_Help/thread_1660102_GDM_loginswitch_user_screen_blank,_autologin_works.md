---
title: "GDM login/switch user screen blank, autologin works"
date: 2011-01-04
forum: General Help
---

### Post by edorfaus on 2011-01-04
I've run into a strange problem with GDM that I haven't managed to find a solution for yet, either by trying myself or googling, and I have run out of good ideas. I'll just infodump here about the problem and what I've tried etc; can anyone help me with figuring it out and getting it fixed?

I installed Ubuntu on a new PC a few weeks ago, setting it up with autologin for my mom and a separate user for myself, using the on/off-icon menu in the top-right corner to switch to my own user and back as needed, and logging the user out when done. This worked quite well.

However, a few days ago, this stopped working; logging out or trying to switch now leaves me with a blank black screen, without even a mouse pointer (but not off, the backlight is on).

[COLOR=Navy]*EDIT: To clarify, this is an issue that only affects the GDM login screen, but that affects it whenever it is used, wether it is on boot (when not set to autologin), after logging out, or when trying to switch user.*[/COLOR]

At this point, I can usually use Ctrl-Alt-F1 to get a textmode login, and Ctrl-Alt-F7 to get back to the auto-logged in session (assuming I tried to switch, not logout).

I can't think of anything specific I did or installed around then that should be related in any way...

I tried disabling autologin and restarting gdm, which left me with the same black screen (which is still there after rebooting), instead of the expected login window. I managed to re-enable autologin by manually editing the /etc/gdm/custom.conf file, so that it would at least work for mom.

I've also tried to change which user is auto-logged in, thinking it might be a problem with my user account, but both users get an automatic session just fine when I restart gdm.

I thought it might be a problem with the video driver, but that's not the case - if I run [FONT=Lucida Console]zenity --info[/FONT] as root with DISPLAY set correctly, the dialog box appears on the screen just fine. It has no borders or titlebar (there's no windowmanager), and is apparently without keyboard focus, so since there's no visible mouse pointer I can't click the OK button... But since it appears, X is apparently up and running just fine, just has nothing to display other than a black background.

I tried purging and reinstalling gdm and gnome-session(-bin|-common), but that didn't help any.

Running [FONT=Lucida Console]ck-list-sessions[/FONT] after trying to switch indicates that there's a new session there, with [FONT=Lucida Console]session-type = 'LoginWindow'[/FONT], so it appears to think everything's fine.

Enabling debug output in the /etc/gdm/custom.conf file did get me some more debug output in the gdm logs, but it didn't really tell me anything, there weren't any obvious problems that I could see.

After some looking around, I've guessed that it's supposed to be running [FONT=Lucida Console]gdm-simple-greeter[/FONT], which I assume would display a login box; trying to run it manually doesn't work though (it's missing some environment variables, and trying to add them based on the abovementioned debug output doesn't really help).

---

### Post by Krytarik on 2011-01-04
I have a similar behaviour, also at my mum's machine.;-)
The markable difference is that one is able to log out and in. But switching users doesn't work properly either.

When trying to switch user the display gets black the two cursor-style lines left and right at the upper edge. I've found that an additional x-server is running at Alt+Ctrl+F8, but I didn't elaborate further.

I guess it is video card or driver related, that machine has a Radeon 9600XT, running the Open Edge drivers.

I've setup my mum's gdm to a timed autologin generally, may be a workaround in your case.

---

### Post by edorfaus on 2011-01-05
> **Krytarik said:**
> I have a similar behaviour, also at my mum's machine.;-)
The markable difference is that one is able to log out and in.
This sounds like a different issue, since you can log in/out and get something on the screen - mine's completely blank unless I start some program manually, then that program is displayed properly (though still on a blank background, the greeter doesn't appear).

As you mention, yours sounds like a card/driver issue, where it doesn't like to be used more than once at a time or something.

> **Krytarik said:**
> I've setup my mum's gdm to a timed autologin generally, may be a workaround in your case.
Yeah, the (non-timed in my case) autologin works fine, so it's not really critical, but it's still annoying to not be able to easily use my own user account (and if mom accidentally logs out or switches user (aka clicks my name), she'd get a black screen and be stuck... not ideal).

I'll try the timed autologin next time I have a chance, see if that somehow makes it work better.

---

### Post by Krytarik on 2011-01-05
> **edorfaus said:**
> mine's completely blank unless I start some program manually, and then it displays properly.
It may be a Compiz-related problem. Try disabling it:
[http://ptspts.blogspot.com/2010/06/how-to-disable-compiz-fusion-and-enable.html](http://ptspts.blogspot.com/2010/06/how-to-disable-compiz-fusion-and-enable.html)

EDIT: If you use the timed autologin, you don't have to modify the gdm-config each time you want to log in with the respective other user.

EDIT 2: > if I run zenity --info as root with DISPLAY set correctly, the dialog box appears on the screen just fine. It has no borders or titlebar (there's no windowmanager) Another indicator that it's definetely a problem with the window manager, like yourself stated. I didn't attributed it to the new x-server at the first reading, sorry.

---

### Post by edorfaus on 2011-01-05
> **Krytarik said:**
> It may be a Compiz-related problem. Try disabling it:
[http://ptspts.blogspot.com/2010/06/how-to-disable-compiz-fusion-and-enable.html](http://ptspts.blogspot.com/2010/06/how-to-disable-compiz-fusion-and-enable.html)
OK, I'll try that... Disabling it per-user seems a bit late though, when it's the login window that has the problem.

> **Krytarik said:**
> EDIT: If you use the timed autologin, you don't have to modify the gdm-config each time you want to log in with the respective other user.
Well, that assumes that the timed autologin makes it so that the login window actually appears instead of the black screen I get with autologin disabled, but yes, it would. If it makes logout work too, I could probably set the timeout really low to get (close to) the same effect I have now, and just logout to switch user...

> **Krytarik said:**
> EDIT 2:  Another indicator that it's definetely a problem with the window manager, like yourself stated. I didn't attributed it to the new x-server at the first reading, sorry.
Well, I'm not sure if the login window is *supposed* to have a windowmanager running. It might be supposed to manage its own windows for all I know (probably (relatively) easy if there's only one fullscreen window). Heck, for all I know there might actually have *been* a windowmanager there, just one that doesn't draw any window decorations or automatically gives focus to dialog boxes...

I didn't really mean to say that the (assumed) lack of windowmanager was (part of) the problem, I just mentioned it as a datapoint in case someone knew it was supposed to be there (or not, as case may be), to help narrow down the cause/fix.

EDIT: sorry, I just realized that my statement about starting a program manually in the earlier post above was really unclear and easily confusing, I've edited it to be clearer now.

---

### Post by Krytarik on 2011-01-05
To disable Compiz/set Metacity for the GDM login, if that is necessary, add "sudo -u gdm" before the gconftool-2 command:
```
sudo -u gdm gconftool-2 --type=string --set /desktop/gnome/applications/window_manager/current /usr/bin/metacity
sudo -u gdm gconftool-2 --type=string --set /desktop/gnome/applications/window_manager/default /usr/bin/metacity
```At my machine those options aren't set.

EDIT: To check if those options are set, and how:
```
sudo -u gdm gconftool-2 --get /desktop/gnome/applications/window_manager/current
sudo -u gdm gconftool-2 --get /desktop/gnome/applications/window_manager/default
```

---

### Post by Krytarik on 2011-01-05
> **edorfaus said:**
> OK, I'll try that... Disabling it per-user seems a bit late though, when it's the login window that has the problem.
I only got before my previous post that it "only" affects the GDM login screen, regardless how it is called.> **edorfaus said:**
> Well, that assumes that the timed autologin makes it so that the login window actually appears instead of the black screen I get with autologin disabled, but yes, it would. If it makes logout work too, I could probably set the timeout really low to get (close to) the same effect I have now, and just logout to switch user...Thus you also don't see anything in this case.
> **edorfaus said:**
> Well, I'm not sure if the login window is *supposed* to have a windowmanager running. It might be supposed to manage its own windows for all I know (probably (relatively) easy if there's only one fullscreen window). Heck, for all I know there might actually have *been* a windowmanager there, just one that doesn't draw any window decorations or automatically gives focus to dialog boxes...

I didn't really mean to say that the (assumed) lack of windowmanager was (part of) the problem, I just mentioned it as a datapoint in case someone knew it was supposed to be there (or not, as case may be), to help narrow down the cause/fix.
Windows called in the GDM login screen normally have window borders and controls, I've just yet re-checked this. And my test window also got focus automatically.

---

### Post by edorfaus on 2011-01-05
> **Krytarik said:**
> I only got before my previous post that it "only" affects the GDM login screen, regardless how it is called.
Yeah, I was starting to get the feeling this was the case... Thanks for mentioning it, I edited original post to clarify a bit.

> **Krytarik said:**
> Windows called in the GDM login screen normally have window borders and controls, I've just yet re-checked this. And my test window also got focus automatically.
Thank you for testing/confirming this; apparently it's not just the greeter that isn't started like it should be...

---

### Post by edorfaus on 2011-01-05
> **edorfaus said:**
> I'll try the timed autologin next time I have a chance
 > **Krytarik said:**
> Thus you also don't see anything in this  case.
I just tried it, and indeed it doesn't work - I just get the black screen, and the autologin never happens, even when I wait longer than the set timeout.

> **Krytarik said:**
> To disable Compiz/set Metacity for the GDM  login, if that is necessary, add "sudo -u gdm" before the gconftool-2  command:
I tried this, but it didn't help - still just get a blank screen.

> **Krytarik said:**
> It may be a Compiz-related problem. Try disabling it:
I tried doing this too, for all users (including gdm), but it didn't help either, so I just changed it back. I think it probably stops at something else, before it even tries to start the WM.

> **Krytarik said:**
> At my machine those options aren't set.
Same here, so I unset them again when it didn't work, just in case having them set would mess things up further.

Any other ideas?

EDIT: Oooh, I got a mouse pointer! I tried the zenity thing again, this time after just starting gdm (without autologin), and this time the window did have focus. I tried moving the mouse, and this time, the pointer appeared.

Most likely the mouse pointer has always been there, just set to an invisible one, which got reset when the mouse hovered over the text field in zenity (since that uses the bar pointer). It's now an X (the standard X cursor) everywhere else, even over the black background and after clicking OK in zenity.

This just reinforces the fact that there's no windowmanager, as I believe the focus-on-hover behaviour is the default X behaviour in that case. (My previous zenity attempt was probably after moving the mouse away from the center of the screen.)

---

### Post by Krytarik on 2011-01-05
After I searched the web on the matter for the first time, I found some recent threads about similar problems, though it's not clear if they could autologin.

[http://crunchbanglinux.org/forums/post/90455/#p90455](http://crunchbanglinux.org/forums/post/90455/#p90455)
[http://crunchbanglinux.org/forums/post/79358/#p79358](http://crunchbanglinux.org/forums/post/79358/#p79358)

According to those it could indeed be, that it's a problem with the video driver.

Which video card/chip is installed, what drivers are you using?

---

### Post by Krytarik on 2011-01-05
Through another thread regarding GDM options, I stumbled over the "User" and "Group" options of the daemon, check if they are either not set or set correctly in "/etc/gdm/custom.conf":

[http://library.gnome.org/admin/gdm/stable/configuration.html.en#daemonconfig](http://library.gnome.org/admin/gdm/stable/configuration.html.en#daemonconfig)

---

### Post by edorfaus on 2011-01-06
> **Krytarik said:**
> After I searched the web on the matter for the first time, I found some recent threads about similar problems, though it's not clear if they could autologin.

[http://crunchbanglinux.org/forums/post/90455/#p90455](http://crunchbanglinux.org/forums/post/90455/#p90455)
[http://crunchbanglinux.org/forums/post/79358/#p79358](http://crunchbanglinux.org/forums/post/79358/#p79358)

According to those it could indeed be, that it's a problem with the video driver.

Which video card/chip is installed, what drivers are you using?
Those problems look a bit different to me, since my video card apparently works (gnome works normally, and even the login screen can display manually started windows), but I can't really know that they are different, so... Not sure what to try based on the info there though. Any suggestions?

According to both lspci and the Catalyst Control Center, the video card is an ATI Radeon HD 4290 (RS880).

I'm currently using the fglrx (proprietary) driver, I suppose I could try the ati, radeon, and/or vesa drivers just to check if they're any different...

Trying those should be as simple as putting e.g. "vesa" instead of "fglrx" in  the Driver key in the "Device" section in the /etc/X11/xorg.conf file, right? (or maybe I should simply rename/move the file away to make it autodetect again...)

The vesa driver would probably be the safest, right? If it doesn't work with that, it's highly unlikely to be a driver issue?


> **Krytarik said:**
> Through another thread regarding GDM options, I  stumbled over the "User" and "Group" options of the daemon, check if  they are either not set or set correctly in "/etc/gdm/custom.conf":

[http://library.gnome.org/admin/gdm/stable/configuration.html.en#daemonconfig](http://library.gnome.org/admin/gdm/stable/configuration.html.en#daemonconfig)
My custom.conf does not specify User/Group, and the defaults in gdm.schema are "gdm", which is the owner and group of the homedir for the gdm user as specified in /etc/passwd, with mode rwxr-x---.

Just to make things easier, here are the complete contents of my /etc/gdm/custom.conf file:
```

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=edorfaus
TimedLoginEnable=false
TimedLogin=edorfaus
TimedLoginDelay=10
DefaultSession=gnome
```

---

### Post by Krytarik on 2011-01-06
Yeah, just rename the xorg.conf, the open source driver "radeonhd" should be used automatically then. If the behaviour doesn't change after doing that, it's indeed very unlikely that it's a driver issue.

---

### Post by edorfaus on 2011-01-06
:confused: What the... I just tried to logout again, and this time the screen appeared just fine, no problems at all. It also works fine to not have autologin now, the login window appears just fine after a reboot.

The weird thing is - I haven't done anything that should have fixed it, that I'm aware of...
[I][COLOR=Navy]
EDIT: in particular, I didn't get around to trying different drivers yet, I tried to logout first to check that the problem was still there.[/COLOR][/I]

As far as I know, the only things I've done since I tried last was to change my mom's screen saver settings (to random instead of blank, longer idle timeout, and to not require a password - logging in and switching user still requires password though), and to run some updates using Synaptic, but I don't recall anything related in there... The former is highly unlikely to be it (though you never know, what with some other bugs related to the screensaver in the past), the latter though...

*Checks the Synaptic history to make sure*

Hm, ok, maybe I was wrong about there not being anything related - it updated aptdaemon, evince, evolution, some related libraries, ubuntu-sso-client - and gnome-system-tools. The latter two *might* be related (though it doesn't appear that they *should* be, reading the package descriptions)...

Well, I suppose the system tools probably includes the settings window for the login screen, which I've used since the upgrade to change the autologin user... Still seems weird that it would just suddenly start to work though, I seem to remember retesting right after the update...

Of course, it was weird the way it just suddenly stopped to work, too... *scratches head*

Anyway, apparently this problem has been solved, despite me being unsure how. Thank you for all the help trying to diagnose and fix it.

---

### Post by Krytarik on 2011-01-06
I seems that today is gnome-fixes-itself-whithout-any-obvious-related-action-day:
[http://ubuntuforums.org/showthread.php?t=1660675](http://ubuntuforums.org/showthread.php?t=1660675)

Happy, that your issue is fixed (at least for now) though!

---

