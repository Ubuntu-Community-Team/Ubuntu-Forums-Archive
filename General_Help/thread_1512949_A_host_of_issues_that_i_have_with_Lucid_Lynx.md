---
title: "A host of issues that i have with Lucid Lynx"
date: 2010-06-18
forum: General Help
---

### Post by hotnikkelz on 2010-06-18
Hmm, is anyone else having the following issues...

Epiphany crashes everytime i try to load a site with flash or java without error message, without warning

Randomly, youtube videos load very slowly

When in the file manager, if i put it on list, i cannot click drag select a group of files. I only can do it in icon view :/

While in any browser, clicking the address bar, does not select the entire adress that's there, which means i have to manually highlight it to replace it with say a search. Normally (in windows) i can click in the address bar, and it automatically selects the entire address, so once i start typing it's replaced

I cannot make my panels thicker. I can increase the pixel size yes, but it just seems to double up the panel. I have a 24 i monitor at 1920x1200, the panels and icons are small, and i have to lean into my screen :/ Why no option to make the panels large UNIFORMLY

Message menu is troublesome for me, i don't like empathy one bit, but i lose most functionality if i don't use it. So the solution? i have to remove the applet altogether :/ bummer. I don't like using email clients, i like launching gmail in browser, and i like pidgin, but want the features that empathy got in the applet

Weird stuff like random small lines appear on my panels like when i exit a program from the indicator applet

It doesn't seem much faster than windows 7 if at all, i find windows is blazing fast for me, i tend to have weird lags when loading apps in ubuntu :(

Doesn't remember my windows positions, it seems quite random

No undo option :'(

There's more, but that's what i can remember off the bat.
If anyone has some advice on how to rectify some of these problems help me please, cuz i really want to use ubuntu as my primary OS.  I'mt relying really hard to fall in love with it. But apart from the better apps I'm not getting the vibe. Please convince me, pretty pretty please

---

### Post by darolu on 2010-06-18
> Epiphany crashes everytime i try to load a site with flash or java without error message, without warning
More info would be nice to help you, using 64-bit OS? does it happen when using other browsers? 64-bit Flash plugin is not stable. I personally love Epiphany, it is my main browser, but they switched from Gecko to Webkit as main render engine not long ago so it still has some glitches and lack of functionality in some areas (like changing the font-type), future versions should solve these issues.
I can recommend Midori, another Webkit-based browser, it is light and fast too.

> Randomly, youtube videos load very slowly
Again, if you're using 64-bit flash plugin, it is "normal" as it is not stable, the 64-bit plug in is a beta version (if you're wondering when it is going be stable, ask Adobe). Remember that some videos just load very slow in all browsers and OS's, why? I don't know, Google's servers are usually good.

> When in the file manager, if i put it on list, i cannot click drag select a group of files. I only can do it in icon view :/
It is not a bug/glitch, no one can. Try the compact view.

> While in any browser, clicking the address bar, does not select the entire adress that's there, which means i have to manually highlight it to replace it with say a search. Normally (in windows) i can click in the address bar, and it automatically selects the entire address, so once i start typing it's replaced
You can press "Ctrl + L" in most browsers to get it.
In Firefox  you can solve it by going to "about:config" (in your address bar); then search for **browser.urlbar.clickSelectsAll**, then double click the "**false**" so it turns into "**true**".

I have never had the other issues you're having, although I don't think I fully understood your panels sizing problem, most apps have the same Windows shortcut to undo (ctrl+z).

If you don't like empathy, try **emesene**, it's quite popular and is very similar to microsoft's messenger clients, you may find it good.
> Please convince me, pretty pretty please
No one is here to convince anybody, we're here to help people solve their technical issues.

---

### Post by hotnikkelz on 2010-06-19
I'm not sure what flash plugin i am using. I have the 64 bit version of LUcid though. I installed the restricted extras, so whatever that uses, I'm using it. I can't give any more info, i wanted a light version of firefox, and the browser looked nice...but it just shuts down just like that..no error msg or anything, jsut failed

Hey compact view works :) Thank God! 

NIce firefox fix, thank you very much :) I didn't know about the ctrl+L

I liked pidgin the most to be honest, but Ubuntu comes with the messagingmenu, and it seems it only works with empathy to utilise all the features, like the status etc

Hmm about the panels, like say i want to add a panel to the left, i get a series of tiny squares instead of a straight smooth rectangle panel that goes on top and bottom. If i try to make a panel thicker, it appers as 2 panels joined together

Another issue i have is that the resize window selection area is quite tiny and precise, i have to be in almost exact postion to get the resize option up and running.

It's strange, i'm using Linux Mint now, which is based of Ubuntu, and i don't get any of these problems hmmm. I think i should stick with that until i'm good enough to tinker with Ubuntu.

