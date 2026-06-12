---
title: "cannot see side panel with cube?"
date: 2012-02-15
forum: General Help
---

### Post by qwertyjjj on 2012-02-15
I tried activating the cube from compiz but it completely hides the left panel so I have no way of starting my programs.
Also, I don;t seem to get an actual cube, it just flips between windows like ALt Tab would.
Any ideas on how to get this working?

---

### Post by qwertyjjj on 2012-02-17
> **qwertyjjj said:**
> I tried activating the cube from compiz but it completely hides the left panel so I have no way of starting my programs.
Also, I don;t seem to get an actual cube, it just flips between windows like ALt Tab would.
Any ideas on how to get this working?

Any ideas?

---

### Post by tkjeeper on 2012-02-17
> **qwertyjjj said:**
> Any ideas?

took me a while for this too, first the unity bar along the left side is set to hidden in compiz settings under unity settings, set it to always show or dodge windows or something else. Second, it took me a bit to find this also, to rotate the cube you have to hold the ctrl+alt, then, and this is tricky without a mouse like on a laptop, hold the left mouse button WHILE moving the cursor around. If your compiz settings are right, the cube should rotate. google is your friend my man.

---

### Post by qwertyjjj on 2012-02-21
> **tkjeeper said:**
> took me a while for this too, first the unity bar along the left side is set to hidden in compiz settings under unity settings, set it to always show or dodge windows or something else. Second, it took me a bit to find this also, to rotate the cube you have to hold the ctrl+alt, then, and this is tricky without a mouse like on a laptop, hold the left mouse button WHILE moving the cursor around. If your compiz settings are right, the cube should rotate. google is your friend my man.

But to install the cube, it removes the unity plugin?!
...and I cannot reenable it

---

### Post by philinux on 2012-02-21
> **qwertyjjj said:**
> But to install the cube, it removes the unity plugin?!
...and I cannot reenable it

I dont think ccsm and unity play nice. Especially trying to activate the cube etc. To reset unity open a terminal ctrl alt t and use ```
unity --reset
```

There was a big debate about ccsm in ubuntu+1 forum.

ubuntuforums.org/showthread.php?t=1915533

---

### Post by qwertyjjj on 2012-02-21
> **philinux said:**
> I dont think ccsm and unity play nice. Especially trying to activate the cube etc. To reset unity open a terminal ctrl alt t and use ```
unity --reset
```

There was a big debate about ccsm in ubuntu+1 forum.

ubuntuforums.org/showthread.php?t=1915533

By resetting unity, won;t that get rid of the cube?

---

### Post by jim_deadlock on 2012-02-21
Yes it will, but it means you can start again setting up your cube from scratch in ccsm - next time, always make sure that the Unity plugin is enabled before closing ccsm because it tends to disable itself for various reasons while messing with other plugins.

To fix your "flat" cube you need to go to the General Options plugin -> Desktop Size (tab) and set Horizontal Virtual Size to 4.

---

### Post by qwertyjjj on 2012-02-21
> **jim_deadlock said:**
> Yes it will, but it means you can start again setting up your cube from scratch in ccsm - next time, always make sure that the Unity plugin is enabled before closing ccsm because it tends to disable itself for various reasons while messing with other plugins.

To fix your "flat" cube you need to go to the General Options plugin -> Desktop Size (tab) and set Horizontal Virtual Size to 4.

But the problem is this, I set H V to 4 as per this tutorial: [http://ubuntuguide.net/enable-compiz-desktop-cube-in-ubuntu-11-10-oneiric-unity](http://ubuntuguide.net/enable-compiz-desktop-cube-in-ubuntu-11-10-oneiric-unity)

As soon as I do that it disables the unity plugin, I cannot reclick the plugin to enable it again.

I then do not have a cube on the desktop, just flat screens. I can switch between screens by pressing Alt Tab but cann't switch between apps.

---

### Post by philinux on 2012-02-21
> **qwertyjjj said:**
> But the problem is this, I set H V to 4 as per this tutorial: [http://ubuntuguide.net/enable-compiz-desktop-cube-in-ubuntu-11-10-oneiric-unity](http://ubuntuguide.net/enable-compiz-desktop-cube-in-ubuntu-11-10-oneiric-unity)

As soon as I do that it disables the unity plugin, I cannot reclick the plugin to enable it again.

I then do not have a cube on the desktop, just flat screens. I can switch between screens by pressing Alt Tab but cann't switch between apps.

Reset unity and try this. No guarantees mind.

[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/)

---

### Post by qwertyjjj on 2012-02-21
> **philinux said:**
> Reset unity and try this. No guarantees mind.

[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/)

nope, same problem. In fact the whole screen is more messed up with that and I couldn't even get the terminal back using ctrl alt t.
Very strange.

---

### Post by qwertyjjj on 2012-02-21
> **qwertyjjj said:**
> nope, same problem. In fact the whole screen is more messed up with that and I couldn't even get the terminal back using ctrl alt t.
Very strange.

Perhaps this bug covers it?
[https://bugs.launchpad.net/unity/+bug/773141](https://bugs.launchpad.net/unity/+bug/773141)

Still unsure if there is a workaround though.

---

