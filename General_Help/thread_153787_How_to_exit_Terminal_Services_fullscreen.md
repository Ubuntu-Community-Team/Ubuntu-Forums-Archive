---
title: "How to exit Terminal Services fullscreen??"
date: 2006-04-01
forum: General Help
---

### Post by gen0 on 2006-04-01
Is there a key-combination or some way to exit a Windows Terminal Services session in fullscreen-mode, *without* logging off from the remote server?

I am using the Terminal Services Client in Ubuntu Breezy 5.10

Thanks for any suggestions...

---

### Post by souki on 2006-04-01
exit the full screen mode with Ctrl-Alt-Enter
annd close the window

---

### Post by gen0 on 2006-04-02
Thanks!

---

### Post by JimTDI on 2006-11-07
> **souki said:**
> exit the full screen mode with Ctrl-Alt-Enter
annd close the window

Wow - thanks!  That helps alot!!  I had the same question.  This Ubuntu community is awesome!!! :)

---

### Post by kangarolf on 2006-12-20
Hi there,

Ive tried to use Ctrl-Alt-Ent to exit full screen mode but all that happens is the desktop flashes on screen briefly and then goes back to the full screen terminal services window.

Any help appreciated...its hard work in this little window to manage these servers!

---

### Post by marcantonio on 2006-12-20
Ever since upgrading to edgy I've had the same problem.

---

### Post by zigx on 2007-07-17
im on fiesty and ctrl+alt+enter works Perfectly, thank you for this thread!l

---

### Post by Strawp on 2007-10-30
> **kangarolf said:**
> Hi there,

Ive tried to use Ctrl-Alt-Ent to exit full screen mode but all that happens is the desktop flashes on screen briefly and then goes back to the full screen terminal services window.

Any help appreciated...its hard work in this little window to manage these servers!

I had this problem and it was driving me nuts. I'm in Gutsy and I've just found out how to fix it - in the connection settings window, go to the "Performance" tab and make sure the "attach to console" and "allow window manager key bindings" options are checked. 

I'm now able to use ctrl+alt+enter (which still doesn't work) but then ctrl+alt+left/right works to switch desktop, which is all I needed. You can even initiate desktop cube and have windows on one face and GNOME on another, which is too cool :D

---

### Post by ColdFusionEESG on 2007-11-28
> **Strawp said:**
> I had this problem and it was driving me nuts. I'm in Gutsy and I've just found out how to fix it - in the connection settings window, go to the "Performance" tab and make sure the "attach to console" and "allow window manager key bindings" options are checked. 

I'm now able to use ctrl+alt+enter (which still doesn't work) but then ctrl+alt+left/right works to switch desktop, which is all I needed. You can even initiate desktop cube and have windows on one face and GNOME on another, which is too cool :D

Great....thanks Strawp....not a perfect fix, but works well enough ;-)

Just a  quick note that you will/may need to use CTRL+ALT+ENTER before you can swap desktops the first time using CTRL+ALT+LEFT/RIGHT....after that you are good to go.

Cheers

---

### Post by ethoms on 2007-12-12
Well I'm using 7.10 (Gutsy Gibbon), all updates applied and I can't get out of terminal fullscreen without logging out. Ctrl-Alt-Enter doesn't seem to do anything, even with "attach to console" and "allow window manager key bindings" checked. When I do Ctrl-Alt-Left/Right it switches between my Solaris 10 (vnc server) workspaces and not the Ubuntu one. It may work for you guys coz your connecting to Windows, which has no workspace switching.

By the way, I'm bran spanking new to Ubuntu, Love at first site. Congrats to everyone involved, this is without doubt in my mind the best OS for desktops / laptops, just what the world has been waiting for. I'm so close to completely ditching windows.... forever. :KS

---

### Post by ColdFusionEESG on 2007-12-12
hmmmm...well I'm still fairly new to Ubuntu, but there is a place to edit shortcut keys.  So perhaps changing which keys are used to switch between Ubuntu desktops could get it going (as I assume Solaris is using the same key combo of CTRL+ALT+left/right).

Good luck

....and I WILL be dropping Windows now that I have Unreal 2004 running on Ubuntu (and all my work and other stuff....but the game was the last thing that required Windows).  Of course I have VirtualBox running Win XP SP2 just in case ;-)

Cheers

---

### Post by ethoms on 2007-12-14
I changed keyboard shortcuts in System->Preferences->Keyboard Shortcuts. Made no difference to my Solaris VNC remote session. I noticed the Ctrl-Alt-Enter works really well in RDPv5. It must be a Solaris VNC and Ubuntu terminal services compatibility issue.

