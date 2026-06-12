---
title: "how to boot in to linux command prompt"
date: 2011-03-15
forum: General Help
---

### Post by acklavidian on 2011-03-15
Sorry if a am in the wrong category here. I am a computer science student, and so sometimes I would like really quick access to a command line. 

First off I was wondering if there was a way I could make a option in grub that will boot Ubuntu without any x11 stuff. Kinda like the System rescue option, but without the menu, and not start as root. 

Second... I would say that I want a session that lets me start without x11, but for my purposes that is easy enough to do with ctrl+alt+number from the GDM. Instead, I would like a fast loading window manager that is good for programming. Really any interesting desktop environment (or window manager)suggestion that I am unfamiliar with would be investigated.(I am highly interested in wm/de, and have explored many.)

---

### Post by WlaadDyaab on 2011-03-15
> Sorry if a am in the wrong category here. I am a computer science student, and so sometimes I would like really quick access to a command line.

Ctrl + alt + T

---

### Post by pqwoerituytrueiwoq on 2011-03-15
i would also like to know this

to rephrase what he said we want a option in grub that would boot our systems like the server version boots normally 

like a dual boot with ubuntu desktop and ubuntu server but with only one install

---

### Post by antaios256 on 2011-03-15
> **acklavidian said:**
> Sorry if a am in the wrong category here. I am a computer science student, and so sometimes I would like really quick access to a command line. 

First off I was wondering if there was a way I could make a option in grub that will boot Ubuntu without any x11 stuff. Kinda like the System rescue option, but without the menu, and not start as root. 

Second... I would say that I want a session that lets me start without x11, but for my purposes that is easy enough to do with ctrl+alt+number from the GDM. Instead, I would like a fast loading window manager that is good for programming. Really any interesting desktop environment (or window manager)suggestion that I am unfamiliar with would be investigated.(I am highly interested in wm/de, and have explored many.)


what your looking for here is to boot into run level 3, you could always issue a reboot comand into init3, however it seems your looking for a quick access to check files mode... no graphics, and not wanting to wait . how to add a run level 3 to the grub boot menu i wouldnt know. if someone could clarify that would be great.  (i wouldnt mind having it myself)

---

### Post by acklavidian on 2011-03-15
yes > [QUOTE]Sorry if a am in the wrong category here. I am a computer science student, and so sometimes I would like really quick access to a command line.
Ctrl + alt + T[/QUOTE]
Thank you WlaadDyaab. This kind of demonstrates my point. Why should I let my computer load up all this Gnome and X11 stuff(Ex: Keyboard shortcuts daemon)when I will just start up a terminal, and use vi and G++ and nothing else.

pqwoerituytrueiwoq is on the money with the type of solution I am looking for.

---

### Post by sisco311 on 2011-03-15
> **pqwoerituytrueiwoq said:**
> i would also like to know this

to rephrase what he said we want a option in grub that would boot our systems like the server version boots normally 

like a dual boot with ubuntu desktop and ubuntu server but with only one install

See: [post]9644518[/post]

---

### Post by grahammechanical on 2011-03-15
Do you guys or gals know what you are asking for? Think of all those people who are not studying computer science and who will boot into command line Linux by mistake and then claim that Ubuntu has broken their monitor because all they see is a black screen.

I might make that mistake myself and then panic. Modify your own boot loader if you want to but it is a no thank you from me.

Regards.

---

### Post by sisco311 on 2011-03-15
> **acklavidian said:**
> 
Second... I would say that I want a session that lets me start without x11, but for my purposes that is easy enough to do with ctrl+alt+number from the GDM. Instead, I would like a fast loading window manager that is good for programming. Really any interesting desktop environment (or window manager)suggestion that I am unfamiliar with would be investigated.(I am highly interested in wm/de, and have explored many.)

There are a a lot of lighter display/login managers (what's the plural of [getty]("http://en.wikipedia.org/wiki/Getty_(Unix)")?) than GDM.

[qingy](http://qingy.sourceforge.net/) is my favorite one.

As for wm/de, a lot of users (including programmers) like/prefer tiling window managers. 

The Arch Wiki is usually good: 
[https://wiki.archlinux.org/index.php/Window_Manager](https://wiki.archlinux.org/index.php/Window_Manager)
[https://wiki.archlinux.org/index.php/Comparison_of_Tiling_Window_Managers](https://wiki.archlinux.org/index.php/Comparison_of_Tiling_Window_Managers)

> **grahammechanical said:**
> Do you guys or gals know what you are asking for?

I hope so.

---

### Post by JKyleOKC on 2011-03-15
> **antaios256 said:**
> what your looking for here is to boot into run level 3, you could always issue a reboot comand into init3, however it seems your looking for a quick access to check files mode... no graphics, and not wanting to wait .Sorry, but the run-levels in Debian-based distros including Ubuntu are not at all like those for Red Hat based ones. In Ubuntu, there's no difference between 2, 3, 4, and 5., and the default run-level is 2.

You CAN edit the grub.cfg file, in the "menuentry" portions, to add the kernel option "text" where it says "quiet splash" in one or more of the portions. You can even duplicate one of these and add the text option, to be able to select from the menu. The reason for the "do not edit" warning is that your changes will be overwritten at the next kernel update (actually, the next run of update-grub).

The simplest way to get what you want is to extend the grub menu timeout from 3 to 10 seconds to give you time to react, and then when it appears, highlight the entry you want and press "e" rather than "Enter" which will give you an editor screen for the selected menu entry. Find the "quiet splash" words, and add "text" between them. Then press CTRL-X to boot with the edited entry.

If you wanted to never have the automatic GUI, you could edit /etc/default/grub to add the option, then run update-grub. Your system would now come up to the CLI every time, and typing "startx" after login would then launch the GUI when you wanted it.

Lots of options! Take your pick, or try them all...

---

### Post by acklavidian on 2011-03-16
> **sisco311 said:**
> See: [post]9644518[/post]

I tried this, and it works... However, the boot time is just as long as it takes to get to the gdm normally which kinda defeats the purpose. There has to be a way to streamline this. Anyhow I am starting to think that it would be best to choose a really fast distro, and boot from usb. Not to nullify my previous requests, but suggestions on a distro that would be ideal for this would be appreciated. The first thing that comes to mind is [SolarOS]("http://www.oby.ro/os/")(recently made popular by TRON). I haven't looked into it much, but its suppose to be fast.

---

### Post by Krytarik on 2011-03-16
I like *sisco311's* approach to have a permanent, additional boot menu option, besides 'normal' and "recovery mode".

How about this one as an alternative to speed up the boot process?:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
Talking about "Install a command-line system" and adding a slim DE of your choice.

---

