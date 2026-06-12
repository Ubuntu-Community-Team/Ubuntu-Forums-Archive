---
title: "Sidebar disappeared"
date: 2011-11-18
forum: General Help
---

### Post by Cavid on 2011-11-18
Hello, I am new to Ubuntu (and Linux too). Downloaded yesterday, and really really loved it. But then I don't know what I did(I think i was somewhere in CompizConfiguration) and sidebar and everything dissappeared. Now my desktop look like this:

[http://imageshack.us/photo/my-images/171/screenshotat20111118173.png/](http://imageshack.us/photo/my-images/171/screenshotat20111118173.png/)

I logged out, and then logged in with Ubuntu 2d this time, there was a sidebar, but the signs on the top left panel (desktop and etc) were not there. View in Ubuntu 2d:

[http://imageshack.us/photo/my-images/846/screenshotat20111118175.png/](http://imageshack.us/photo/my-images/846/screenshotat20111118175.png/)

Pls help me to get everything as was.

P.s What is the difference between Ubuntu and Ubuntu 2d?


Thank in advance

---

### Post by BillyBoa on 2011-11-18
I think you need to reset Unity (the side bar)

CTRL+ALT+T opens a terminal and write

```
unity --reset
```

Unity 2d is for video cards without graphics acceleration.

---

### Post by elliotn on 2011-11-18
I had the same problem before, but luckly I have Cairo dock running with the terminal launcher in it so I just start terminal and run unity 

then I reset compiz.

2d has no bling bling while ubuntu 3d unity has all the bling effects

---

### Post by Cavid on 2011-11-18
Thank for quick answer, but it didn't work. After I typed message followings appeared


unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done

---

### Post by bbrg548 on 2011-11-18
Caveat: a) I'm assuming you're correct about this being caused by something you did in CompizConfig, b) I'm assuming that simply restarting Compiz won't fix it, since you've rebooted the computer already, and c) be aware that I'm working from memory since I'm not currently at my home system to verify anything.

In Unity (not Unity 2D), there should be a "terminal" option in one of those menus at the top - I believe it's the "Go" menu. Select that and you should get a terminal window.

Step 1: In the terminal, type ```
compiz --reset &
``` That should reset Compiz to the default settings. If that brings back your desktop, then go to Step 5, if not then continue on.

Step 2: If the terminal didn't go to the regular prompt (i.e. "user@computer:", hit "Ctrl+c" to exit the waiting command and get back to the regular prompt, then type ```
unity --replace &
``` to restart the Unity interface. 

Step 3: If you still have no Unity, get back to the regular prompt and type ```
sudo reboot
``` to reboot the computer, which may be needed to get things back to normal.

Step 4: If that doesn't work, you may need to also reset Unity to the default settings. Again in a terminal, type ```
unity --reset &
```. Reboot again if necessary.

Step 5: If you get your desktop back and the terminal goes to the regular prompt (i.e. "user@computer:", use "Ctrl+d" to close it and you should be good to go. If not, use "Ctrl+c" to get back to the prompt, first. 

I've found that for some reason, even though you used the "&" option, closing the terminal by clicking on the "x" button in these situations seems to bork the system again (although at that point a simple reboot usually fixes it).

I hope that helps!

---

### Post by Frogs Hair on 2011-11-18
Do you get a massage when you attempt to close the terminal that a process or job is still running ?

---

### Post by Cavid on 2011-11-18
@bbrg548
The step from 2 and on didn't help, unfortunately.
And when I entered compiz --reset & I get this message


cavid@cavid-Satellite-L300:~$ compiz --reset &
[1] 2147
cavid@cavid-Satellite-L300:~$ compiz (core) - Warn: Unknown option '--reset'

---

### Post by BillyBoa on 2011-11-18
> **Cavid said:**
> @bbrg548
The step from 2 and on didn't help, unfortunately.
And when I entered compiz --reset & I get this message


cavid@cavid-Satellite-L300:~$ compiz --reset &
[1] 2147
cavid@cavid-Satellite-L300:~$ compiz (core) - Warn: Unknown option '--reset'

The way to reset Compiz is

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

but it's a last resource movement

---

### Post by bbrg548 on 2011-11-18
> **BillyBoa said:**
> The way to reset Compiz is

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

but it's a last resource movement

Thanks for the correction! :D Like I said, I was doing this from memory.

Cavid: Try again with the above command in Step 1 in place of what I had. Steps 2 and on weren't likely to work without resetting Compiz first, if it's a Compiz issue like it appears to be.

Edit: The "unity --reset" is a separate step - you can keep that as Step 4. So Step 1 should be ```
gconftool-2 --recursive-unset /apps/compiz-1 &
```

---

### Post by Cavid on 2011-11-18
Nope, doesn't seem to work either. I got this message and nothing appeared:

cavid@cavid-Satellite-L300:~$ gconftool-2 --recursive-unset /apps/compiz-1 &
[1] 2124
cavid@cavid-Satellite-L300:~$

---

### Post by Cavid on 2011-11-18
At last worked!!
For others who have same problem see:

[http://www.tuxgarage.com/2011/04/mis...-in-unity.html](http://www.tuxgarage.com/2011/04/mis...-in-unity.html)

I think for me it helped after this command

rm ~/.config/compiz-1/compizconfig/config

Thank everyone!!:)

---

### Post by bobardu on 2011-11-18
> **Cavid said:**
> At last worked!!
For others who have same problem see:

[http://www.tuxgarage.com/2011/04/mis...-in-unity.html](http://www.tuxgarage.com/2011/04/mis...-in-unity.html)

I think for me it helped after this command

rm ~/.config/compiz-1/compizconfig/config

Thank everyone!!:)

Cavid,
I am having the same problem, but have not been able to reset unity.  Could you please provide the whole url that you listed above?  I can't seem to find that particular site. Thanks!

---