Anyways, my Solaris is so fast to logon / logoff and it's perhaps best to close the session properly by logging off. Solaris VNC has multi-session desktoping via http in browser, way, way cool. I have set up 12 sessions, six at 16bit color depth and six at 8bit, each with different resolutions. So if bandwidth is scarce I can logon at 800x600 or even 640x480.

:)

---

### Post by philws on 2008-01-29
Sadly I have the same problem as ethoms (i.e. can't find any key combination to exit full screen mode) when connecting from 7.10 Terminal Server Client full screen mode to a VNC server running on Fedora Core 3... any ideas?

---

### Post by SilverWave on 2008-02-02
Got The Fix Here:
[http://www.steveneppler.com/blog/200...n-and-tsclient](http://www.steveneppler.com/blog/200...n-and-tsclient)

1. Press ctrl-alt-enter, then QUICKLY press ctrl-alt-(arrow left or right).
>>>Took me a bit of messing around but it finaly got me out

2.Check your COMPIZ plugins for - “Workarounds” Check settings of this plugin for:
> Legacy Fullscreen support
If enabled disable it.
Fullscreen in rdesktop then works properly eg “CTRL ALT ENTER” works.

Class!

Thanks Everyone.

---

### Post by kon5ad on 2008-02-04
Hey Silver...

That worked for me with Gutsy Gibbon. Thanks a lot.

---

### Post by Maarten78 on 2008-02-06
> **Strawp said:**
> 
I'm now able to use ctrl+alt+enter (which still doesn't work) but then ctrl+alt+left/right works to switch desktop, which is all I needed. You can even initiate desktop cube and have windows on one face and GNOME on another, which is too cool :D

GREAT!!!!

Yes, I had the same option. I even opened a new post. But I didnt got any reply on that, but checking this post AGAIN :( you saw this again, And tried again, i works for me! THANKS alot.

Greetz,
Maarten.

---

### Post by philws on 2008-04-25
> **ethoms said:**
> ... all updates applied and I can't get out of terminal fullscreen without logging out. Ctrl-Alt-Enter doesn't seem to do anything, even with "attach to console" and "allow window manager key bindings" checked. ... It may work for you guys coz your connecting to Windows, which has no workspace switching.

I second this... I'm also connecting to a non-Windows (in fact another Ubuntu) box and simply can't get this to work.

Phil :(

---

### Post by thooran on 2008-05-01
If you are using VNC to connect via terminal service, then perhaps try hitting F8 key to exit full screen.

---

### Post by boywithcar on 2008-05-01
FYI
I am using Hardy Heron and connecting to remote desktop of Windows Xp.
If you set both "Attach to console" and "Enable window manager's key bindings" in the "Performance" tap, "Ctrl + Alt + Enter" could help you change the mode of the "Terminal Server Client". Although it still has the focus after applying "Ctrl + Alt + Enter", you could either use "Ctrl + Alt + Left/Right" to switch the workspace or use "Alt + Space" to pop down a menu of "Terminal Server Client", where you could choose "Minimize".



> **gen0 said:**
> Is there a key-combination or some way to exit a Windows Terminal Services session in fullscreen-mode, *without* logging off from the remote server?

I am using the Terminal Services Client in Ubuntu Breezy 5.10

Thanks for any suggestions...

---

### Post by grozni on 2008-06-13
> **SilverWave said:**
> Got The Fix Here:
[http://www.steveneppler.com/blog/200...n-and-tsclient](http://www.steveneppler.com/blog/200...n-and-tsclient)

1. Press ctrl-alt-enter, then QUICKLY press ctrl-alt-(arrow left or right).
>>>Took me a bit of messing around but it finaly got me out

2.Check your COMPIZ plugins for - “Workarounds” Check settings of this plugin for:
> Legacy Fullscreen support
If enabled disable it.
Fullscreen in rdesktop then works properly eg “CTRL ALT ENTER” works.

Class!

Thanks Everyone.



Thanks for this!!!

---

### Post by dwu on 2008-06-18
The terminal server client is "always on top" for me even if I was able to switch to another virtual desktop using the tricks mentioned above.  It doesn't work :(

I eventually use the "Use specified screen size" in the display tab, choose a resolution which is slightly shorter than my screen vertical size (for 1280x1024, I chose 1280x960" and "Hide window manager's decorations".  This works very will.

It is still like in full screen mode but you have access to top/bottom panel to switch to other applications or virtual desktop.

---

