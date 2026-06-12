---
title: "Window focus mode setting pops window to top [repost]"
date: 2012-02-22
forum: General Help
---

### Post by 4museman on 2012-02-22
I have the same problem with **window focus mode** as it is very well described by ***[UnSandpiper]("http://ubuntuforums.org/member.php?u=757934")*** in this unanswered but closed thread:
[http://ubuntuforums.org/showthread.php?t=1858321](http://ubuntuforums.org/showthread.php?t=1858321)

Here is the copy of text:
[COLOR=DarkRed][I]In Gnome 2 I've always been using the window focus to follow the mouse  and after upgrading to Oneiric and switching to Unity I had to enable it  again using the gnome-tweak-tool.

Now the window focus does follow the mouse, but with one annoying new  feature, namely popping the active window to the top above other windows  after a slight delay. [/I] [I]
This is very annoying when working with a fullscreen terminal, then  opening an email to copy paste some stuff, but everytime I switch to the  terminal, the email will go to the background.

Is there a setting to disable that?[/I] [I]

And also what is the difference between the "Sloppy" and "Mouse" setting? Both settings seem to behave the same way.[/I][/COLOR]


I have the same problems since I upgraded to 11.10.
It is very annoying behaviour and I didn't figure out how to keep the mouse focus, but turn off the moving focused window to top.

Does anyone knows some solution? Please...

---

### Post by 4museman on 2012-05-02
Hi all!

In new release the same problem. :sad:

Please, is there a way to set up the focus without that annoying picking up the windows to top? I can't believe that nobody uses this behaviour.

---

### Post by 4museman on 2012-05-02
So I start to dig in "Configuration Editor" and I've found the option for healing of my problem!
[B]
/apps/metacity/general[/B] --> key: "**auto_raise**" = **[COLOR=DarkRed]OFF[/COLOR]**

I  wonder I didn't find that in previous version, because I remember I  tried. Now I'm pretty satisfied with the window focus behaviour.

The  only sad is, that this useful feature (as many others) is still so  hidden! It didn't make it even to "Advanced Settings", which are  shamefully unadvanced compare to good old versions of Ubuntu. :???:

---

