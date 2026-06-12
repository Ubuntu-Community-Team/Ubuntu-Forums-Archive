---
title: "I killed wineserver"
date: 2011-05-27
forum: General Help
---

### Post by Zebaas on 2011-05-27
Well, I was having a problem with a game, and someone told me to kill wineserver and steam...He went offline...Now I'm wondering, How do I re-Enable wineserver?
I killed it with
wineserver -k

---

### Post by linuxinstalledfromhdd on 2011-05-27
Reboot your entire system. 

[http://stream-recorder.com/forum/showthread.php?t=4998](http://stream-recorder.com/forum/showthread.php?t=4998)

---

### Post by Zebaas on 2011-05-27
What do you mean By "Reboot your entire system." Restart the PC or...Sorry, I'm new to this.

---

### Post by linuxinstalledfromhdd on 2011-05-27
That should fix it.  It fixes it whenever I lock up my system running Wine games too.

---

### Post by Zebaas on 2011-05-27
I restarted my PC. Nothin'....

---

### Post by linuxinstalledfromhdd on 2011-05-27
Did you restart your application you were running?

---

### Post by linuxonbute on 2011-05-27
start up a terminal and type:

wineserver


This should start wineserver up.

See if you get any error messages. If you do post them so we can see.

If there are no error messages then try running your program.

In any case let us know how you get on.

---

### Post by Zebaas on 2011-05-27
I type wineserver...Nothing Happens...
I run the program, Which was running perfectly before I killed wineserver, and:
"Steam is no longer supported on this computer's operation system"
It also say that with wineboot.exe and When I launch a game from Terminal...

---

### Post by linuxinstalledfromhdd on 2011-05-27
Did you install Steam with PlayOnLinux? 

[http://cinderbox.net/2011/05/23/2856/](http://cinderbox.net/2011/05/23/2856/)

That's the only thing I have ever used to install games.

---

### Post by linuxonbute on 2011-05-27
> **Zebaas said:**
> I type wineserver...Nothing Happens...

Ok then that means that wineserver is not in your path or no longer installed.

From a terminal do 

locate wineserver

If it shows a path to it you can start it up by entering the full path.

for example if locate reports :
/usr/local/bin/wineserver

then typing /usr/local/bin/wineserver
will start it up.
If not then it looks like you need to reinstall it.

---

### Post by Zebaas on 2011-05-27
Found the problem...Well, i fixed it...Something to do with Windows XP and Windows 98...Idk what i did but I fixed it...Good ole Winecfg...

---

