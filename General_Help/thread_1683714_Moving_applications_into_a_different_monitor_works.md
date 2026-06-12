---
title: "Moving applications into a different monitor workspace"
date: 2011-02-07
forum: General Help
---

### Post by stephanmir on 2011-02-07
Hi guys, hope your evenings are going well.

So my question is this: Is it possible to have programs load onto a second monitor workspace?

I am trying to figure out how to do it with Evolution. When I have my primary monitor occupied with games I would like to keep evolution open on my 2nd monitor, however I don't see a way to:

a) Drag it across the screen into the second monitor
b) Have it automatically load into that second monitor workspace
c) Change permissions to move it directly into a second monitor workspace, only workspaces within the primary monitor

Let me know what you guys have been able to find out.

Thanks all!

ScubaSteve

---

### Post by winchendonsprings on 2011-02-08
Do you have your monitors in TwinView?

a. I don't think that you can have two workspace open at the same time.
b. I think once you get the monitors settings worked out you will just be able to drag the window across. Also most window manger remember the placement of windows so if you drag it across and close it, then next time you open it, it will be where you left it.
c. I don't think it's a permissions issue.

I use two monitors and have them in "twinview." Both monitors are a single workspace, so when I change workspaces they both change to the next workspace. I know with compiz you can clarify what number workspace you want a certain application to open on. That is not the issue at hand though.

If you're using Nvidia, are you using NIvidia x server settings?

---

### Post by Hedgehog1 on 2011-02-08
> **stephanmir said:**
> :

a) Drag it across the screen into the second monitor
b) Have it automatically load into that second monitor workspace
c) Change permissions to move it directly into a second monitor workspace, only workspaces within the primary monitor



To move a window to another workspace, you can: Right Click on the application's button in the lower bar.  Then select 'move to workspace right' or 'move to another workspace' and you will see a list.

Also, if you have compiz visual effects turned on, the shift switcher will allow you to drag windows to the next workspace.  In fact, there are a ton of ways to move windows with compiz.

However, I think the right click method is your best place to start.

:KS

p.s. I did not find a way to open an app in a workspace that is not the active one. I am sure one exists, I just don't know it.

---

### Post by Forgotten Path on 2011-02-08
It sounds like you have the second monitor setup as a "Separate X-Screen", in which case you can't drag windows back and forth.

However, you can control which display an application launches on with:

```
DISPLAY=:0.0 nautilus ~/Music
```
or
```
DISPLAY=:0.1 nautilus ~/Music
```

depending on which display you want it on.  If you want to do this quickly (without terminal) you can create a desktop launcher.

EDIT:
This may be an elegant solution for you, if you are using Compiz-Fusion:
[Move Active Window to Different Screen (dual head)]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1045417")

---

### Post by stephanmir on 2011-02-08
Thanks everyone for all your responses.

So here's what I found out. I looked under my Monitor settings (NVidia controls) and under the X Screen Display Configuration it says:

Configuration: Separate X Screen

So I switched it to Twin View and saved settings then Quit and Rebooted.

Now I can drag everything across the monitor to the other one. Also if you click Add New Bar, it'll do the sides of the primary then adds to the secondary, top bottom then sides again. You can remove which bars you don't use.

Thanks also for the tip on the Display command, however now that it treats everything as 1 display it won't recognize the command anymore. But no worries now that I can drag across monitors!

Thanks all!

ScubaSteve

---

