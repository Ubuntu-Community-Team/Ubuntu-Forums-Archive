---
title: "Double Right click annoyance"
date: 2010-10-29
forum: General Help
---

### Post by satish_j on 2010-10-29
I have this nasty habit of refreshing desktop in a quick succession by right-clicking and selecting 'Refresh',on my XP system at office.(And,iam sure most of us do the same;)).
With Ubuntu,if a right-click on desktop _slowly_ and select 'align by...',it simulates the XP refresh action as explained above.
But,if i perform the same action rapidly,it takes this first option from right-click context menu,which is 'Create Folder',and results in an empty folder being created on desktop.
I tried double _right-clicking_ and again it created an empty folder.
Is there any workaround to handle this.I mean:Can the right-click context menu items be shuffled so that the 'Create Folder' option is moved from 1st place.
Or any other workaround??

---

### Post by nlsthzn on 2010-10-29
... but why?

---

### Post by satish_j on 2010-10-29
> **nlsthzn said:**
> ... but why?

What do you mean 'why'..dont you think it's an annoyance?Oh..may be you do not belong to my category(meaning:rapid right-click-->refresh) type of pupils..:)

---

### Post by WorMzy on 2010-10-29
I don't think there's anything you can do about this behaviour, so why not left-click and press F5 to refresh instead?

You shouldn't need to refresh the desktop anyway, but maybe you have a specific reason for doing so?

---

### Post by matt_symes on 2010-10-29
Hi

You have an itchy trigger finger. Not much can be done about that except maybe drink less coffee?

Kind regards

---

### Post by nlsthzn on 2010-10-29
> **satish_j said:**
> What do you mean 'why'..dont you think it's an annoyance?Oh..may be you do not belong to my category(meaning:rapid right-click-->refresh) type of pupils..:)

You left some of your bad habits (Windows), so now leave the rest too (refreshing the desktop the whole time in a vain attempt to feel better because your OS is so slow your never sure when it is finished doing something useful, or when it is just busy crashing...)

---

### Post by gnicko on 2010-10-29
You know....

I'm sitting at a Windows XP machine right now...and "double right-clicking" on the desktop does...absolutely nothing.

Does this help?
[http://ubuntuforums.org/showthread.php?t=875262]("http://ubuntuforums.org/showthread.php?t=875262")

---

### Post by mc4man on 2010-10-29
Install xdotool, then create a desktop or panel launcher ( a panel launcher will work on any window with focus inc. desktop

For command use 
 xdotool key Ctrl+r

Edit: if you confine your r. clicking to the bottom of the screen the menu will be above you, will stop the creating of new folders

---

### Post by satish_j on 2010-10-29
> **matt_symes said:**
> Hi

You have an itchy trigger finger. Not much can be done about that except maybe drink less coffee?

Kind regards
Nice suggestion..;)

---

### Post by satish_j on 2010-10-29
> **gnicko said:**
> You know....

I'm sitting at a Windows XP machine right now...and "double right-clicking" on the desktop does...absolutely nothing.

Strange,it should detect the first right-click and show the context menu..

---

### Post by satish_j on 2010-10-29
> **WorMzy said:**
> I don't think there's anything you can do about this behaviour, so why not left-click and press F5 to refresh instead?

You shouldn't need to refresh the desktop anyway, but maybe you have a specific reason for doing so?

thanks for the kind advice frnd,but old habits die hard..

---

### Post by satish_j on 2010-10-29
> **mc4man said:**
> Install xdotool, then create a desktop or panel launcher ( a panel launcher will work on any window with focus inc. desktop

For command use 
 xdotool key Ctrl+r

Edit: if you confine your r. clicking to the bottom of the screen the menu will be above you, will stop the creating of new folders

thanks,will give it a try later today..

---

### Post by nlsthzn on 2010-10-30
Quadruple posts, used when editing is just not awesome enough :D

---

### Post by coffeecat on 2010-10-30
> **nlsthzn said:**
> Quadruple posts, used when editing is just not awesome enough :grin:

Indeed.

@satish_j, there is a useful forum feature called 'Multi-quote' if you want to quote and respond to several posts. As you can see I've used this for this post. The multi-quote  button is just to the right of the regular quote button.

> **satish_j said:**
> Nice suggestion..;)

> **satish_j said:**
> Strange,it should detect the first right-click and show the context menu..

> **satish_j said:**
> thanks for the kind advice frnd,but old habits die hard..

> **satish_j said:**
> thanks,will give it a try later today..

Hope this helps! :)

---

### Post by CharlesA on 2010-10-30
Multiquote is awesome.

Anyway, if you double right click on the desktop on an XP box, all that happens is that it brings up the context menu twice.

Compulsively refreshing the desktop is pointless, even on Windows.

---

