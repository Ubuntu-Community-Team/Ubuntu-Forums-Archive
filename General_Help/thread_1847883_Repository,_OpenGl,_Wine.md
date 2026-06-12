---
title: "Repository, OpenGl, Wine"
date: 2011-09-21
forum: General Help
---

### Post by XeKaaz on 2011-09-21
Good evening.

Before I ask my questions I will inform you all of that I have searched for a reasonable answer, however so far, no luck. So I decided to come here.

I'm fairly new with Ubuntu so I'll need very simple explanations, I'm also Swedish, my English might therefore also be questionable at times.

Now to topic.
I've decided that I wish to play games on my pc - for this, Windows is excellent, but I think that the advantages of Ubuntu's fast loading times, stable system makes up for that.

Anyway. The game I'm currently struggling with is Diablo 2 and it's expansion Lord of Destruction.
I've come to terms with that I need to add wine to my repository.
 Which brings me to the first question; The repository. I just can't understand where/how to find/access and deal with it.
     I believe I access it by first going to Applications > Synaptic Package Manager, then Settings > Repositories. However I can't understand what I'm supposed to do there.
(I'm supposed to go there to properly install wine, add this *ppa:ubuntu-wine/ppa, *to my repository) However I've installed wine via the Ubuntu Software Centre. Might this work just as good?

Second question. OpenGL drivers.
I'm sitting on a quite old homebuild, my graphic card is a Radeon X850, where/how do I get OpenGL drivers? Also, what is it?!

I'm greatful for those who takes the time to write me a serious answer. I'm aware of that I'm a noob and that I've probably missed to read some helpful threads, please teach me.

Regards.
XeKaaz

---

### Post by Luxx on 2011-09-21
Diablo II
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=74](http://appdb.winehq.org/objectManager.php?sClass=application&iId=74)

This seems to be one of the games that works well under WINE version 1.3.26. Unfortunately you can't get that version of  WINE through the repositories any more. It was just updated today to version 1.3.28 and some games and apps are not working in the new version. You may have to install WINE version 1.3.26 from the archive here:

[http://wine.budgetdedicated.com/archive/binary/](http://wine.budgetdedicated.com/archive/binary/)

The instructions are on the WineHQ website here:
[http://wiki.winehq.org/FAQ#head-7ed3c3163e2b932ee2030a48f9c5e553dc41817b](http://wiki.winehq.org/FAQ#head-7ed3c3163e2b932ee2030a48f9c5e553dc41817b)

As far as graphics drivers, I don't have much advice. I know WINE has some issues with DirectX, but haven't had any problems with standard GL. Perhaps someone else will have some better information for you.

---

### Post by patryk77 on 2011-09-21
> **XeKaaz said:**
> OpenGL drivers.
I'm sitting on a quite old homebuild, my graphic card is a Radeon X850, where/how do I get OpenGL drivers? Also, what is it?!

Check under System / Administration / Hardware Drivers.

If there are proprietary drivers for your video card (I expect yes) you can enable them there; OpenGL support will be included.

Although that may not be necessary (don't own an ATI card, but I have heard good things about the open source drivers, don't know about your particular card), you can always try the game first and see if you need to install the drivers afterwards.

---

### Post by ashams on 2011-09-21
Now try with diablo2, if it doesn't work, look for 'playonlinux' from Synaptic Package Manager(From: System>Administration>Synaptic Package Manager) then type 'playonlinux' in the top field, claick on the package name and click install, then from the toolbar choose apply. When it finishes start it from Applications Menu and find diablo or some.

---

### Post by XeKaaz on 2011-09-21
> **patryk77 said:**
> Check under System / Administration / Hardware Drivers.

If there are proprietary drivers for your video card (I expect yes) you can enable them there; OpenGL support will be included.

Although that may not be necessary (don't own an ATI card, but I have heard good things about the open source drivers, don't know about your particular card), you can always try the game first and see if you need to install the drivers afterwards.

Ehe...

I seem to have issuses locating this directory.
I'm using Ubuntu 11.04 if that helps you help me navigate :)

---

### Post by patryk77 on 2011-09-21
Ummm... I keep forgetting that people use Unity by default :P

It's not a directory, it's in the menu.

You can try to press alt+f2 and typing jockey-gtk in the run menu (if it appears) or running jockey-gtk from the terminal.

---

### Post by Mark Phelps on 2011-09-22
There are no proprietary drivers that will work with your Radeon card and any recent verion of Ubuntu.  ATI (now, AMD) dropped Linux driver support for your card years ago.

Therefore, you will be restricted to using the default open-source drivers and while those support 2D graphics fine, they provide no hardware acceleration for 3D graphics.

Also, newer Windows games require DirectX 10 support in the driver and on the card.  Your card and driver provide only older DirectX (9 or less) support.

It's unlikely you'll be able to run the game you want without completely replacing the card.

And, don't be tempted to download any drivers from AMD.  They won't work with your card, will totally hose up your display, and you will then be forced to do a LOT of work removing them -- only to replace them with the same drivers you already have running now.

---

