---
title: "orange rectangle"
date: 2011-10-22
forum: General Help
---

### Post by Gawains Green Knight on 2011-10-22
When I move the mouse to the left or right of the screen it causes a transparent orange rectangle to cover half the screen. Almost like its trying to snap a window or something. Anyone else noticed this? Is there a solution?

---

### Post by enkay009 on 2011-10-22
This normally happens when you drag a window to the edge. It's quite helpful when working on many things at once (ex. browser windows on the left, terminal on the right).

Are you simply moving your mouse to the edge (i.e. not dragging a window) when the orange rectangle appears?

---

### Post by Gawains Green Knight on 2011-10-22
Yes, no dragging involved. I go over to unity to switch workspaces or to the scroll bar and it kicks it off. I usually have to click on the workspace switcher to get it to stop.... tried playing with compiz setting but no joy.

---

### Post by enkay009 on 2011-10-22
Hmm... that is weird. It doesn't sound like intended behavior. Unfortunately (or maybe fortunately) I haven't run into it so I can't offer much help.

---

### Post by Gawains Green Knight on 2011-10-22
Hmmm I wonder if its because I'm running libreoffice. I just booted up and opened google chrome in one workspace and libreoffice impress in another (both full screen) and it happened, but didn't happen before then....

---

### Post by enkay009 on 2011-10-23
A shot in the dark here, but what if you logged out and tried deleting your compiz settings?

Since the grid/orange rectange is a feature of compiz, it might be worth trying to see if it fixes this issue.

```
rm -rf ~/.compiz* ~/.config/compiz*
```

You could alternatively rename them too if you want to roll back.

---

### Post by Gawains Green Knight on 2011-10-23
I changed a whole bunch of stuff, and seemed to fix it.... I actually I messed a whole bunch of other stuff up, but once I got it all sorted it was, well, all sorted.... not too sure what I did to compiz which fixed the problem though. Something in ccsm.

---

### Post by enkay009 on 2011-10-23
I read somewhere on this forum that ccsm doesn't play nice with ubuntu 11.10. 

Anyways if you got it to work then great.

BTW, I assumed you were running 11.10... but then again your profile says 11.04... so nevermind.

---

### Post by dburgan on 2011-10-25
It's happening to me as well, no LibreOffice running. See attached screen shot. Generally the way I reproduce is to launch something, then when I try to click on it in the launcher to switch to it, the obnoxious orange rectangle appears.

Is there a way in ccsm or dconf to simply turn this feature off entirely? I don't personally find it useful and would prefer to make the orange rectangle issue go away entirely ... ?

Thanks in advance for any help ...

---

### Post by miaumiau on 2011-10-26
I would like to know what feature is this and how can I deactivated, is becoming annoying.

---

### Post by Me Mechant on 2011-10-26
> **enkay009 said:**
> A shot in the dark here, but what if you logged out and tried deleting your compiz settings?

Since the grid/orange rectange is a feature of compiz, it might be worth trying to see if it fixes this issue.

```
rm -rf ~/.compiz* ~/.config/compiz*
```

You could alternatively rename them too if you want to roll back.

When i try this my computer freeze ! So i reboot and when i came back all the compiz settings were removed....but after 5 minutes the horrible orange rectangle came back ! Thanks for trying !

In the meantime i'm using gnome 3 this rectangle is so annoying  !

---

### Post by Frogs Hair on 2011-10-26
> **miaumiau said:**
> I would like to know what feature is this and how can I deactivated, is becoming annoying.

If you are using the Compiz CCSM disabling the desktop wall will keep the box from appearing except when causing a window to overlap with the top panel.

This is fine if you are using the cube , but less than ideal other wise .

---

### Post by Cortexbuster on 2011-10-26
I am experiencing the same thing in 11.10 using ccsm.
I got rid of the annoying rectangle by disabling the 'Grid' 
Save your work before you make any changes in ccsm, because gnome tends to crash while applying the changes... at least on my machine.

---

### Post by Gawains Green Knight on 2011-10-27
Cortexbuster, thats what I did too. Exactly the same.

---

### Post by chuckyanutsup on 2011-10-27
I was having this issue. I have seen a bug report on it. I believe I may have fixed it by adjusting the "automaximise value" in CompizConfig Settings Manager. I am not really sure what it does, but since I set it to 95$ I've stopped getting the bug. Will post again if it resurfaces.

---

### Post by mjuhasz on 2011-10-27
Here's the bug report bug: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/875557](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/875557)

It's nominated for the unity milestone 4.26.0 "SRU1"

---

### Post by chuckyanutsup on 2011-10-27
looks like I was wrong, it's back. I'm trying disabling grid now.

---

