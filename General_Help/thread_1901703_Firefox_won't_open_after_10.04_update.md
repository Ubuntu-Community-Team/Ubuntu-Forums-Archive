---
title: "Firefox won't open after 10.04 update"
date: 2011-12-29
forum: General Help
---

### Post by houseworkshy on 2011-12-29
As in the title.  Firefox did work on first being installed even after adding no-script, better privacy, add to search bar, and downthemall.  I also put in the none free flash player for it.  It stopped working after an update yesterday. It had been working fine for a few weeks until then.   As far as I rememember  I took all the important security updates and declined the recomended updated which included something to do with weather.  Usually I disable the recomended updates but hadn't got round to it yet as this install is fairly recent and it's been Christmas etc.  I have no extra repositories installed.
On trying to open firefox either via the Applications menu or the icon on the top bar the cursor does the spinning "I'm trying to do something" bit and the firefox tab appears on the lower bar then the tab disapears and the cursor returns to the pointer mode.
So I then totally removed firefox via synaptic and reinstalled it, this caused a repeate of the the above fail to open.
Then I put in seamonkey which, oddly as it is also mozilla, works fine and I'm using it to post this.  So the bug is not utterly critical for me though I'd rather use firefox as it is easier to add search engines via the add to search bar.  It is also the default browser on a fresh install of Ubuntu so if this bug is general it's bit of a problem.
Whilst  uninstalling firefox I noticed that the libweather ect stuff which I'd declined during the update was there anyway ( could have come in earlier, not sure ).  Thinking it may have something to do with it I tried to uninstall that too but it wanted to remove gnome-panels the applets, everything to do with evolution and even the gnome desktop so I didn't.
Another thing I noted was that for a week or so video has been stalling visually ( sound keeps running ), this is a persistant fault which seems to develop a week or two after any fresh install of Ubuntu 10.04 on my machine irrespective of what I do, this is common to vlc, totem and flash.
 
The latter fault is one I have banged my head against for some time and is only mentioned in case it helps to diagnose the firefox problem, I only use ubuntu as a video player for however long it lasts after a fresh install and then simply use puppy if I want to watch films.

---

### Post by lovinglinux on 2011-12-31
Start Firefox in safe mode from terminal:

```
firefox -safe-mode
```

If it starts, then you most likely have an add-on issue. I would start by disabling Global Menu Bar Integration extension.

If it doesn't start, try a clean profile. You can create new profiles with the profile manager.

```
firefox -P
```

Please report any errors you get on the terminal.

---

### Post by houseworkshy on 2012-01-02
Thanks for the reply.  I have reinstalled firefox and realised that when I removed it the last couple of times I hadn't removed the mozzilla folder, an ommission I blame on seasonal festivities.  This was very clear as add-ons from my previous installations were present in the fresh one ( you were right about profiles ).  

The way I installed it this time was to follow the advice from this sticky post   [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247) which I'd missed when searching earlier, I added the mozillateam/firefox-stable ppa and went from there.  Now it all seems to work.  So it's  likely that the problem was the firefox versions compatability with Lucid.  I'll use it for a few days, browse youtube etc, and if all continues to work will mark this as solved.

Thanks again for your help and have a happy new year.

---

### Post by houseworkshy on 2012-02-07
It all still works so I'll mark this as solved.  As an aside my sticky video problem also went away, which was a peculiar ( if not just coincidencial why would firefox mess up totem and vlcs offline functionality? ) but welcome bonus.

---

