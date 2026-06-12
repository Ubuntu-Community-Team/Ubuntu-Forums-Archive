---
title: "Help with Compiz Please"
date: 2009-08-02
forum: General Help
---

### Post by l-x-l on 2009-08-02
Hi all,

I've been having this problem with Compiz that I can't figure out. Whenever I put my laptop to sleep then we awaken my laptop, if I do Alt+Ctrl+Downbtn to get the film strip there are black & white alternating strips on my screen. Otherwise Compiz works great. Logging out fixes the problem. But this has become one annoying papercut for me.

I wish there was a way to take a screen shot when doing a Compiz filmstrip to show you the problem but I haven't figured out how to do that. Can anyone help?

BTW I'm on Jaunty & using NVidia driver v180.

Edit: I incorrectly labeled this under Kubuntu but I have Ubuntu with Gnome.

---

### Post by l-x-l on 2009-08-03
bump...

---

### Post by Zorael on 2009-08-04
That sounds very driver-related (Nvidia).

Not knowing what's really causing it, one workaround that *might* work is to reload Compiz after you resume. If that compiz tray icon still exists, I believe there is a "Reload window manager" option in its context menu.

Else, you could create a launcher that runs '**compiz --replace**', alternatively let a script do it;
```
#!/bin/bash

compiz --replace &
```
Save it someplace (desktop?) and make it executable.

---

### Post by l-x-l on 2009-08-04
> **Zorael said:**
> That sounds very driver-related (Nvidia).

Not knowing what's really causing it, one workaround that *might* work is to reload Compiz after you resume. If that compiz tray icon still exists, I believe there is a "Reload window manager" option in its context menu.

Else, you could create a launcher that runs '**compiz --replace**', alternatively let a script do it;
```
#!/bin/bash

compiz --replace &
```
Save it someplace (desktop?) and make it executable.

Thx. Compiz --replace saves me from having to log out then back in to fix the problem. Is there a way to have you script that runs only after awaking from suspend?

---

### Post by Zorael on 2009-08-04
Technically it should be possible to create a script in **/etc/acpi/resume.d/**, yes. It'd have to check if Compiz is already running, and if so, restart it with --replace. My bash-fu is too weak to write something like that with confidence, but looking at **90-screensaver.sh** in that directory, shouldn't something like the following be possible?
```
#!/bin/sh

compizpids=($pidof compiz)

if [ "$compizpids" ]; then
	for x in /tmp/.X11-unix/*; do
		[COLOR="Red"]displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`[/COLOR]
		getXuser;
		if [ x"$XAUTHORITY" != x"" ]; then
			export DISPLAY=":$displaynum"
			if [ "$(ps u $compizpids | grep compiz | grep $user)" ]; then
				[COLOR="DimGray"]# must be launched as a child process, else the script won't keep iterating for other X displays[/COLOR]
				su $user -c "(compiz --replace **[COLOR="Lime"]&[/COLOR]**)"
			fi
		fi
	done
fi
```
I don't know **sed** so I don't know if the **displaynum=** line works at all. But seeing as it allegedly works for 90-xscreensaver.sh (which we basically copy/pasted the entirety of and just did minor changes to), I don't see why it shouldn't do the trick here as well.

As for naming it, I'm not sure about the priority number; should it run before the screensaver dialog pops up? **87-restartcompiz.sh**? Don't forget to set it to exectuable.

Perhaps find someone on IRC (#ubuntu on irc.freenode.net) to give it a proper look.

---

