---
title: "Using FreeNX removes theme settings"
date: 2009-11-25
forum: General Help
---

### Post by Redsandro on 2009-11-25
Hi,

When I log in to my Ubuntu machine using FreeNX, stuff like colors and icons are reset to something basic and grey while the window borders are in the correct style.
How can I force FreeNX to broadcast the correct style/theme?

I found something on this in [this very old topic](http://ubuntuforums.org/showthread.php?t=66024) where someone suggested I should run *gnome-settings-daemon*, but it doesn't work for me. All it does is make **d** a shortcut for desktop, preventing me from typing in any window or terminal.

Any more recent way of fixing things?

---

### Post by t0p on 2009-11-25
Maybe you'll find [this]("http://aaron-kelley.net/blog/2009/08/freenx-on-ubuntu-9-04-jaunty-what-happened-to-my-gnome-theme/") helpful.  Or [this]("http://aaron-kelley.net/blog/2009/08/freenx-on-ubuntu-9-04-jaunty-what-happened-to-my-gnome-theme/").

---

### Post by Redsandro on 2009-11-25
Hey thanks! Now I know where the problem lies.

Unfortunately both solutions don't work for me:
```
**run** gconf-editor
**disable** /apps/gnome_settings_daemon/plugins/keyboard
```
```
**run** gconf-editor
**disable** /apps/gnome_settings_daemon/plugins/mouse
```

Third solution for Ubuntu 9.04:
```
revert **libxklavier** to **3.9-0ubuntu1**
```

I cannot revert that in Ubuntu 9.10

So I guess I cannot fix this until someone fixes the bug in that library.

---

### Post by lz1dsb on 2009-11-30
I also had exactly the same problem and the proposed workaround really works, but there's a catch. After you disable the keyboard plugin, you're no longer able to switch between layouts. The only keyboard layout you can use is US, and you can't switch. Let alone, there's a problem with the keyboard layout indicator when using the Freenx server. It's just not possible to use it... I'll search a bit in the forums and will post a new thread with more details if I don't find anything relevant.

---

### Post by Redsandro on 2009-11-30
Strange how it doesn't work for me. I really disabled them, both in user and in root mode just to be sure. No ball.

If you post a new topic can you please notify of this new topic here?

---

### Post by lz1dsb on 2009-12-01
Did you reload the system after disabling the keyboard plugin from the Gnome config tool? You really need to reload, otherwise there's no effect whatsoever...

Regards, 
Boyan

---

### Post by Redsandro on 2009-12-01
Yes I restarted X by ctrl+alt+backspace.
But since you mentioned, just to be sure I rebooted my server and tried again. Still no style on the windows.

I doublechecked the config, both mouse and keyboard plugins are not active.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=138274&stc=1&d=1259699361[/IMG]

---

### Post by lz1dsb on 2009-12-01
What versions do you use? I use Ubuntu 9.04 and the latest freenx server, compiled for Jaunty. 

Regards, 
Boyan

---

### Post by lz1dsb on 2009-12-01
And btw, I've started a new thread about the keyboard layout problem, when using freenx [http://ubuntuforums.org/showthread.php?t=1342966&highlight=Keyboard+layout+indicator+problem+FreeNX+server](http://ubuntuforums.org/showthread.php?t=1342966&highlight=Keyboard+layout+indicator+problem+FreeNX+server) 
I hope that somebody could shed some light on this...

Regards, 
Boyan

---

### Post by Redsandro on 2009-12-01
Oh! Yeah, no, I thought you use 9.10. Like me. I meantioned it somewhere. :)

> **Redsandro said:**
> Third solution for Ubuntu 9.04:
```
revert **libxklavier** to **3.9-0ubuntu1**
```

I cannot revert that in Ubuntu 9.10

So I guess I cannot fix this until someone fixes the bug in that library.

Misunderstanding. So I guess the conclusion that there is no fix for 9.10 is not too bad after all. :)

---

### Post by The Woozy Fieldmouse on 2011-06-18
Same problem here. I setup FreeNX on my Linux Mint 10 machine, logged in via a Windows machine, but when I logged in locally again, all my color settings were gone. Now it won't take any custom colors whatever. Fail.

---

