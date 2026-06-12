---
title: "Ubuntu vs Other Distros - Ubuntu Less Administrative Options?"
date: 2010-06-05
forum: General Help
---

### Post by fs_tigre on 2010-06-05
Hi,

I was recently talking with a friend of mine about how I like Ubuntu and he was telling me how Mandriva was a nicer OS than Ubuntu, in fact he said that Ubuntu was for Kids or people that don't know much about computers.

He said that with Ubuntu you don't have as much as administrator control as with Mandriva, I did't argued since I don't know much about Ubuntu neither Mandriva, so I would like to hear from the experts.

Is it true that with Ubuntu the user has less administrative options than any other linux distro?

Can someone help me to understand the basics about the differences between different distros?

Will programs run on any distr regardless of what distro was the program written for? 

Thanks a lot!

---

### Post by beastrace91 on 2010-06-05
> **fs_tigre said:**
> Is it true that with Ubuntu the user has less administrative options than any other linux distro?

Not true. Ubuntu currently lacks a centralized location for administrating the entire system from, but this does not mean you have less control over your computer. More so that to find the tools to do so you need to simply look in your menu instead of opening a "control center". This is something that is planning on being added as of 10.10 though.

> **fs_tigre said:**
> Can someone help me to understand the basics about the differences between different distros?

The core difference between any two distros are their default packages (software), what versions they maintain in their repositories, and what package management system they use. Obviously there are some more (such as rolling release distros) but that is the basics.

> **fs_tigre said:**
> Will programs run on any distr regardless of what distro was the program written for? 

Most FOSS/Linux software is not written for one particular "distro" as much as it is written for Linux as a whole. At worst most times you may have to compile something from source instead of installing for a pre-compiled package when using a less main-stream distro.

Hope that clears some things up for you.

Regards,
~Jeff

---

### Post by fs_tigre on 2010-06-05
Fist of all thanks a lot for the clarification.

> Most FOSS/Linux software is not written for one particular "distro" as much as it is written for Linux as a whole. At worst most times you may have to compile something from source instead of installing for a pre-compiled package when using a less main-stream distro.

Sorry, is this a YES (excuse my ignorance)?

Thanks a lot!

---

### Post by XSAlliN on 2010-06-05
> ...in fact he said that Ubuntu was for Kids or people that don't know much about computers.

He trolled you there for most part, yet there is some truth in this as in "more user friendly then other linux distributions" and It's true that's the main reason why Ubuntu is so popular.. But, even advanced users can find a home on Ubuntu, since his popularity made Ubuntu a primary target when it comes to application development for Linux. So if you like Debian, then there's a good chance you like Ubuntu as well - doesn't mater if you're beginner or advanced users...

The funny part about your friend- he doesn't realize that Mandriva liked the Ubuntu approach and it even follows it. Since even Mandriva Desktop is made with beginners in mind.

Tell your friend to try Slackware, Arch, Gentoo - or other so called "aimed at advanced/expert Linux Users" and then, maybe... he won't act like a Linux expert/advanced users which I believe it's not the case. ;)

---

### Post by teh603 on 2010-06-05
> **beastrace91 said:**
> Not true. Ubuntu currently lacks a centralized location for administrating the entire system from, but this does not mean you have less control over your computer. More so that to find the tools to do so you need to simply look in your menu instead of opening a "control center". This is something that is planning on being added as of 10.10 though.If its anything like the eeebuntu control center, then its either totally redundant or the maintainers have stripped controls out of the menu so people will actually have to use it. The latter is true in eeebuntu; the Control Center has most of the controls that should be in the Settings menu.

---

### Post by ajgreeny on 2010-06-05
What he may have meant was that ubuntu does not use a separate root password, nor an administrator account for those jobs that most other distros require a root password.  In ubuntu we use sudo instead for those users who are members of the admin group.

Some so called experts suggest that thi sis not as secure as a separate root password, something refuted by the ubuntu developers very strongly.

For more details of this see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I also agree with XSAIIIN that simply because ubuntu is the most popular desktop linux distro, does not mean that it is any less powerful.  Anything that can be done on those supposedly more grown up and powerful distros, can be done just as well with ubuntu.

Incidentally, it is very easy to add the **gnome-control-centre** to your menu by using alacarte (system- preferences- main menu).  It is something I always do as I just find it easier than looking through the menu.

---

### Post by Bradj47 on 2010-06-05
When I used Mandriva it seemed just as n00b-like as Ubuntu. As far as I can tell it's just an RPM version of Ubuntu.

---

### Post by Linuxforall on 2010-06-05
Of course Ubuntu is a sore eye for rest, while others are barely making it, Ubuntu stays on top of distro watch count and for a good reason. I compile my own ffmpeg, x264 and mplayer thanks to excellent instructions here by Fake Outdoorsman and andrew46, I find compiling to be most accesible and easiest in Ubuntu and Debian in general, the package creation is far more transparent process. I don't know why people make these childish comparison to act superior. Madriva is quite good on its own and no one distro is superior than others, its just a matter of choice. Its like talking about religion, one is never superior to others no matter what they say.

---

### Post by aysiu on 2010-06-05
Ubuntu actually has a centralized control center, but its menu item is deactivated by default. You can right-click on the Applications menu and select **Edit Menus** to re-enable it. Or you can invoke it by pressing Alt-F2 and pasting in ```
gnome-control-center
``` Why don't you just try both Ubuntu and Mandriva and see if what your friend says is true? My guess is that he will not be able to name any specific "administrative option" possible in Mandriva that is not also possible in ubuntu.

More importantly, there is nothing less kid-oriented about Mandriva than there is about Ubuntu. Both are new-user-friendly Linux distros that set everything up for you. If your friend really wants to prove how "leet" he is, he should be using Arch Linux, Gentoo, or Slackware... or Linux from Scratch.

---

### Post by Barafu Albino Cheetah on 2010-06-05
Well, for me, Ubuntu is one of the least user-friendly distros I know. I runs awesome, when you install it, at it recognises your video card. What a progress. When the first bug come out (on the first day usually) it is stubborn as hell. 
Ubuntu is user friendly, if by user we understand a guy, who hardly knows windows. He will think most bugs to be features (Gnome loading for a minute after welcome sound) and most features to be bugs (no wm by default on Gentoo). 
If you want a little more than described in Ubuntu advertisement, you will have problems. 

Those who think I am picky, do the following things. 

[LIST]
[*]Imagine that Avahi crushes your netwotk and local admin said he will ban you from Internet if you start it once more. Disable avahi in one try without uninstalling it.
[*]Install splix package with j2000 support.
[*]Recompile ffmpeg so that it can handle 12GB videos. Maximum size is a compile time setting.
[*]Install newest mysql  and amarok at the same time.
[*]Alter kernel config without the need to realter it every time kernel updates.
[*]Switch to previous minor kde version that is supposed by your version on Ubuntu. Imagine current one has a bug you can't fix or tolerate.
[*]So on.
[/LIST]

---

### Post by fs_tigre on 2010-06-05
Thank you all very much!

---

