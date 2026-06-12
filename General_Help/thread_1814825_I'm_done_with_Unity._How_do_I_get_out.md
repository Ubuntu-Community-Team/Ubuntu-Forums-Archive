---
title: "I'm done with Unity. How do I get out?"
date: 2011-07-30
forum: General Help
---

### Post by pieroxy on 2011-07-30
Ok, I've tried Unity for awhile now and I can say it lacks a couple of critical things for me. First is launchers, second is a task bar. While casually browsing the web is ok, more serious work involving several windows has become a pain.

I have a dual screen with four virtual desktops. I'm tired of searching for my windows. 

Now, I've read in a few places that I just need to choose "Ubuntu-classic" whenever I boot my machine. This is fine, but for the fact that I don't have any options on my login screen... Just the login and the accessibility & power buttons at the bottom right.

How can I log in using the old gnome display manager?

---

### Post by flipper T on 2011-07-30
you need to enter your username on the log in screen ***_before_*** the option to use classic becomes available

---

### Post by elliotn on 2011-07-30
kde rocks

---

### Post by pieroxy on 2011-07-30
> **flipper T said:**
> you need to enter your username on the log in screen ***_before_*** the option to use classic becomes available

Aaaand, life is good again. Thanks.

How did I miss that? I wonder...

---

### Post by Vaphell on 2011-07-30
it lacks launchers? as in 'icons that run applications when clicked'?
that thing on the left works pretty much exactly like taskbar in win7, you can right click on a program icon and pin it there so it's permanent. If by any chance you know your way around taskbar in win7, then it should be not remotedly alien in unity, the main difference being the bottom vs left thing.
Not that i am a unity fanboy but it seems that you didn't really try to discover the way it works.

---

### Post by richaustin on 2011-07-30
> **Vaphell said:**
> it lacks launchers? as in 'icons that run applications when clicked'?
that thing on the left works pretty much exactly like taskbar in win7, you can right click on a program icon and pin it there so it's permanent. If by any chance you know your way around taskbar in win7, then it should be not remotedly alien in unity, the main difference being the bottom vs left thing.
Not that i am a unity fanboy but it seems that you didn't really try to discover the way it works.

I have to agree there. Unity works for me really well, but it does take a bit of time to get used to. I use four desktops with at minimum one app' on each, usually more, and have no trouble navigating around. In fact I find it quicker than in Classic Gnome or KDE. Linux is all about freedom though and Unity is sure not going to Unite everyone!

---

### Post by coldraven on 2011-07-30
I just got used to pressing Super+A to see all apps on all desktops in 10.10.
What is the equivalent in Unity?

---

### Post by pieroxy on 2011-07-30
> **elliotn said:**
> kde rocks

Ah... And here we go.

I am using Gnome (Ubuntu). Before that, I used bare X with openbox (Slackware). Before that, X with fvwm  (Slackware again). That's all I know.

Now. I have windows decorations, a taskbar and launchers. That's all I care about really. The rest is religion for me.

