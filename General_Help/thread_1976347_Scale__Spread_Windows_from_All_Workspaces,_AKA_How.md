---
title: "Scale / Spread Windows from All Workspaces, AKA How to &quot;Fix&quot; Compiz Scale?"
date: 2012-05-08
forum: General Help
---

### Post by drplix on 2012-05-08
I'm reaching out to the community in exhasperation.   I have updated from 11.10 to 12.04 and find that my long-standing workflow for using mutliple workspaces is no longer possible.

The following thread discusses the behaviour we came to know and expect since the earliest days of 3D desktop with compiz (going back 4 or 5 years now)...

[http://askubuntu.com/questions/115209/scale-mode-window-on-same-workspace](http://askubuntu.com/questions/115209/scale-mode-window-on-same-workspace)

In a multi workspace system it is essential that you can find all windows of a given application across all workspaces.

In the above question, I commented on a common scenario with Skype's multi-window chat but the same is true if you move email windows around to use the content in conjunction with a task on another workspace etc etc.

Workspaces allow us to organise by tasks.  But applications are the tools.  It is natural that more than one task needs the same tool.  Hence the windows of a particular application will appear on more than one desktop.

The scale plugin in Compiz was fantastic to find all windows.  Over the last many years I have come to expect that I can assign a hot-key to find all windows on the current workspace, but also have another key to find all windows on all workspaces.  With this feature I don't need to remember where I put them.  I can get a 30,000 foot view.

The recent "fix" to Compiz to prevent Scale supporting windows from more than one workspace is a disaster.  Many people seem to feel the same, here is the original "bug" report and recent comments from people saying that this adds no value and is a regression...

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733)

I don't know if anyone is listening to the user frustrations on that bug report since this seems to have been an intended "design decision".

Irrespective, what I really want to know is is there someone out there that has a PPA with a vanilla standard version of Compiz that I can use instead of the stock version.  One that lets *me* choose if I want to have all windows shown from all desktops?

I really don't want to have to manually patch compiz (as has been suggested as the "accepted solution" on the askubuntu.com forum).

All help gratefully received.  In 11.10 I was actually a strong advocate of the design changes in Unity.  It makes using the desktop on a smaller screen (standard laptop 1360x780) very productive.  But small screens demand using workspaces and now workspaces are incredibly frustrating to use.   A major step back I'm afraid.

My best hope is that this can be reverted in the 12.04 repos.  But a fallback would be if someone can suggest a reliable way to workaround with a vanilla compiz.  I'm afraid that this is so serious for me that if I can't find a solid solution I will be forced to leave Ubuntu after 6 years of fulltime use.

Thanks for listening.  Here's hoping... ;-)

---

### Post by Bazon on 2012-05-08
For me, it's the other way round: in a multidesktop environment, it's essentially for me that I get not distracted by anything going on on other workspaces. I want a clear separation in order to get good and quick access to all tasks. (Each task is in a specific workspace and I know exactly which one. So everything I need for that task ist quick accessable without clutter from other tasks.)

Because Unity isn't doing that fine, I quit it. 
So in the end, Unity seems to be a compromise which makes neither site happy (except the single workspace users) and there are nicht options to fit it to your taste. Great. :-(

---

### Post by mc4man on 2012-05-08
There are 2 things in play here. cpmpiz scale 'broke' picking ALL windows from ALL workspaces during 12.04 dev. (previously seen with Super+W

This is intended to be fixed, when no clue  - [https://bugs.launchpad.net/bugs/933776](https://bugs.launchpad.net/bugs/933776)

The other thing is window picker for window group from ALL workspaces, that broke as a user settable binding back in 11.04. It was available thru the l. click on launcher icon till mid 12.04 dev, now that's also gone (It was always intended to be removed so no big surprise when it Finally happened. As seen in bug report you linked this was a unity change, not compiz 

The scale plugin atm can be user re-built to initiate_all from ALL workspaces using a patch to restore the function, though as mentioned it is intended to be fixed at some point.

Once that is functioning the 'pick window group from ALL workspaces' can returned as a binding but not thru the scale plugin. As it stands now it will only work thru a compiz command & dbus
Whether there is ever any intention to return window group from ALL WS's don't know, probably not. Whether anyone is inclined to fix that in unity time will tell, a fair amount of water under that bridge

There are changes coming for the workspace switcher, value?, we'll see. Overall compiz is & remains a bit of a dog performance wise, you never know whether changes/new features help or hurt

As example see screen on current 12.04 here, I set the overlay large so it's apparent, 1 nautilus window on each WS

---

### Post by piwacet on 2012-05-08
I'm one who would like to see the old behavior of the scale plugin.  I find that I frequently have many terminals open on different workspaces, and can't remember which one is where, so I liked seeing all instances of an application when I tap that icon on the launcher.  Seems people have strong feelings either way.  Would be nice if it was configurable.

Anyone know how to find the commit that made this change?

---

### Post by mc4man on 2012-05-08
> Anyone know how to find the commit that made this change?

This is the bug where the change came from & it eventually appeared in unity (5.2.0-0ubuntu1)

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733)

Unity source has changed quite alot since then,

---

### Post by drplix on 2012-05-09
> **mc4man said:**
> 
This is intended to be fixed, when no clue  - [https://bugs.launchpad.net/bugs/933776](https://bugs.launchpad.net/bugs/933776)


Thanks for pointing this out - I guess this discussion is actually my primary problem.  It seems like a trivial "fix" to revert the Scale.cpp change.  Hopefully someone will understand that this is a very important regression for many many peoples daily use.

Speaking more broadly. Its very disappointing to be in this position with 12.04.  I only recently switched from 10.04 to a Unity-based 11.10 after a hard disk failure.  I was wary of the transition, having heard some horror stories, but actually I quickly came to admire the work that had been put into Unity.  In short, I was a convert.

Compiz/Scale worked as it had always done, and yet I also had the added benefit of the modal icons in the dock allowing me to find all windows of an app in a scale view (across all workspaces - which is the key point for me).

Now scale all windows is broken and even the bonus feature of having the unity dock show all windows doesn't work for me - and maybe even worse  minimized windows can't be found at all.

In summary, this state of affairs can only be considered a major and urgent regression.   I really hope someone who has the ability to resolve this is listening.

---

