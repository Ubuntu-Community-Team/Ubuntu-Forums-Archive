---
title: "Startup Script Sleep Gnome-Do?"
date: 2009-12-14
forum: General Help
---

### Post by TurtleKing on 2009-12-14
I had the problem before with gnome-do starting up before Compiz and this caused Docky to not work properly. This got so bad to the point where Docky disappeared from the Ubuntu 9.10 entirely (Tried searching and could not find it). I read from a bug report some where that the solution is to creating a startup script to put gnome-do to sleep for 10 seconds giving Compiz enough time to startup properly. My big question is how do I make this script and where or how do I add it to Gnome-do?

---

### Post by TurtleKing on 2009-12-14
hmm I am sure somebody here in the forums knows how to develop a script.

---

### Post by TurtleKing on 2009-12-14
please somebody answer my question I had to uninstall due to horrible freezes and crashes Ubuntu 9.10 and Linux from my driver because of not making this script with Gnome-do. I managed to reinstall Ubuntu and Linux and just wanna move on to learn new stuff on Ubuntu, but I need to fix this problem before it goes as bad as it did on the first installation.

---

### Post by josephellengar on 2009-12-14
In your startup programs you can put somehting that says:
```

sh -s 'pkill gnome-do && sleep 15 && gnome-do'

```
or the like.  I'm not in front of my computer right now so I don't know the exact command for gnome-do but what you're doing is you can't remove gnome-do from your gnome-panel, as you would lose your settings so on boot you kill it, then wait for compiz to start, then start it again.  If you are willing to use a lot of resources on boot you could also delay compiz so that it starts during that 15 or whatever seconds.

---

### Post by TurtleKing on 2009-12-14
okay I will try and see if this works

---

### Post by TurtleKing on 2009-12-14
this is worst now I can't not even use gnome-do at all.:(

---

