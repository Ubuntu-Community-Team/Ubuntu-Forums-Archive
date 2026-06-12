---
title: "Extra Visual Effects don't stay"
date: 2010-03-10
forum: General Help
---

### Post by soccer4dummys on 2010-03-10
I'm using Compiz for some effects (wobbly windows for example). What's weird, though, is every time I reboot I need to right click on the desktop -> change desktop background -> visual effects -> extra. It's like it defaults back to "None". It works fine after that, so I don't believe it's a driver issue. I do have an ati 5870, and the drivers as well as ati catylist have installed correctly. 

Another thing that keeps changing, are my workspaces. I have 4 set up, two columns and two rows. It likes to change them back to 4 columns and 1 row, though. 

It's weird. Anybody have any ideas? I've been using Ubuntu for 2 weeks, so I'm still kind of new at this. I'm getting the hang of some of the features, though!

EDIT: Also, I don't know if it's related or not, but around the same time I noticed this happening is when my Ubuntu System Panel I recently installed freaked out. I removed it and installed the standard menu in it's place. Haven't been able to get it working as of yet, either. Could be two separate issues, but thought it might be useful info.

---

### Post by n0dix on 2010-03-10
For the visual effects                                                                    [this]("http://ubuntuforums.org/showthread.php?t=1167402") could help you.

---

### Post by soccer4dummys on 2010-03-10
The Compiz --replace command does indeed work. My workspaces change back to the way I want as well. Ty.

However, putting it in the startup doesn't. Maybe I'm doing it wrong? I added it to the startup programs in the Startup Application Preferences, by clicking "Add", and putting "compiz startup" as the name, and the command as "compiz --replace"

That should work, correct? What happens currently (with it as described above) the effects will stay until I open a window, then close it again. It's weird. I tested this with both firefox and a terminal, and waited before closing it, just to be sure it's not a timing thing.

Oh, and the USP I fixed by a reinstall.

---

### Post by n0dix on 2010-03-10
Try the third suggestion

---

### Post by soccer4dummys on 2010-03-10
Those keys are already set to /usr/bin/compiz, so I wouldn't need to change anything, correct?

---

### Post by n0dix on 2010-03-10
> **soccer4dummys said:**
> Those keys are already set to /usr/bin/compiz, so I wouldn't need to change anything, correct?

No. 
Try with [this]("http://ubuntuforums.org/showthread.php?t=1000965&highlight=compiz+resets&page=2")
or 
[this]("http://www.uluga.ubuntuforums.org/showthread.php?p=8938388").

---

### Post by soccer4dummys on 2010-03-11
It lives! Thanks. :)

fyi, [this one](http://ubuntuforums.org/showpost.php?p=8162422&postcount=11) did it for me.

---

### Post by n0dix on 2010-03-11
i'm glad you solved the problem, but don't forget to add the Solved tag to the title. ;)

---

### Post by soccer4dummys on 2010-03-11
Bah, I thought it worked, but I guess I was mistaken. I recently rebooted again, but alas. The issue is still there. x_X

The Compiz --replace will get compiz working, but only if entered manually.

---

### Post by soccer4dummys on 2010-03-12
It's weird, but I found a work around.

If I start Firefox immediately after startup and keep it open for awhile (not sure on the exact time) then I can close it and compiz will still be running. I'll look into getting firefox to open on a different workspace so I don't have to be there when it boots. I'm OK with that.

[Solved]

---

### Post by n0dix on 2010-03-13
> **soccer4dummys said:**
> It's weird, but I found a work around.

If I start Firefox immediately after startup and keep it open for awhile (not sure on the exact time) then I can close it and compiz will still be running. I'll look into getting firefox to open on a different workspace so I don't have to be there when it boots. I'm OK with that.

[Solved]

Very weird, but it works for you it's great.
Cheers!

---