Thanks for the help though, kudos

---

### Post by warfacegod on 2010-06-19
> I cannot make my panels thicker. I can increase the pixel size yes, but it just seems to double up the panel. I have a 24 i monitor at 1920x1200, the panels and icons are small, and i have to lean into my screen :/ Why no option to make the panels large UNIFORMLY


This is probably due to the Theme you are using. Either use a different Theme or make the panel transparent.

---

### Post by hotnikkelz on 2010-06-19
Using the default right now, will try out your suggestion thank you.

ATI proprietary drivers blow on ubuntu, i better stick with the ubuntu open source ones.

---

### Post by warfacegod on 2010-06-19
> **hotnikkelz said:**
> Using the default right now, will try out your suggestion thank you.

ATI proprietary drivers blow on ubuntu, i better stick with the ubuntu open source ones.

I've never used ATi with Linux so I have no first hand experience. However, I assure you that you are by no means the first person that's posted similar sentiments.

---

### Post by hotnikkelz on 2010-06-20
ATI 10.6 is not as bad as the others, but there's still issues with that driver as well. As soon as you see the poor resolution of the ubuntu splash screen, you know it's not what it should be lol.

I'm sticking with ubuntu's packaged open source in teh meanwhile.

I tihnk i found a massively weird bug imo.
If I'm connected to VPN after like 15 minutes, my connection pretty much dies. ouch. Tech support for my vpn service has no clue what's going on with it hahaha

THe flash drivers bundled with 64 bit seem very flaky indeed. On full screen i get some major lag and freezing. I'm giving 32 bit ubuntu a run through and see how it compares

WHere do i find the 'extra' effects for compiz. Mine doesn't have ones like the airplane fly away one, among a good few others :/

---

### Post by warfacegod on 2010-06-20
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by warfacegod on 2010-06-20
Also:

```
sudo apt-get install compiz-fusion-plugins-main
``````
sudo apt-get install compiz-fusion-plugins-extra
```

---

### Post by tacotime on 2010-06-20
> **hotnikkelz said:**
> 
WHere do i find the 'extra' effects for compiz. Mine doesn't have ones like the airplane fly away one, among a good few others :/

Or you could install ubuntu tweak from 
[ ubuntu-tweak.com]("http://ubuntu-tweak.com/"), and install the compiz settings manager from there, it's also pretty useful for other stuff like cleaning up GRUB and different things.

---

### Post by hotnikkelz on 2010-06-20
> **warfacegod said:**
> Also:

```
sudo apt-get install compiz-fusion-plugins-main
``````
sudo apt-get install compiz-fusion-plugins-extra
```


already had the manager, but not the extras, thank u :)
Still can't find which option are for the mouseeffects though..except for the water effects

How do i double click to to pen on the items in the notification applet, and how do i change the icons? For eg, if i wanted to ge a mono colour one for pidgin. How i go about that?

Icons on panel, have no location awareness, its kinda weird

---

### Post by warfacegod on 2010-06-20
Right click the icon and uncheck "Lock To Panel" to move them around.

Icon themes can be found here: [http://gnome-look.org/]("http://gnome-look.org/")

To install them, go to: Right click your desktop> Select "Change Desktop Background"> Themes tab> Drag n' Drop theme packages into the window.

---

### Post by warfacegod on 2010-06-20
> Still can't find which option are for the mouseeffects though..except for the water effects


Paint Fire On Screen

---

### Post by wilee-nilee on 2010-06-20
OP could your clarify your actual level of understanding of the OS, and how long you have been using it and to what extent.

---

### Post by hotnikkelz on 2010-06-20
ah i can only change those icons via theming...i was hoping i can do them individually. Bummer. I know that you can unlock them and move them about too, what i mean is that if i add something to panel, i have to move them into a nice position manually, it doesn't 'snap' into position. If i restart the OS, it lines up well for some reason.

fire!!! yay!! a good 30 seconds of fun :)

Are u calling me OP?
If so, i would say i'm pretty **** poor at Linux based stuff, but i'm learning quite a bit, and gradually finding out what i like and don't like. Mostly on the interface side though...which is a good thing. Recently started, and i want it to be my main OS

---

### Post by wilee-nilee on 2010-06-20
> **hotnikkelz said:**
> ah i can only change those icons via theming...i was hoping i can do them individually. Bummer. I know that you can unlock them and move them about too, what i mean is that if i add something to panel, i have to move them into a nice position manually, it doesn't 'snap' into position. If i restart the OS, it lines up well for some reason.

fire!!! yay!! a good 30 seconds of fun :)

