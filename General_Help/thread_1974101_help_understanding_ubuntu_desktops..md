---
title: "help understanding ubuntu desktops."
date: 2012-05-05
forum: General Help
---

### Post by spiritech on 2012-05-05
below i have laid out the thing that i find hard to understand about ubuntu.

the way i see it at the moment is that gnome or unity is just a collection of programs that could work independently of each other. so if thats the case can i run ubuntu without gnome or unity installed and if so what are the base programs that are needed to get a "desktop" up and running eg. background manager, window manager, window decorator.

it just seems to me that there is no real need to have desktop specific programs at all and most programs could work independently.

i suppose what i am trying to ask is what do gnome or unity actually do. if they are needed to actually have a desktop up and running why is it that when i go to install it i have to install a barrage of other programs aswell?

i understand that some programs work in unison with each other but where does that stop and independence begin. or maybe i am missing something.

it just seems to me that the thing i most like about life is missing from ubuntu. CHOICE.

spiritech.

please post your thoughts on this subject.

---

### Post by Max Blyss on 2012-05-05
If I'm catching your drift right, and you just want out of Unity, pop a terminal and go: sudo apt-get install xubuntu-desktop and this will get you xfce.  same thing with kubuntu-desktop will get KDE...  Or you can go through synaptic and get Cairo Dock and use its session option at login.

In terms of building your own, you can go get different Window Managers like Openbox, Metacity, XFWM, etc...  As well as installing Compiz for effects and such.

I install compiz & metacity into xfce on all my setups, incidentally.

Poking around in the software center or synaptic will show you how many different environments and components of them there are.  It seems you can mix and match pretty extensively, and there's a tutorial out there for just about everything.

Trial and error is a lot of the fun.  Hope I got your inquiry right.

---

### Post by spiritech on 2012-05-05
> **Max Blyss said:**
> If I'm catching your drift right, and you just want out of Unity, pop a terminal and go: sudo apt-get install xubuntu-desktop and this will get you xfce.  same thing with kubuntu-desktop will get KDE...  Or you can go through synaptic and get Cairo Dock and use its session option at login.

In terms of building your own, you can go get different Window Managers like Openbox, Metacity, XFWM, etc...  As well as installing Compiz for effects and such.

I install compiz & metacity into xfce on all my setups, incidentally.

Poking around in the software center or synaptic will show you how many different environments and components of them there are.  It seems you can mix and match pretty extensively, and there's a tutorial out there for just about everything.

Trial and error is a lot of the fun.  Hope I got your inquiry right.


Max Blyss.

thanks for your reply.

at the moment i would like to know if is possible to run ubuntu without  any of the prepackaged desktops at all eg. xfce gnome unity etc?

i read that the desktops are designed to work differently. ie xfce is designed to be fast. ubuntu is designed to be full featured and unity was desinged to be annoying ( LOL ). though in fact they all do the same thing surely if a program is designed to be quick then it is designed to be quick regardless of desktop environment. and program quality should surely depend on the window manger, compositor that is handling it. yes i agree that programs can be designed to work quickly and in turn grouped together to form i desktop, however ( and this is my major point i am trying to make ) i feel that programs should not be desktop specific. fair enough there maybe certain runtime libraries and dependencies that need to be installed when installing programs from different "Desktop specific programs".

the point i am trying to clarify is why do i need to install any of the preconfigured desktops at all?

---

### Post by papibe on 2012-05-05
Hi spiritech.

Although an interesting question, the answer is not a simple one (long and full of 'ifs' and 'buts').

For your specific concern, I think [this]("https://wiki.archlinux.org/index.php/Desktop_Environment") arch wiki explains it very well. Pay special attention to the paragraph named 'Desktop Environments'.

For more grounding, take a look at this comparison table found [here]("http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments"). Note the 'toolkits' different DEs use. For instance KDE uses QT and Gnome uses GTK+

An application can be very independent in the sense that its functionality is well separated from its interface so it could be build and package easily. For instance, you will find 2 versions of the famous video editor Avidemux on the Software Center. One is Avidemux (GTK+) and the other Avidemux (QT).

Not all applications are created equal. I like very much an mp3 ID3 tag editor called Kid3. Unfortunately it is only available on its QT version.

I hope that can help you understand it better.
Regards.

---

### Post by spiritech on 2012-05-05
> **papibe said:**
> Hi spiritech.

Although an interesting question, the answer is not a simple one (long and full of 'ifs' and 'buts').

For your specific concern, I think [this]("https://wiki.archlinux.org/index.php/Desktop_Environment") arch wiki explains it very well. Pay special attention to the paragraph named 'Desktop Environments'.

For more grounding, take a look at this comparison table found [here]("http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments"). Note the 'toolkits' different DEs use. For instance KDE uses QT and Gnome uses GTK+

An application can be very independent in the sense that its functionality is well separated from its interface so it could be build and package easily. For instance, you will find 2 versions of the famous video editor Avidemux on the Software Center. One is Avidemux (GTK+) and the other Avidemux (QT).

Not all applications are created equal. I like very much an mp3 ID3 tag editor called Kid3. Unfortunately it is only available on its QT version.

I hope that can help you understand it better.
Regards.


thank you for you reply

i am going to have a read through the wiki. i just feel that "desktop environments" are miss leading. and that before "desktop environment" should come window manager/decorator. so maybe after installing ubuntu you get a choice of window managers/decorators. then a choice of your desktop package.

---

### Post by spiritech on 2012-05-05
so are all gnome programs written for GTK?

---

