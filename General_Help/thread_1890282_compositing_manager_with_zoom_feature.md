---
title: "compositing manager with zoom feature"
date: 2011-12-03
forum: General Help
---

### Post by esbrinartot on 2011-12-03
I'm using Lubuntu 11.10 and I didn't have any compositing manager.

As my computer has low resources I've installed xcompmg and Cairo Composite manager but they have some small problems

xcompmgr: Works fine. The only feature I** miss is to have a similar tool than Compiz ****Enhanced **[I]**Zoom Desktop.**

[/I]Cairo Composite manager: Doesn't work properly and has* some problems of stability*. Has the **pluggin magnifier but doesn't satisfy me**.

So I prefer xcomprmgr but I need to find out  a software that provides similar features than enhanced zoom desktop of Compiz. **Anyone knows a Software??**

---

### Post by Exüberance on 2011-12-03
I've been looking for something like this too.

Compiz has a major bug where nothing is redrawn while you are dragging windows.
Mutter crashes whenever you go to screensaver, lock the screen, or suspend.
Metacity with compositing turned on doesn't properly clear the screen when dragging files or text.
Xcompmgr causes part of the screen to flicker when draging files or text, and the corners of windows with transparency are not properly redrawn.

...sigh... I'm probably going to have to go back to Ubuntu 11.04 until compiz gets fixed.

Where did you manage to find a build of Cario Composite Manager for oneiric? The newest version I can find is for Maverick.

EDIT: Right now I'm installing kwin. I use GNOME Classic (gnome-fallback), not KDE, but it can apparently be used with non-KDE environments and is like Compiz, so I'll let you know how that turns out!
UPDATE: Wwwwwooooooooooooooooooooo kwin works! EXCELLENT.

---

### Post by esbrinartot on 2011-12-04
Is strange what you tell me.

1- Regarding Cairo composite manager I installed Cairo composite manager for Maverik. Also was impossible for me to find the oneiric version. Anyway try to install it. Maybe works for you. In my case works... The only problem I found is when I use full screen to watch a video the lxpanel doesn't hide. All the other features works. Try it maybe works for Ubuntu (I'm using Lubuntu).

2- You have tried so many composite manager and all of them have problems. So my advice is wait. If this happens to everyone you will soon receive updates and the problems you have will be fixed. Anyway consider that maybe is problem of your graphic card or the drivers drivers you are using. Are you using privative drivers?? if you don't try to use them... maybe works better than open drivers.

3- If you are thinking to reinstall and downgrade to 11.04 think seriously to downgrade to 10.04 LTS. If you don't use Unity I think there is no reason to install 11.04. In my opinion Newest versions of ubuntu consume to much resources. 10.04 LTS was fine and it's LTS you have long term support.

4- With xcompmgr I have the same problem as you but only flickers an instant. (for me is not a problem and I'm sure that if I disable the animations the problem is fixed) I just want to have zoom feature. (but Maybe there is no option available as nobody answer post. Yes there is compiz but it's too heavy)

5- I don't mind if I don't have any composite manager due to the only think are doing is making slower the computer. So for me xcompmgr is a very good option as it's so light. But I'm looking a solution to have the zoom feature.

have a nice weekend

---

### Post by Exüberance on 2011-12-04
I'm using the proprietary drivers from NVidia. They work perfectly when playing graphics intensive games like 0 A.D. The only problem is that the GPU is always at the highest performance level no matter what window manager I use (even plain metacity with no compositing). When I'm on battery instead of AC power, it's on the middle performance level though, so that's better.

I was using 10.04 (that's what I meant in my previous post. I typed 11.04, but I meant the latest LTS) on my old computer, but my new System76 computer came with Oneiric, so I started using that for now.

Hopefully all of these bugs will be fixed by the next LTS, otherwise I'll have a problem. I added the cairo-compmgr ppa, changing the distribution from Oneric to Mavrick so it would find it, and it works perfectly! I finally have something I'm happy with.

If you're looking for a light window manager (ie not compiz or kwin), then there are really only 3 options:
1) Metacity with compositing (gconf editor: apps=>metacity=>general, set compositing_manager and compositing_effects on)
2) xcompmgr, which has a couple issues
3) cairo compositing manager

None of those have zoom like you want though unless there's a plugin I don't know about.

---

### Post by esbrinartot on 2011-12-05
I guess the behaviour of your computer is correct. Well ty to update the Nvidia drivers. You can do it through this repository:

Maybe with the updates you will receive your problem will be fixed:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
And then update the system. For sure you will receive updates of your graphic card.

