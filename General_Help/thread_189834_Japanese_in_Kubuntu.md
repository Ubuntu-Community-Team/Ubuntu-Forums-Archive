---
title: "Japanese in Kubuntu"
date: 2006-06-05
forum: General Help
---

### Post by Castar on 2006-06-05
Hi,

I am trying to setup support for japanese input on a pc with a british keybord (en-GB). I have installed the support for japanese, but I cannot write japanese at all. The engines installed is scim and anthy, but when I input Ctrl+Space or Shift+Space nothing happens. Do I need to install additionally something else like scim-uim? 

thanks

---

### Post by Evoreth on 2006-06-05
[list]
[*]sudo apt-get install im-switch scim-anthy libapt-pkg-perl
[*]im-switch -s scim
[*]sudo cp /etc/X11/xinit/xinput.d/ja_JP ~/.xinput.d/en_GB (your language code)
[*]restart your system
[*]press ctrl + space to activate scim
[/list]

Sorry, but I can't guarantee that it works.
&#12364;&#12435;&#12400;&#12387;&#12390;&#12397;&#12540;&#12540;

---

### Post by Castar on 2006-06-06
Unfortunately, this didn't work for me. 

I didn't have libapt-pkg-perl. After it was installed, I put the ja_JP file in ~/.xinput.d/ but not only I could not input japanese, but most programs I tried to run kept freezing. 

And scim-uim doesn't help too :-k

---

### Post by tsb on 2006-06-06
I honestly don't know why they can't get multiple language environments working like they do in Windows.  Dapper was supposed to fix this issue, but it's become worse.  It was relatively easy to get Chinese input in Breezy, but I gave up with Dapper.  Why not just let us add them and have them instantly work like they do in Windows?

---

### Post by Evoreth on 2006-06-06
If scim doesn't work, check out UIM:
[list]
[*]sudo apt-get install im-switch uim uim-anthy
[*]im-switch -s uim_anthy
[*]hit alt + F2 and type "uim-pref-gtk" to configure it
[*]add either "uim-toolbar-gtk" or "uim-toolbar-gtk-systray" or none of them (if you don't want any visual feedback in which mode you are currently) to your startup programs in "gnome-session-properties"
[*]restart your system
[/list]

I hope that it works this time. :)

---

### Post by vialick on 2006-06-06
[QUOTE=tsb]I honestly don't know why they can't get multiple language environments working like they do in Windows.  Dapper was supposed to fix this issue, but it's become worse.  It was relatively easy to get Chinese input in Breezy, but I gave up with Dapper.  Why not just let us add them and have them instantly work like they do in Windows?[/QUOTE]

I found windows to be increadibly hard to get different language environments up and working without having to use 3rd party software. Infact so far the only easy OS I've found for it is OS X

---

### Post by Castar on 2006-06-06
But if I'm correct, OSX only supports a handful of languages, right?

---

### Post by Castar on 2006-06-19
So is anyone using successfully the scim/skim combination for Japanese? UIM works for me so just wondering... :rolleyes:

---

### Post by Najand on 2006-06-19
[QUOTE=Castar]So is anyone using successfully the scim/skim combination for Japanese? UIM works for me so just wondering... :rolleyes:[/QUOTE]

SCIM/SKIM works for me. However, the problem with SCIM is that many commercial softwares like Acroread or Realplay still conflict with SCIM and there is no practical solution has been found for it. Unfortunately the bugs in Novel Bugzilla and RedHat Bugzilla RESOLVED CLOSED, but it is still a serious problem, clearly. For using such softwares you still have to export your gtkimmodule to "xim" and it is not practical all the time. I personally prefer UIM with Canna.

---

### Post by Castar on 2006-06-19
Is it only me who thinks these UIM - Scim / Canna - Anthy etc combinations are very confusing? :confused: I never really understood what each does in their cooperation!

I mean, can't just a simple system be proposed that works in both KDE/Gnome? It makes no sense...#-o

---

### Post by Najand on 2006-06-20
[QUOTE=Castar]Is it only me who thinks these UIM - Scim / Canna - Anthy etc combinations are very confusing? :confused: I never really understood what each does in their cooperation!

I mean, can't just a simple system be proposed that works in both KDE/Gnome? It makes no sense...#-o[/QUOTE]

Hmm, They are just different IMs. Actually you can find different Input  Methods in MS-Windows too... Hmm, Like... MS-IME... ATOK... et cetra...  However, as far as most of them are commercial and people have to pay for them,  you  don't  hear  about  them most of the time... Anyway, if you wanna know the most popular Japanese IM  in Japan, I think it is kinput2+canna. But still, I personally think that, UIM is much more user friendly and easier to use than kinput2.

Have you seen the help page in UBUNTU homepage for instruction on how to install UIM+ANTHY? you  can find it [here]("https://help.ubuntu.com/community/JapaneseInputHowToInBreezy"). It is for Breezy, but it works fine with Dapper Drake too.

---

### Post by Castar on 2006-06-21
Najad, thank you for the information. Actually now I am already running uim+anthy for japanese and it indeed runs great. I was just hoping to have a KDE-oriented IM like skim on my desktop. 

Of course, at the end of the day the only point is to be able to write Japanese, right? ;) So why bother more :D

---

### Post by xOrphenochx on 2006-06-29
It's quite easy to do. Install scim, anthy and make a file like this:

```
@ubuntu:~$ cat .xprofile
#!/bin/sh
export XMODIFIERS=@im=SCIM
export QT_IM_MODULE=scim
export GTK_IM_MODULE=scim
export LC_CTYPE=ja_JP.UTF-8

```

After that, make sure its executable and restart your session.

---

### Post by Castar on 2006-06-30
This works xOrphenochx! Thanks! :D 

The only problem is, that I have to somehow set the input method to scim, since now XIM is the default. Any way of doing it automatically?

---

### Post by Hiroshima on 2006-07-31
> **Evoreth said:**
> If scim doesn't work, check out UIM:
[list]
[*]sudo apt-get install im-switch uim uim-anthy
[*]im-switch -s uim_anthy
[*]hit alt + F2 and type "uim-pref-gtk" to configure it
[*]add either "uim-toolbar-gtk" or "uim-toolbar-gtk-systray" or none of them (if you don't want any visual feedback in which mode you are currently) to your startup programs in "gnome-session-properties"
[*]restart your system
[/list]

I hope that it works this time. :)

Umm, it worked pretty well, except I cannot seem to do the last step
[COLOR="Red"][*]add either "uim-toolbar-gtk" or "uim-toolbar-gtk-systray" or none of them (if you don't want any visual feedback in which mode you are currently) to your startup programs in "gnome-session-properties"[/COLOR]
Probably due to the fact that I'm using KDE not Gnome.  How would I do that last step in KDE?

Cheers,

Hiroshima

EDIT*
Why is it that after you post something, it ends up working?  No need to answer the above question, it worked like you said it would.

uim-toolbar-gtk-systray  in a run command works like a charm.  How do I&#12288;get it to run at startup?

Hiroshima

---

