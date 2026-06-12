---
title: "Boot stuck on Ubuntu Studio 11.04"
date: 2011-08-11
forum: General Help
---

### Post by Neraste on 2011-08-11
Hello everyone

Well... It's in the title: my Ubuntu Studio 11.04 on my EeePC 1215 is stuck when booting, all of a sudden, and I can no longer use the GUI.

[LIST]
[*]When I start as usual, the boot stops at the splash screen, with the directions *wait to continue*, *S to skip* and *M for manual* (usually, this screen appears less than 2 seconds). If I press any key nothing happens. The screen doesn't freeze, since the splash animation is playing, but nothing more happens (the HDD led doesn't blink).
[*]When I start in recovery mode, I can boot in command line as root and have access to my session in terminal. If y try to start Xorg, the server launches but is quickly stuck, too: I have hardly an animated cursor on a blank screen and that is all (I can move the cursor and the HDD led is off). Switching to tty1, I have :
```
(WW) fglrx: No matching Device section for instance (BusID PCI:000:1:1) found
```This, several time with different PCI bus ID. If I try to quit Xorg in command line, I am told :
```
waiting for X server to shut down ................
xinit: X server slow to shut down, sending KILL signal
waiting for server to die ...
xinit: X server refuses to die
```I have to wait a while before typing anything.
[/LIST]

Well I have no access to the GUI. What is wrong? Xorg?

The most significant things I have performed last time I used Ubuntu were:

[LIST]
[*]Uninstalling/reinstalling **KDEnlive **and trying to force a **melt **old version installation (removed)
[*]Fixing /apps/gksu/sudo-mode to enabled in **gconf-editor** dialog box.
[/LIST]
I don't think I have done any upgrade: a signature error was occurring when I was trying **apt-get update**.

So, how can I make my Ubuntu to boot? What is the problem? All was working fine up to now and I haven't try any hazardous experiments...

Thank you for your help.

---

### Post by Neraste on 2011-08-11
I tried to boot with Ubuntu Studio today and believe it or not, it is still stuck. But this time, it has shown me the booting log. Here it is, maybe it can help:
```
[...]
* Starting network connection manager                      [fail]
* Stopping network connection manager                      [ OK ]
* Starting configure network device security               [ OK ]
* Starting configure network device                        [ OK ]
* Checking battery state...                                [ OK ]
* Stopping cold plug device                                [ OK ]
* Stopping log initial device creation                     [ OK ]
* Starting load fallback graphics devices                  [ OK ]
* Starting configure virtual network devices               [ OK ]
* Starting configure network device security               [ OK ]
* Starting save undev log and update rules                 [ OK ]
* Stopping configure virtual network devices               [ OK ]
* Starting load fallback graphics devices                  [fail]
* Stopping save undel log and updates rules                [ OK ]
Drive /dev/sdb5 is not ready yet or missing
Continue to wait; or press S to skip mounting or M for manual recovery
* Starting GNOME Display Manager                           [ OK ]
* Starting GNOME Display Manager                           [fail]
* Stopping System V runlevel compatibility                 [ OK ]
* Starting CUPS printing spooler/server                    [ OK ]
```Here, this last step take several time.
```
* Starting Mount network filesystems                       [ OK ]
* Stopping Mount network filesystems                       [ OK ]
* Starting configure network device                        [ OK ]
```Here, the booting is completely stuck.

What is strange is that I don't have any **sdb** device!

If you have any idea of what is happening and any advise to give me. I really don't know what to do now.

---

### Post by Neraste on 2011-08-13
After many investigations, it seems that X had some troubles, perhaps because of too much **apt-get autoclean**, **apt-get clean** and** apt-get autoremove**...

Then, I have re-installed Ubuntu Studio and everything is working fine now.

---