It's up to you which system you use. With Ubuntu I will use 11.04 because has Gnome classic desktop.

REgarding the composting manager I've tried xcompmgr and cairo-compositing manager and both of them have problems on Lubuntu 11.10. I've tried to do the same with metacity but I can't install it.

I install metacity and after I type metacity --replace and after that the keyboard of the computer doesn't work and the windows border disappear.

Anyone knows if it's possible to install metacity in lubuntu 11.10?

---

### Post by Exüberance on 2011-12-05
That's... strange. Perhaps Metacity doesn't work with LDXE. If the keyboard doesn't work and there's no window decorations, that means that no window manager is running so it seems Metacity is immediately crashing as soon as you start it. What's the output in the terminal after you run it?

I've also noticed screen tearing with non-compiz windows managers, so I might just go back to 10.04. I've already burned the live CD, but I'm going to give 11.10 a chance for a bit longer to see if I can make things work. I'll try that ppa you mentioned.
EDIT: Turns out my Compiz window moving problem was a mouse polling issue (upon further testing, the screen only froze when moving with my mouse, not my touchpad). I found a fix, so I'm once again happy with my desktop.

Have you tried installing compiz? I realize that's kind of counterproductive  to having Lubuntu, but really if you don't use crazy effects, it won't  use up noticeably more resources than any other compositing window  manager.

---

### Post by esbrinartot on 2011-12-06
Hi Exüberance

Have you tried to add the nvidia repositories and update the system?  I think you should try it because maybe you will solve all your problems.

Please also go to your nvidia setting / X Screen 0 / OpenGL settings and disable Allow Flipping.

Don't format your computer just because of this problem. It's funny to find a solution and if you unconfigure the system try to fix your problem then you can format of course.

Another solution I have for you is next. I finally installed metacity and metacity works perfectly Cairo compositing manager or if you prefer you can install the default composite manager of metacity. To install metacity...  Well you go to synaptic and install the packets

then you go to:

/home/your user/.config/lxsession/LXDE
or if when you start the sesion uses lubuntu then go to
/home/your user/.config/lxsession/Lubuntu

Inside the folder you will find the archive desktop.conf

In this archive you must modify:
window_manager=openbox-lxde
for
window_manager=metacity

Then restart your sesion and works fine. Then install cairo composite manager and solved ar activate composite manager of metacity.

So before formatting please try all the available options you have. You will even get fun.

Now with metacity I have a problem And maybe someone can help me. Anyone know how to change the theme of The windows....  I can change the them of the windows but there is no option to change the borders of the windows. (the place you can find the buttons and so on.)

Can anyone help me with this issue.) I will like that windows of metacity looks like to openbox windows but I have the problem of the window border.

---

### Post by Exüberance on 2011-12-06
With the mouse polling fix, I got everything working in Compiz so I abandoned Metacity + Cairo in favour of Compiz, though there's screen tearing when I use anything other than Compiz. I'll try disabling flipping like you said to see if that works.
EDIT: That didn't do anything, but I notice there's no "triple buffering" option in my NVidia settings. If I can figure out how to add that into my xorg.conf file, that will hopefully eliminate tearing in Metacity.

As for the themes, install Ubuntu-Tweak (**ppa:tualatrix/next**) and you can change your theme from there. If you like your current theme, but just want larger borders, you can *probably* change it by modifying one of the files in /usr/share/themes/{your theme name}/ or one of it's subfolders.
EDIT: For Ambiance, it's the file /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml. Probably something similar for other themes. If that file doesn't exist for your theme, try gtk.css or gtkrc.

---

### Post by esbrinartot on 2011-12-07
Why did you use Metacity + Cairo composite manager?

Metacity has it's own composite manager. You can activate it with gconf-editor.

I've also found out to change border themes. Can be done with gconf-editor. I've used Ubuntu Tweak in the past but with gconf-editor it's enough for me.

Is not clear for me if you solved the tearing problem with config. If not please read this aticcle

[http://omniumpotentior.wordpress.com/2011/04/03/eliminar-tearing-en-compiz/](http://omniumpotentior.wordpress.com/2011/04/03/eliminar-tearing-en-compiz/)

Is in spanish but there are good translators.

---

### Post by Exüberance on 2011-12-07
I did try Metacity with compositing, but the screen didn't redraw properly when dragging files or text around, so I turned it's compositing off and used Cairo instead.
Plus, Cairo lets you choose from a limited number of desktop effects, but Metacity doesn;t.

That article didn't help since I don't have tearing in Compiz. It's only when I *don't* use Compiz, that I have tearing. Thanks for the suggestion, though.

---

