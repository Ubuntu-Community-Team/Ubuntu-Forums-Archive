---
title: "System Settings doesn't load"
date: 2009-07-04
forum: General Help
---

### Post by djchallis on 2009-07-04
I had a bit of a poke around the forum but I couldn't find anything quite like this. Sorry if I missed it, please link me.

I'm using Kubuntu (Intrepid, KDE4) and the System Settings won't open. It's been this way since before I upgraded to Intrepid. I didn't bother with it because I figured the upgrade would fix it, but I upgraded to Intrepid and it still doesn't work.

When I click "System Settings" from the Kmenu the bouncy icon next to the mouse appears and System Settings appears on the task manager but after ten seconds or so they give up and vanish.

When I type "systemsettings" into Konsole and run it I get a lot of text that I don't really understand. I can print the entire thing if you like. This line is repeated lots:
> systemsettings(1677) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
At the end of the text is this:
> KCrash: Application 'systemsettings' crashing...
sock_file=/home/djchallis/.kde/socket-djchallis-laptop/kdeinit4__0
<unknown program name>(1676)/: Communication problem with  "systemsettings" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "

Straight after that a Crash Handler pops up. It says this:
"The application System Settings (systemsettings) crashed and caused the signal 11 (SIGSEGV)."
It comes up with no debug symbols and no backtrace.

I don't know if it's relevant, but in the ctrl-esc "System Activity" window there's a process called "nm-system-settings".

That's all the information I can think of off the top of my head. I can find out anything else if I need to.
It's been this way for a long time and I'm slowly cracking. Can anybody help?
Thank you!

---

### Post by djchallis on 2009-07-27
Bump. Can anyone help?

---