So please, since you are trying to convince me, tell me what I will have when I switch to KDE (which I've never tried). And keep in mind that I have a quad core with 8GB of RAM, so drop the resources arguments on the doorstep.

I am genuinely interested to know what KDE offers.

---

### Post by Vaphell on 2011-07-30
> I just got used to pressing Super+A to see all apps on all desktops in 10.10.
What is the equivalent in Unity?

i think Super+W does that

---

### Post by pieroxy on 2011-07-30
> **Vaphell said:**
> it lacks launchers? as in 'icons that run applications when clicked'?
that thing on the left works pretty much exactly like taskbar in win7, you can right click on a program icon and pin it there so it's permanent. If by any chance you know your way around taskbar in win7, then it should be not remotedly alien in unity, the main difference being the bottom vs left thing.

Well, it lacks a usable launcher. First, it is vertical with huge icons, leaving way to few icons really. And no, scrolling IS a pain. This could EASILY be worked around with drawers, but alas, they are not supported. Another thing, icons are mixed. Could be running or not. Could be running multiple times. So whenever you have more icons than the height of your window, you just can't see anything anymore. Everything is mixed is a colorful bunch of icons. But worst of all, it goes away whenever you maximize any window. I thought I'd get used to this, but I didn't. 


> **Vaphell said:**
> Not that i am a unity fanboy but it seems that you didn't really try to discover the way it works.
I've been working with it since the day of the release. I already know everything you've told me.

Edit: Of course, that's my take on it. YMMV.

---

### Post by Vaphell on 2011-07-30
> Well, it lacks a usable launcher. First, it is vertical with huge icons, leaving way to few icons really. And no, scrolling IS a pain. This could EASILY be worked around with drawers, but alas, they are not supported.

do you know you can regulate the size of the icons? you can make them smaller.
install compiz settings manager
```
sudo apt-get install compizconfig-settings-manager
```
run it
```
ccsm
```
ubuntu unity plugin: Launcher Icon size - by default 48, range from 32 to 64
just checked, on a standard 1366x768 display 13 app icons fit without scrolling (plus 4 hardcoded: trash, workspace switcher, app lens, file lens) when set to 32px
also you can about sorting tasks to different workspaces and switching between them? ctrl+alt+left/right/top/down, WIN+S?

> Another thing, icons are mixed. Could be running or not. Could be running multiple times. So whenever you have more icons than the height of your window, you just can't see anything anymore. Everything is mixed is a colorful bunch of icons.

that's how docks work since forever in mac and linux and win7 does that too now. Launchers are taskbar items at the same time if there is any instance present. Have you noticed those little triangles on the left side of icons? They indicate the number of windows in a group. Also workspaces - use them

> But worst of all, it goes away whenever you maximize any window. I thought I'd get used to this, but I didn't.

run compiz settings
```
ccsm
```
ubuntu unity plugin: hide launcher = Never
magic :-)

---

### Post by pieroxy on 2011-07-30
> **Vaphell said:**
> do you know you can regulate the size of the icons? you can make them smaller.
install compiz settings manager
```
sudo apt-get install compizconfig-settings-manager
```
run it
```
ccsm
```
ubuntu unity plugin: Launcher Icon size - by default 48, range from 32 to 64
just checked, on a standard 1366x768 display 13 app icons fit without scrolling (plus 4 hardcoded: trash, workspace switcher, app lens, file lens) when set to 32px
also you can about sorting tasks to different workspaces and switching between them? ctrl+alt+left/right/top/down, WIN+S?



that's how docks work since forever in mac and linux and win7 does that too now. Launchers are taskbar items at the same time if there is any instance present. Have you noticed those little triangles on the left side of icons? They indicate the number of windows in a group. Also workspaces - use them



run compiz settings
```
ccsm
```
ubuntu unity plugin: hide launcher = Never
magic :-)

Interesting post. I learned a couple of things, but it made me realize what I can't cope with in Unity "magic bar".

I do use workspaces extensively. I usually end up with consoles in all my workspaces, sometimes more than one. And yes, I know there are tabs in consoles. But I also have dual screens so sometimes I have more than one terminal per workspace.

With gnome, the taskbar shows me the consoles and apps running on my workspace. With unity, the *$£%%! taskbar show me everything ALL THE TIME, in every workspace. How is that for keeping stuff organized? I don't care to know every app running on my system at one time. I want the current workspace to show me what's in the current workspace. I thought that was the point of workspaces? To be able to "compartmentalize" your desktop.

As you pointed out, you can get 13 apps displayed at a time. I usually end up with twice or three times this number. Just my development workspace has icons for jEdit, Conky, Squirrel SQL, Eclipse, SmartSVN, Chrome, Firefox, 3 VMWare (webserver in a VM of course, A Vista and an XP to test), a couple of consoles. That's 12 already. Just one workspace. Or several for that matter, since all icons are stuffed in there no matter which workspace you're on. I just can't get around the fact that this one thing to put everything (launchers, running apps, some hardcoded stuff, workspace switcher, ...) is just not a way of keeping stuff organized.

It's like saying "look at your wallet, there are compartments for cards, cash, coins and other stuff. I bought this improved wallet: just one big bag where you can stuff everything you need". Well, I'll keep my walled over the "improved one" anytime.

And I'm not counting the fact that whenever you close an app, you have to click on the background to make the "Ctrl-Alt-RightArrow" work to go to the next workspace. I'm not too keen on the menubar being on top either. It is confusing sometimes.