### Post by mc4man on 2010-10-30
satish_j
feel free to do whatever you want, probably not needed but so what.
(I have seen the need, starting in lucid, to refresh a dir. during some operations which are not always reflected in realtime

While i don't have an Xp around it's probable that in xp, when r. clicking the cursor is slightly outside of the context box, where in ubuntu it's slightly inside.
So depending on whether the box goes down or up the first or last choice is already highlighted. (on desktop, for folders the highlighted choice depend on folder position and size of context box.

(you could also keep in mind that if you just hold your r. click then whatever action chosen will be executed upon release.

---

### Post by satish_j on 2010-11-01
> **coffeecat said:**
> Indeed.

@satish_j, there is a useful forum feature called 'Multi-quote' if you want to quote and respond to several posts. As you can see I've used this for this post. The multi-quote  button is just to the right of the regular quote button.

Hope this helps! :)

Thanks frnd,was really not aware about it...
OK,so i see there is no way out of this annoyance,but what iam amazed at is that there is no single reply that consider this as an annoyance.
BTW,i suppose this is the feature of Nautilus(default FM in ubuntu).
And,iam also looking for feedback on the thread topic from those who are using a different file manager than Nautilus.
I mean whether the Double right-click annoyance exists in those too??

---

### Post by satish_j on 2010-12-01
Ok,where can i get the source code for Nautilus.(I assume this annoyance can be solved by modifying its source code)
Also,what are the basic technical skills required to modify the source code according to our needs and compile it..

---

### Post by CharlesA on 2010-12-01
Guess this would be a good place to start:[http://stackoverflow.com/questions/2056766/modify-nautilus-source-code-where-to-start](http://stackoverflow.com/questions/2056766/modify-nautilus-source-code-where-to-start)

---

### Post by mc4man on 2010-12-01
> (I assume this annoyance can be solved by modifying its source code
Create a folder, cd to it and 
apt-get source nautilus

I would think one reason not many see this as an issue, (there actually have been some threads on the unintended creation of folders), is there isn't much reason to .d right click.
Normally one is r. clicking to select something, so I'd figure the usual behavior is to r. click, hold, select and release. 
There is a very short time frame before the 'up' is set to execute, this allows a 'tap' right click for a static menu.

Your best bets, if possible, would be to either increase the time frame till 'up' executes or make the cursor be outside of the context menu when it's created in the first place, ala windows

(what is sorta interesting is that a r.click in a window that isn't nautilus is always (i believe) outside of the menu, on the desktop it's in the menu

---

### Post by satish_j on 2010-12-01
> **CharlesA said:**
> Guess this would be a good place to start:[http://stackoverflow.com/questions/2056766/modify-nautilus-source-code-where-to-start](http://stackoverflow.com/questions/2056766/modify-nautilus-source-code-where-to-start)

The link does not mention the url from which the source code was downloaded..

---

### Post by CharlesA on 2010-12-01
> **satish_j said:**
> The link does not mention the url from which the source code was downloaded..
See mc4man's post. I forgot that you can just apt-get the source code.

---

### Post by DeMus on 2010-12-01
Stop to double right-click and all your problems are history.
You mentioned in your first post that probably many people do this, but reading the responses there is no one who does it, including me. I still don't know why you do that. What is wrong with your desktop when you feel the need to do so? Can you maybe show some pictures here, or describe it?
Would love to know why you do this.

---

### Post by CharlesA on 2010-12-01
Sidenote: I tried doing the whole "double right click on a clean install of Lucid (without moving the mouse) and it worked as expected - didn't do anything.

---

### Post by satish_j on 2010-12-02
I just came to know about this file 'nautilus-directory-view-ui.xml' in /usr/share/nautilus/ui,which stores the menu-items.
am going to mess around it and will post the result..

---

### Post by mc4man on 2010-12-02
> I tried doing the whole "double right click on a clean install of Lucid (without moving the mouse)

Are you sure you're not moving it slightly, - maybe it's just here but on all nautilus windows and the desktop the cursor is in the context box, either at the top or bottom.

In app windows it is outside the menu so a d. click does nothing.

( on a laptop it's easy to discern or a 'tap' click should also show

---

### Post by matt_symes on 2010-12-02
Hi

> Are you sure you're not moving it slightly,

This is interesting, because on my laptop (booted into Lucid at the moment) it's also outside (or at least not selecting an item from) the menu, just like CharlesA. Maybe it's a distro issue.

@OP. Are you really sure you want to change the source just to get around this issue. There is a chance that an update or distro upgrade will break all the changes you make. 

It's easier to unlearn that habit.

Kind regards

---

### Post by coffeecat on 2010-12-02
> **matt_symes said:**
> This is interesting, because on my laptop (booted into Lucid at the moment) it's also outside (or at least not selecting an item from) the menu, just like CharlesA. Maybe it's a distro issue.

I can confirm that I can reproduce this in Maverick on my desktop with a wired optical mouse. I'm fairly sure it's not a movement issue either - I tried "tethering" the mouse with one hand and right-double-clicking with a finger on the other to minimise the possibility of mouse movement. My desktop now has several 'untitled folder X' folders on it which I shall clean up shortly.

However, to my mind this is a near non-issue. The OP has already been told that this is a pointless habit even in XP. 

> **matt_symes said:**
> @OP. Are you really sure you want to change the source just to get around this issue.

Quite. If I had the choice between hours of source code hackery or simply abandoning an unnecessary mouse habit, I think I know which one I would choose. :)

---

### Post by mc4man on 2010-12-02
> Maybe it's a distro issue
I'd think possibly more of a theme deal. 
At least here the cursor is always just inside the context menu in nautilus. However with some themes the active area in the context menu doesn't extend full width, so in that case nothing is selected. With the light and dust themes, (use ambiance here), the active area is full width so something is always selected.

---

### Post by satish_j on 2010-12-03
I Thank you all for the inputs!!
I managed to get around this by modifying the file *nautilus-directory-view-ui.xml*..
I have now 'Create Launcher' as very first menu-item in right-click context menu.So,even if the rapid right clicks causes first item of context menu to trigger,it displays this 'Create Launcher' window,which can be easily cancelled with 1 mouse click.
And,this is exactly the feature I was looking for..i.e to shuffle the right-click context menu-items so that 'Create Folder' is shifted down the line..
Thanks again for your time..And,Iam now continuing with ;)my Nasty Habit...;)

---

### Post by CharlesA on 2010-12-03
Don't forget to mark the thread as solved from thread tools.

---

### Post by satish_j on 2010-12-06
> **CharlesA said:**
> Don't forget to mark the thread as solved from thread tools.

Oh yeah,doing it right away..

---