Are u calling me OP?
If so, i would say i'm pretty **** poor at Linux based stuff, but i'm learning quite a bit, and gradually finding out what i like and don't like. Mostly on the interface side though...which is a good thing. Recently started, and i want it to be my main OS

If you want direct answers to any problems, lumping them together like the thread starting post is not the way to do it. The best way is to do one at a time, it is a forum etiquette issue. It is great that you want to learn, and that you want it as your main OS, you will get there faster with some specific questions rather then a mixture of problems. It was easy to see from the problems that you were a fairly new user. I think we all want you to succeed in your endeavor here.:p

---

### Post by warfacegod on 2010-06-20
Wobbly windows is fun too. I sometimes waste as much as ten minutes goofing off with it. I'm thinking of getting two mice working independently so that I can wiggle two windows at a time.

Yes, wilee-nilee is referring to you as OP. It stands for Original Poster or some such.

---

### Post by hotnikkelz on 2010-06-21
Oh, i didn't think that was a problem :/
live and learn i guess, i apologise

---

### Post by hotnikkelz on 2010-06-22
Is there any way to configure the indicator applet or the messaging menu to be integrated with pidigin instead of empathy. I'm not liking empathy at all.
I would like to be able to click my name, and change status and so on via the memnu, but for Pidgin.


How do i view the source code for these applets, i'm curious to see how these things look like and so on. Curiousity of course since i don't know a lick of programming whatsoever.

ALso, how do I go about customising the panel? when i customise the panels using the simple way, the applets don't change with it, neither does the application menu, so it seems kinda pointless.. How i go about theming it in other words, like assigning monochrome icons to things that go to the tray etc

---

### Post by warfacegod on 2010-06-22
Right click your desktop> select Change Background> Theme tab> click Customize> Icons tab> choose icon set> Controls tab> choose different control sets to change the look of the menu.

Many themes are available here: [http://gnome-look.org/](http://gnome-look.org/)

Download them and then drag n' drop them into the Theme tab to install.

---

### Post by cryptotheslow on 2010-06-22
> **hotnikkelz said:**
> Is there any way to configure the indicator applet or the messaging menu to be integrated with pidigin instead of empathy. I'm not liking empathy at all.
I would like to be able to click my name, and change status and so on via the memnu, but for Pidgin.

This probably isn't much help as I can't remember exactly how I achieved it. But right after installing 10.04 I removed Gwibber and installed Pidgin, I think I may also have uninstalled at least parts of Empathy - you need to be very careful here as the package manager may want to remove the entire desktop packages when removing Empathy.

Now, the mail icon on the top bar goes purple when I receive a new message in Pidgin and when I click on my name in the top bar I can change my status in Pidgin - although the options are limited to Available, Away, Busy, Invisible, Offline.

It was achieved using information on these forums, try searching the forum for something like "replace Empathy with Pidgin" or "safely remove Empathy" etc.

---

### Post by warfacegod on 2010-06-22
> the package manager may want to remove the entire desktop packages when removing Empathy.

This is only partially true. Some of the Empathy package are also tied into things like gnome-panel for instance. Perhaps I'm thinking of the Evolution packages but either way, the concept applies. Removing the ubuntu-desktop package poses no real risks. It only a meta-package. That means it tells your system what other packages to pull in during install. The only time after that you'll really need it is in the event of deciding to do an Upgrade Install. Removing won't remove any other apps or packages.

---

### Post by hotnikkelz on 2010-06-23
warface:
Yeah i know how to tinker with existing themes alredy, i wanted to know how to do my own.

crypto:
Thank you, will do a browse around and see, that's good news :) 
Why does it sem ubuntu is 'foricing' me to use applications that I don't want to use. In order to get the user experience i need to use evolution eeew....empathy....eew. Gwibber's not bad though haha

---

### Post by warfacegod on 2010-06-23
Try icon-slicer, icontool, libusplash-dev. Stuff I found in Synaptic I'm petty sure there's one for building themes too.

---

### Post by alphacrucis2 on 2010-06-23
> **hotnikkelz said:**
> Using the default right now, will try out your suggestion thank you.

ATI proprietary drivers blow on ubuntu, i better stick with the ubuntu open source ones.

I disagree. I have seen constant improvement in the Catalyst driver over the last eighteen months. The latest Catalyst 10.6 that was released last week rocks as far as my ATI card goes. They've finally fixed the backclear problem! I used to have to run a patched version of x-server to make fglrx play well with compiz - to eliminate the dreaded window restorelag.

---

### Post by warfacegod on 2010-06-23
A friend of mine recommended "The Widget Factory" for themes.

---

### Post by Oolongtea on 2010-06-28
I have Lubuntu on another of my computers and it lags any time I try to load anything.

---

