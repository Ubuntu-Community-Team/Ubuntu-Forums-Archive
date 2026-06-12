---
title: "DontVTSwitch doesn't pass through Ctrl-Alt-(Shift)-Fn to applications"
date: 2011-06-10
forum: General Help
---

### Post by pjdorrell on 2011-06-10
I recently upgraded to the latest version of Ubuntu (11.04) on my PC. I'm using the default Confity interface.

I have an application (Emacs) which uses many keyboard shortcuts of the form Ctrl-Alt-Fn or Ctrl-Alt-Shift-Fn.

I have managed to insert this[INDENT] **Section "ServerFlags"**[B]
         Option "DontVTSwitch" "true"[/B]
** EndSection**
[/INDENT]into my /etc/X11/xorg.conf

It partly works: Ctrl-Alt-Fn (with or without shift) no longer invokes virtual terminal n.

But, the Ctrl-Alt-Fn keystrokes don't get fed through to the applications.

An easy way to see this is to go to System Settings => Keyboard Shortcuts and try and define a new shortcut. For example, I can define any one of F5, Shift-F5, Alt-F5, Ctrl-F5, Shift-F5, Ctrl-Shift-F5, Alt-Shift-F5, but not Ctrl-Alt-F5 or Ctrl-Alt-Shift-F5. When I type one of the last two, it just sits there as if I did nothing at all.

I've seen many discussions on the web about disabling Ctrl-Alt-Fn keys, and explanations about DontVTSwitch, but I haven't seen anyone confirm that DontVTSwitch actually passes the desired keystrokes through to their application. Is this a known bug?

Relevant quote from [http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html) : 
**Option "DontVTSwitch"  "***boolean***"** This disallows the use of the **Ctrl+Alt+F***n* sequence (where F*n* refers to one of the numbered function keys).  That sequence is normally used to switch to another "virtual terminal" on operating systems that have this feature.  When this option is enabled, that key sequence has no special meaning and is passed to clients.  Default: off 

Side note: if I really really want to invoke a non-X terminal (for some reason), I can use Alt-SysReq-r etc. I don't want to disable the virtual terminals. I just want to disable how X handles those key combinations, so I can have them in my application.

---

### Post by pjdorrell on 2011-06-13
I think I have found the answer to my own question, which is to also add this to xorg.conf:

```

Section "InputClass"
    Identifier "keyboard defaults"
    MatchIsKeyboard "on"
    Option "XKbOptions" "srvrkeys:none"
EndSection
```The srvrkeys:none option points to a rule +srvr_ctrl(no_srvr_keys) in /usr/share/X11/xkb/rules/evdev which points to a rule in /usr/share/X11/xkb/symbols/srvr_ctrl which suppresses the standard interpretation of the Ctrl-Alt-Fn key strokes.

And you can still do Alt-Sysrq-r and then Ctrl-Alt-Fn to access a console.

It follows that the documentation for the DontVTSwitch option in xorg.conf(5x) is wrong, i.e. that option by itself does not cause events to be "passed to clients". (Maybe some of the other "Dont" options are also incorrectly documented.)

---

### Post by na5m on 2011-06-23
Cool. I was looking for a way to disable breaking out of X, and your **srvrkeys:none** trick worked like a charm :)

---

