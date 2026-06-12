---
title: "List Open with... in Nautilus"
date: 2009-10-07
forum: General Help
---

### Post by DeMus on 2009-10-07
When I right click a file in Nautilus and choose "Open with..." I get a long list of possible programs to open the file with.
Through time this list has become very long and very disorganized. Where can I find this list to organize it, delete program listings I don't have anymore, change the list into alphabetical order, etc?
I looked in the .gnome and .nautilus folders in my home folder but it's not there. Where else can I look?

---

### Post by mc4man on 2009-10-07
look in ~/.local/share/applications

( in jaunty and earlier, the blue icons are from custom commands, the display name is not the actual name of the .desktop 
( actual name is userapp-<first name in command>-XXXXXX.desktop

Corresponding entries plus normal installed app associations per mimetype association are in ~/.local/share/applications/mimeapps.list using the actual .desktop  name

As far as alphabetical order, don't think that is possible, the order shown off of r. click is somewhat 'seemingly random' ( though cleaning up the uneeded entries per line in mimeapps.list can help

---

### Post by DeMus on 2009-10-07
> **mc4man said:**
> look in ~/.local/share/applications

( in jaunty and earlier, the blue icons are from custom commands, the display name is not the actual name of the .desktop 
( actual name is userapp-<first name in command>-XXXXXX.desktop

Corresponding entries plus normal installed app associations per mimetype association are in ~/.local/share/applications/mimeapps.list using the actual .desktop  name

As far as alphabetical order, don't think that is possible, the order shown off of r. click is somewhat 'seemingly random' ( though cleaning up the uneeded entries per line in mimeapps.list can help

Complicated, to say the least. I'll try to figure it out. Thanks for your answer.

---

### Post by mc4man on 2009-10-08
It's not really as it first seems.

as far as the blue icons, right click on -> properties and you'll see the command it represents.

( when I set up a open with -> use a custon command i normally go right in and give it an icon and a distinctive display name

A nautilus action " open in text editor" is valuable for editing the . .desktops themselves ( vs. it's properties.


In mimeapps.list each line is a specific mimetype and the entries are apps ( technically their .desktops) or custom commands that were used on that mimetype

The first listed is usually the default for that mimetype

The format of each line is

whatever.desktop;whatever1.desktop;


notice there are no spaces and each whatever.desktop ends with a ;

here's an ex. from karmic ( if I was on my hardy could show better, haven't made/created many yet
for auto play of cd's

> x-content/audio-cdda=userapp-amarok21-1LC70U.desktop;rhythmbox.desktop;vlc.desktop;userapp-amarok-9RFE0U.desktop;userapp-audcd-RTB80U.desktop;totem-xine.desktop;


The default ( first listed is a custom amarok .desktop, the rest are other's I've made or tried
You can freely remove entries per line as long as you maintain the formatting

Ex.
> x-content/audio-cdda=userapp-amarok21-1LC70U.desktop;rhythmbox.desktop;vlc.desktop;userapp-audcd-RTB80U.desktop;


---

### Post by DeMus on 2009-10-08
> **mc4man said:**
> look in ~/.local/share/applications

( in jaunty and earlier, the blue icons are from custom commands, the display name is not the actual name of the .desktop 
( actual name is userapp-<first name in command>-XXXXXX.desktop



You talk about blue items, where can I find those? I don't see any blue items.

---

### Post by mc4man on 2009-10-08
> You talk about blue items, where can I find those?

Then either you haven't used any custom commands or the change I see in karmic is also in jaunty ( never used jaunty, now custom commands are files with actual name

By custom command I mean 'open with' -> 'open with other application -> 'use a custom command'
see screen 1 from hardy

For just removing from what you see listed from the r. click open with screen, those can be removed by going r. click -> properties -> open with, clicking on an entry -> remove

Everything removed from properties screen on right will disappear from the open with on left

screen 2


Edit 
If I wanted to remove any entry permanently for all filetypes  I'd instead remove  it from the lines it's in in mimeapps.list and delete the .desktop from the applications folder **if I'd created it.** ( like in screen1  - ffplay, mplay, run1, Amarok Cd Player

---

### Post by DeMus on 2009-10-08
I think we are talking slightly about different windows. You choose file properties and then tab "Open with".
I right-click a file and in the drop down menu I choose "open with". With the arrow next to it, I go to the right. There is a list of standard applications which I used before and at the bottom of the list I see: Open with other application. When I choose this I see a totally random list. That's the list I was talking about.
Sorry for not writing it more clearly in the beginning.

---

### Post by mc4man on 2009-10-08
> I think we are talking slightly about different windows.
Yes and no, was somewhat alluding to in both  posts (deleting or renaming .desktops

That list you have limited control over

**Any item that you created** can be removed by deleting the .desktop in ~/.local/share/applications

In your case the most likely ones would be ones seen without icons

The rest are there to stay unless you uninstall  the app itself

The wine/windows ones may or may not be seen in ~/.local/share/applications ( should be

For instance in my screens you'll see 2 ffplay entries and .desktops. **I created both**, but only gave one an icon. Both will show up in the r. click -> open with other application list, one as 'ffplay', one as ffplay
with an icon.

If I delete one or the other or both of the .desktop's from ~/.local/share/applications then they will then  be gone from all lists

On the other hand in that list is 'Firefox Web Browser'. 
It's there to stay unless I uninstall firefox, if I uninstalled firefox and the entry was still there then I'd delete the firefox .desktop in /usr/share/applications

Can you post a screen  of ~/.local/share/applications ?

---

### Post by DeMus on 2009-10-08
> **mc4man said:**
> Can you post a screen  of ~/.local/share/applications ?

Sure, here it is. Sorry for the delay, had to work, just got home again.

---

### Post by mc4man on 2009-10-08
Decided to take a look in karmic figuring jaunty would be more like that than hardy

Solely on the list in question

Anything on that list that's an installed app will stay on the list unless the app is un-installed.

My list is in alphabetical order. ( may not be in jaunty, is in karmic

Anything you added thru a custom command that's appearing in the list can be removed by deleting the associated **userappp **.desktop in ~/.local/share/applications. ( though on karmic it won't disappear till you log out and in

So if your not using or the listings are dups then delete those .desktops

For example if your seeing multiple FoxitReader entries in the list

All those userapp-FoxitReader .desktops may have the same Exec= (command) or different ones.
To check use the properties or open them  in a text editor. ( Nautilus action or cli, ex.
```
gedit ~/.local/share/applications/userapp-FoxitReader-6L5UUU.desktop


```

As far as the wine-extension ones
Never saw those before, so went ahead and installed wine 1.2.
Initially there weren't any but after opening a file in notepad they're all over the place so to speak (both in the applications folder and in the list

Don't know what to make of them yet, though they seem to be a way to open files based on ext. directly with  windows progs.

For the moment i'm going to ignore them even though some are duplicated in the list ( notepad, wordpad

Edit; Karmic doesn't use blue icons and display names for userapp. desktops like hardy did, now you see the actual name of the .desktop as a file ( no icon
assuming jaunty is the same

---

