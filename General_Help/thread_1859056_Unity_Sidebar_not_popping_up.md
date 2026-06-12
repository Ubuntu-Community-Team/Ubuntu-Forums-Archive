---
title: "Unity Sidebar not popping up"
date: 2011-10-13
forum: General Help
---

### Post by Ertai87 on 2011-10-13
I've just upgraded from Ubuntu 11.04 to 11.10, and I'm having a bit of a problem with the Unity sidebar.  Previously, if I used an application in fullscreen, such as Firefox, and I moved my mouse cursor over to the left of my screen, the Unity sidebar would pop up and I could easily switch applications.  It seems that 11.10 has lost that functionality, unless I've managed to bugger something up.  How do I regain this functionality?  I don't want to have to minimize the window every time I switch apps.

Thanks.

---

### Post by phibxr on 2011-10-13
> **Ertai87 said:**
> I've just upgraded from Ubuntu 11.04 to 11.10, and I'm having a bit of a problem with the Unity sidebar.  Previously, if I used an application in fullscreen, such as Firefox, and I moved my mouse cursor over to the left of my screen, the Unity sidebar would pop up and I could easily switch applications.  It seems that 11.10 has lost that functionality, unless I've managed to bugger something up.  How do I regain this functionality?  I don't want to have to minimize the window every time I switch apps.

Thanks.

Try running the following in a terminal:

```
$ compiz --replace &
```

Fixed it for me.

---

### Post by Ertai87 on 2011-10-13
> **phibxr said:**
> Try running the following in a terminal:

```
$ compiz --replace &
```

Fixed it for me.

Yup, that did it.  Now, will I have to do that on every boot or should it be fixed for good now?

---

### Post by phibxr on 2011-10-13
> **Ertai87 said:**
> Yup, that did it.  Now, will I have to do that on every boot or should it be fixed for good now?

I checked it, and I have to do it at every login after the updates earlier today.

---

### Post by Ertai87 on 2011-10-13
> **phibxr said:**
> I checked it, and I have to do it at every login after the updates earlier today.

Dislike.  Oh well, better than nothing.  Hopefully they'll get it in a future update, sooner rather than later.  Can this be filed as a bug report somehow?

---

### Post by phibxr on 2011-10-13
> **Ertai87 said:**
> Dislike.  Oh well, better than nothing.  Hopefully they'll get it in a future update, sooner rather than later.  Can this be filed as a bug report somehow?

I think the bug should be filed here: [https://bugs.launchpad.net/unity/+filebug](https://bugs.launchpad.net/unity/+filebug)

Been browsing around to see if it's reported yet, but I haven't been able to find anything yet.

---

### Post by effenberg0x0 on 2011-10-13
Have you tried:
```

unity --reset
sudo service lightdm restart

```
select Ubuntu Session (not 2d)

Regards,
Effenberg

---

### Post by phibxr on 2011-10-14
> **effenberg0x0 said:**
> Have you tried:
```

unity --reset
sudo service lightdm restart

```
select Ubuntu Session (not 2d)

Regards,
Effenberg

The issue is still here after several reboots and only appeared after those updates. But the earlier mentioned "fix" still remedies it. :)

---

### Post by phibxr on 2011-10-23
If someone still has this issue, I solved it by clearing out all the config-directories (the ones prefixed with a dot) in my home directory. Seems like a setting somewhere caused this strange behavior.

---

### Post by anewguy on 2012-03-20
I know this is an old thread, but I just had this issue show up today.  I built this PC a few weeks ago and run 11.10 on it.  I could not figure out why my other 11.10 system was updating and this one was not.  Then today the unity bar started doing pop-under instead of pop-over.  I have no idea why.

All I know is that by doing the unity --reset, the pop-under was correct to pop-over, and I have over 200 updates waiting to be installed.  Mighty strange........

EDIT:  I just figured out what messes up my Unity bar - MythTV!  After I installed it, and again when I start it, the Unity bar is moved to the background.


Dave ;)

---

### Post by TBABill on 2012-03-20
Same thing happened in 12.04 b2. Had to fully update in order to pull in the fix, otherwise you just had to leave it always showing.

---