### Post by TurtleKing on 2009-12-14
Somebody please help, now Gnome-do will not open at all even though the program is in applications> Accessories. How am I suppose to even use docky now when I can even get open gnome-do appearance?:(

This is what it the file looks like:
#!/bin/sh

SCRIPT_PATH=`dirname $0`
SCRIPT_PATH=`cd $SCRIPT_PATH; pwd`

if [ "x$SCRIPT_PATH" = "x/build/buildd/gnome-do-0.8.2+dfsg/Do/bin/Debug" ] ||
   [ "x$SCRIPT_PATH" = "x/build/buildd/gnome-do-0.8.2+dfsg/Do" ] ; then
    echo "*** Running uninstalled ***"
    GNOME_DO_EXE="/build/buildd/gnome-do-0.8.2+dfsg/Do/bin/Debug/Do.exe"
else
    GNOME_DO_EXE="/usr/lib/gnome-do/Do.exe"
fi

# Send the dbus Summon signal right away for fastest response if
# Do is already running.
dbus-send --session --type=method_call --dest='org.gnome.Do' \
	'/org/gnome/Do/Controller' 'org.gnome.Do.Controller.Summon'

# If Do is not running, run it.
if pgrep -u "`id -un`" '^gnome-do$' >/dev/null; then
	/usr/bin/cli "$GNOME_DO_EXE" "$@"
fi
while [ "$?" -eq "20" ]; do
	/usr/bin/cli "$GNOME_DO_EXE" "$@"

---

### Post by josephellengar on 2009-12-14
> **TurtleKing said:**
> Somebody please help, now Gnome-do will not open at all even though the program is in applications> Accessories. How am I suppose to even use docky now when I can even get open gnome-do appearance?:(

This is what it the file looks like:
#!/bin/sh

SCRIPT_PATH=`dirname $0`
SCRIPT_PATH=`cd $SCRIPT_PATH; pwd`

if [ "x$SCRIPT_PATH" = "x/build/buildd/gnome-do-0.8.2+dfsg/Do/bin/Debug" ] ||
   [ "x$SCRIPT_PATH" = "x/build/buildd/gnome-do-0.8.2+dfsg/Do" ] ; then
    echo "*** Running uninstalled ***"
    GNOME_DO_EXE="/build/buildd/gnome-do-0.8.2+dfsg/Do/bin/Debug/Do.exe"
else
    GNOME_DO_EXE="/usr/lib/gnome-do/Do.exe"
fi

# Send the dbus Summon signal right away for fastest response if
# Do is already running.
dbus-send --session --type=method_call --dest='org.gnome.Do' \
	'/org/gnome/Do/Controller' 'org.gnome.Do.Controller.Summon'

# If Do is not running, run it.
if pgrep -u "`id -un`" '^gnome-do$' >/dev/null; then
	/usr/bin/cli "$GNOME_DO_EXE" "$@"
fi
while [ "$?" -eq "20" ]; do
	/usr/bin/cli "$GNOME_DO_EXE" "$@"

sorry, in what I wrote above it was supposed to be "sh -c" (without quotes), not sh -s.  And again, I am not an expert, just repeating what other people told me when I had similar problems.  But I'll try to help you figure this out.

---

### Post by TurtleKing on 2009-12-14
I tried the command again with sh-c this time and still gnome-do will not open at all.:(

---

### Post by josephellengar on 2009-12-14
> **TurtleKing said:**
> I tried the command again with sh-c this time and still gnome-do will not open at all.:(

Okay, I'll try one more time:

```

sh -c "sleep 10 && gnome-do"

```

Maybe doing it without the pkill will work.  After this I'm out of ideas.  Sorry.

---

### Post by TurtleKing on 2009-12-14
I tried it still no good. Screw Gnome-do I am not doing another reinstallation of Ubuntu 9.10 for this stupid picky program. Do you know if there is an alternative program that gives you the docky feature from Gnome-do?

---

### Post by tom.swartz07 on 2009-12-15
> **TurtleKing said:**
> I tried it still no good. Screw Gnome-do I am not doing another reinstallation of Ubuntu 9.10 for this stupid picky program. Do you know if there is an alternative program that gives you the docky feature from Gnome-do?

pretty much all of the dock programs need compiz to run, but if i had to pick, try AWN, its available in the software center- avant window navigator.

its really low resource, has a ton of little applets, and will be updated soon (im on the dev-release, so i get to sneak peek at the new version- youll like it im sure)

Ill look into the sleep command for you and post back in a minute or two

---

### Post by tom.swartz07 on 2009-12-15
ok- got your answer for gnome do.

open gedit text editor and type this.

```
#!/bin/bash
sleep 50 && gnome-do;
```

save it in your home folder as ".gnome-do-start.sh" (no quotes)

in your startup applications, remove the gnome do entry and do the following.

1. add new, pick a name - :gnome-do?:
2. in the command, click browse and select the .gnome-do-start.sh file
3. add a comment if you please

when you open gnome do, (if you cant see it, try pressing win key + spacebar) and go into preferences. uncheck the option to open it at startup, and make sure that your appearance is set to docky. sometimes it resets to the standard gnome do popup, but you could recover it with win key and spacebar.

Hopefully this helps!

---

### Post by TurtleKing on 2009-12-15
man I wish I had been more patient and not reinstalled ubuntu 9.10 yesterday. I have gnome-do docky feature working since I reinstalled and did not install simple compiz config manager. Now I tried your sleep command and hopefully next time computer restarts it will work. And if I go back to square 1 I will try that program you menitoned. Thanks a bunch now I focus more on learning new stuff about Ubuntu rather than fixing.:)

---

### Post by josephellengar on 2009-12-15
> **tom.swartz07 said:**
> ok- got your answer for gnome do.

open gedit text editor and type this.

```
#!/bin/bash
sleep 50 && gnome-do;
```

save it in your home folder as ".gnome-do-start.sh" (no quotes)

in your startup applications, remove the gnome do entry and do the following.

1. add new, pick a name - :gnome-do?:
2. in the command, click browse and select the .gnome-do-start.sh file
3. add a comment if you please

when you open gnome do, (if you cant see it, try pressing win key + spacebar) and go into preferences. uncheck the option to open it at startup, and make sure that your appearance is set to docky. sometimes it resets to the standard gnome do popup, but you could recover it with win key and spacebar.

Hopefully this helps!

Isn't that exactly the same command that I suggested above (except using bash instead of sh)?

---

### Post by TurtleKing on 2009-12-15
I believe not since this time it worked. I can now use Compiz and Gnome-do (with Gnome-Do delay of course) working together.

---

### Post by tom.swartz07 on 2009-12-16
> **rossholley said:**
> Isn't that exactly the same command that I suggested above (except using bash instead of sh)?

pretty much, yeah. 
Ive found through experimentation that using a simple bash script to run the program is 99.9 times out of 100 better than using sh commands with the startup manager.

---

### Post by stinkeye on 2009-12-16
Try this script which won't start gnome-do until compiz has loaded.
Don't worry about the wmctrl part of the post.
[_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=8376643&postcount=9[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=8376643&postcount=9")

---