Edit: My point with the consoles is that clicking on the console icon in Unity bring you thumbnails for your consoles which are completely and utterly useless. I know which console does what (prod, test, des, other stuff) by where I placed it. Thumbnails of text is pointless.

---

### Post by Vaphell on 2011-07-31
i do't use unity much, my main box is lucid with awn at the bottom. Yes, hardcoded behavior of unity sucks though there are features i'd like to see in other docks (like native support for hotkey navigation, in unity super+#)

> With gnome, the taskbar shows me the consoles and apps running on my workspace. With unity, the *$£%%! taskbar show me everything ALL THE TIME, in every workspace. How is that for keeping stuff organized? I don't care to know every app running on my system at one time. I want the current workspace to show me what's in the current workspace. I thought that was the point of workspaces? To be able to "compartmentalize" your desktop

does unity really show icons of all apps, no matter which workspace they are on? oh man, that would suck. My understanding was that it shows pinned launchers and 'free' apps of current workspace

Either way your it's clear that your workflow doesn't subscribe well to unity philosophy so it's understandable to look for something that suits you better :) Unity is tailored for a average joe that uses 5 apps tops and doesn't do any hardcore coding with tons of IDEs and testing environments.

---

### Post by pieroxy on 2011-07-31
> **Vaphell said:**
> does unity really show icons of all apps, no matter which workspace they are on? oh man, that would suck. My understanding was that it shows pinned launchers and 'free' apps of current workspace


That's my experience... The unity bar looks the exact same in all workspaces.

---

### Post by Vaphell on 2011-07-31
i have access to unity now and what you say is true o_O That is ridiculous and in such scenario workspaces are rendered pretty much useless as they don't do anything to limit the clutter
i have found a launchpad bug report discussing it (it's not a bug but a deliberate design decision).
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683170](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683170)
Srsly, ubuntu devs should listen to their user base for a change :/

---

### Post by walt.smith1960 on 2011-07-31
> **pieroxy said:**
> Aaaand, life is good again. Thanks.

How did I miss that? I wonder...

And 11.10 has an environment similar to 11.04's classic (so far at least). The choices (with gnome-session-fallback enabled) are Ubuntu (Unity), Ubuntu 2D, GNOME 3, GNOME CLASSIC and GNOME CLASSIC - no effects.  So much for "OMG it's gonna be Unity or nothing!!!"  I don't know how the various applets will fare; I'm sure they'll have to be rewritten.  11.10 has just gotten Gnome3 desktop working more or less.

---

### Post by old farmer on 2011-07-31
sorry, started new thread

---

### Post by pieroxy on 2011-08-01
> **Vaphell said:**
> i have access to unity now and what you say is true o_O That is ridiculous and in such scenario workspaces are rendered pretty much useless as they don't do anything to limit the clutter
i have found a launchpad bug report discussing it (it's not a bug but a deliberate design decision).
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683170](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683170)
Srsly, ubuntu devs should listen to their user base for a change :/

The problem is that their user base is geeks and techies. And they'd like it to be n00bs and grandma's. So... Let's just try to not alienate your current user base in your attempts to grab the new one.

---

### Post by blane2 on 2011-08-01
go to login screen in admin

unlock and set your default session to classic.

---

### Post by walt.smith1960 on 2011-08-01
> **pieroxy said:**
> The problem is that their user base is geeks and techies. And they'd like it to be n00bs and grandma's. So... Let's just try to not alienate your current user base in your attempts to grab the new one.

Your point is valid.  I think Unity is an attempt to address the "Linux is HARD!!" cry from the non-geeks & techies.  GNOME 3 and 2 flavors of GNOME classic are present in the next release to follow 11.04s GNOME classic.  The risk with trying to satisfy two disparate groups is satisfying neither.  I guess we'll see how things pan out.

---

### Post by Vaphell on 2011-08-01
i agree that ubuntu team caters to nooblets but who says that novice users don't benefit from sane defaults? I simply don't see how workspaces can be useful when the launcher bar is littered with icons for all apps. Why not set number of workspaces to 1 when separate workspaces provide very little value? Besides behavior of the launcher needs revision.
They should just copy awn/docky/cairo/whatever_dock_there_is/osx and call it a day instead of reinventing the wheel, but in an inferior way.

---

