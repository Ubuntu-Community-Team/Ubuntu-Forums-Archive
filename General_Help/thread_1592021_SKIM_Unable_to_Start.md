---
title: "SKIM Unable to Start"
date: 2010-10-10
forum: General Help
---

### Post by gnulab on 2010-10-10
Solved by using another method - UIM as outlined by Zoreal.

---------------------------------------------------------------------------------------
Hi Guys,

I am having trouble starting SKIM in KUbuntu 10.10 and thus unable to type Chiense characters.

I have followed the instructions listed here [https://help.ubuntu.com/community/SCIM/Kubuntu](https://help.ubuntu.com/community/SCIM/Kubuntu)

But when I try to start SKIM through K Menu -> Utilities -> SKIM, it fails. I have no idea how to proceed from here.

I've also read this thread [http://ubuntuforums.org/showthread.php?t=452018](http://ubuntuforums.org/showthread.php?t=452018) and I'm stuck again at the part **'start SKIM'**.

I can start SCIM (K Menu -> Settings -> SCIM), but it doesn't seem to have any effect when I invoke the trigger.
And so does the iBus Keyboard Input Methods application (K Menu -> Settings -> Key Board Input Methods) that I am able to start but have no effect too.
Under Settings, there is also another application called Input Method Switcher (K Menu -> Settings -> Input Method Switcher) which fail to start too.

So what can I do to be able to type in Chinese under KUbuntu? I remember setting it up in Ubuntu 9.04 is really easy.

Please help. Thanks.

Henry

---

### Post by Zorael on 2010-10-10
I would advise against use of SCIM unless you really want/have to. It's old and development of it has sort of died off. I would likewise advise against using Skim, because it's written in Qt3. Loading it would load libraries into memory that you probably don't share with any other programs (unless you're still using Qt3 stuff, that is.) I'd suggest you go with either IBus or UIM, which can both be considered as active projects. I use UIM myself but either should work.

Notably IBus doesn't have a native Qt4 toolbar, so you would either have to install the IM Switcher widget (**plasma-widget-kimpanel** and **plasma-widget-kimpanel-backend-ibus**), or use the standard GTK toolbar. Since the latter would be launched before your user session is properly started, it isn't affected by the qtcurve theming, so it will look grey and ugly. UIM does have a native Qt4 toolbar though, as well as a GTK toolbar and a GTK systray icon thingie. Toolbars can largely be killed, restarted and switched freely in a running session. IBus makes this a bit harder though, as you have to restart the entire daemon to get a new toolbar to pop up.

The package recommendations below assume you want to input in Pinyin. I only input in Japanese myself and know little of the different kinds of written Chinese, but hopefully this should work.

Note that you need the [**universe** repositories enabled](https://help.ubuntu.com/community/Repositories/Kubuntu) to be able to download the uim packages.

[list=1][*][SIZE="3"]**Install packages**[/SIZE]
For **UIM**;
(Add **uim-qt3** if you still use Qt3 programs.)
```
$ sudo aptitude install uim uim-qt uim-pinyin
```
For **IBus**;
(As mentioned earlier, add **plasma-widget-kimpanel** and **plasma-widget-kimpanel-backend-ibus** if you want to use the plasma IM Switcher widget instead of the normal GTK toolbar/systray icon.)
```
$ sudo aptitude install ibus ibus-gtk ibus-qt4 ibus-pinyin
```
[*][SIZE="3"]**Set default input method**[/SIZE]
For **UIM**;
```
$ im-switch -s uim-toolbar-qt
```
For **IBus**;
```
$ im-switch -s ibus
```
For **IBus with the plasma IM Switcher applet as default toolbar**;
```
$ im-switch -s ibus-kde
```
[*][SIZE="3"]**Extra fixes**[/SIZE]
For **UIM**;
```
$ sudo sed -ie 's/toolbar-qt)/toolbar-qt4)/g' /etc/X11/xinit/xinput.d/uim-toolbar-qt
```
[*][SIZE="3"]**Logout and back in (or reboot)**[/SIZE]
You should get a UIM/IBus toolbar or tray icon after having logged back in.[/list]

------------

If it **doesn't** work, paste the output of the following (inbetween [code****] code-tags [/code****] please).
```
clear; echo -e "8< 8< 8< -- Cut from here -- >8 >8 >8\n\nGTK:\t$GTK_IM_MODULE\nQt:\t$QT_IM_MODULE\nXMOD:\t$XMODIFIERS\n"; im-switch -l; echo; ps ux | grep uim | grep -v grep; ps ux | grep ibus | grep -v grep; echo; dpkg -l ibus\* | grep ^ii; dpkg -l uim\* | grep ^ii; echo -e "\n8< 8< 8< -- ...to here -- >8 >8 >8\n"
```
All in one line for easy copy-pasting. And not to worry; those commands are safe.

---

### Post by gnulab on 2010-10-11
Hi Zoreal,

Thank you for your solution and clarification about the slow development of SCIM & SKIM.

I'm trying out the UIM method. Will experiment with iBus when I have the time.

Just for information to those who are trying out UIM under Kubuntu, the command below is definitely necessary.

>  ```

sudo sed -ie 's/toolbar-qt)/toolbar-qt4)/g' /etc/X11/xinit/xinput.d/uim-toolbar-qt

```

I do have few more questions how to switch IM, but that will be another new thread, but thanks once again.

I guess Ubuntu documentation team is lacking behind in the progression of the technology.

Thanks once again.
Henry

---

