---
title: "Pause music on suspend?"
date: 2009-11-12
forum: General Help
---

### Post by mlissner on 2009-11-12
Hi, does anybody know how to pause music on suspend? I've found that I can put scripts into /etc/pm/sleep.d, and I think they're run on suspend, but I can't seem to get things to work properly.

I also know that banshee --pause will pause banshee (my music player of choice). But putting that in a simple script in /etc/pm/sleep.d/66_pause_music doesn't work.

I'm fairly experienced with scripting, but I think the script is getting run as root, and that it's not working as a result.

Does anybody have any thoughts that might help?

---

### Post by mlissner on 2009-11-24
I'm still playing with this, and I still can't get it to work. Anybody have any ideas? I'm also trying things like:

```
amixer set Master mute
```

But that's not working either.

---

### Post by Darael on 2009-11-24
Well, sudo is configured by fault to let root not use a password, and the -u option lets you specify a user to run as, so you could make the script run "sudo -u [your-username] banshee --pause"?

---

### Post by mlissner on 2009-11-24
Well, the script ran (because it echoed to a log), but pausing banshee still didn't work. When I ran it by suspending, it seemed to do nothing, and when I ran it by hand, the script started another instance of Banshee.

That's why I am now trying the amixer approach, but that seems to fail for some reason.

---

### Post by krelverehan on 2012-05-25
> **Darael said:**
> Well, sudo is configured by fault to let root not use a password, and the -u option lets you specify a user to run as, so you could make the script run "sudo -u [your-username] banshee --pause"?

Thanks Darael for the "sudo -u" tip!

I had no problem stopping my Quodlibet player by creating a file:

```
$sudo gedit /etc/pm/sleep.d/pause_music_suspend
```

Entering in the text into the file and replacing "krel" with your $USERNAME and replacing "quoblibet --pause" with whatever the pause command  is for your music player (or any other command for that manner).

```
#!/bin/sh

# Action script ensure that music pauses 
# before a hibernate or suspend


     sudo -u krel quodlibet --pause
     exit 0

```

Close and save and don't forget to mark it as executable!

```
$sudo chmod +x /etc/pm/sleep.d/pause_music_suspend
```

You should be ready to rock and roll. You can view errors happening during a suspension on the log:

```
$gedit /var/log/pm-suspend.log
```

Cool stuff,
-Krel

---

